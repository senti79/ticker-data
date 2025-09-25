# ticker-data

GitHub Pages로 배포되는 전광판(messages) 데이터 저장소입니다. 언어별 메시지 파일을 직접 업로드(커밋/PR)하여 앱이 읽어갑니다.

## 구조

- `docs/messages.ko.json` — 한국어 메시지
- `docs/messages.en.json` — 영어 메시지
- `docs/messages.ja.json` — 일본어 메시지
- `docs/messages.es.json` — 스페인어 메시지
- `docs/messages.zh.json` — 중국어(간체) 메시지
- `docs/messages.de.json` — 독일어 메시지
- `docs/messages.fr.json` — 프랑스어 메시지
- `docs/messages.json` — (선택) 단일 파일 호환 또는 기본값
- `schema/messages.schema.json` — 간단한 스키마
- `.github/workflows/validate.yml` — PR/푸시 시 스키마 검증

## Pages 설정

- Settings → Pages → Deploy from a branch
- Branch: `main` / Folder: `/docs`
- 배포 URL 예시: `https://senti79.github.io/ticker-data/`
- JSON URL 예시: `https://senti79.github.io/ticker-data/messages.ko.json`

## 앱 연동(이미 설정됨)

- 앱은 `window.__TICKER_SOURCE__ = { mode: 'pages', baseUrl: 'https://senti79.github.io/ticker-data' }` 설정 시,
  - 우선 `messages-<locale>.json`(예: `messages-ko.json`)을 조회하고,
  - 없으면 `messages.json`으로 폴백합니다.

## 운영 방법

1. 해당 언어 파일(`docs/messages.<lang>.json`) 편집/업로드
2. PR 생성 → CI(스키마 검증) 통과 → 리뷰/머지
3. 1~2분 내 Pages 반영 → 앱 자동 반영(폴링)

캐시 무효화는 앱에서 기본 제공됩니다(쿼리 파라미터).

