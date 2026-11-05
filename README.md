# rogue-launcher-feed

더로그 런처가 읽는 피드. 런처는 `raw.githubusercontent.com/nocksa/rogue-launcher-feed/main/` 에서 받는다.

| 파일 | 내용 | 누가 쓰나 |
|---|---|---|
| `manifest.json` | 묶음 버전, Fabric, 서버, 모드 목록(`mods`), `mods/` 밖 파일(`files`) — sha1·주소 | `RogueLauncher/tools/publish.py pack` |
| `fabric/<versionId>.json` | Fabric 버전 프로필 | 같은 도구 |
| `launcher.json` | 최신 런처 버전·주소·sha256 | `publish.py launcher` |
| `news.md` | 공지·패치노트 (최신이 위) | 사람이 직접 |

## 피드 약속 (통합 런처가 이 값으로 움직인다)
- `mods`·`files` 내용이 바뀌면 `version` 을 올린다. `models.rmb` 만 바뀌어도 올린다 (`publish.py` 가 그대로 두면 막는다).
- 필드 이름·뜻이 바뀌면 `formatVersion` 을 올린다. 추가만이면 그대로 둔다.
- 피드 주소를 바꾸면 런처 업데이트가 필요하니 미리 알린다. 받는 주소는 `https://` 만, 모드 파일 이름은 `^[A-Za-z0-9._+-]+\.jar$` 모양만 쓴다.

## 공지 쓰는 법
`news.md` 맨 위에 글을 하나 더 쌓는다. 머리줄 형식을 지킨다.

```
## [공지] 2026-10-31 · 서버 점검 안내
본문. **굵게**, - 목록, ### 소제목, [링크](https://...) 를 쓸 수 있다.
```

종류는 `[공지]` 또는 `[패치노트]`. GitHub 웹에서 고치고 커밋하면 몇 분 안에 런처에 뜬다.

## 우리 모드 jar · 런처 exe
GitHub Release 첨부 파일로 올린다: `pack-<버전>` (Modrinth 에 없는 우리 모드), `launcher-<버전>` (RogueLauncher.exe).
