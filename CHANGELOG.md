# Changelog — rmx-sx-gateway (Raspi-Daemon)

Alle nennenswerten Änderungen am Gateway-Daemon (WebSocket-Server für den
ESP32-WLAN-Handregler) werden hier dokumentiert.

Format angelehnt an [Keep a Changelog](https://keepachangelog.com/),
Versionierung semver (MAJOR.MINOR.PATCH).

Regel (Vorgabe im Projekt): Bei jedem funktionalen Code-Change wird
`__version__` in `src/rmx_sx_gateway/__init__.py` gebumppt UND dieser
CHANGELOG-Block sowie ein Git-Tag `v<version>` (auf GitHub) angelegt.
Die Version ist im `hello_ack.server_version` des WebSocket-Handshakes
sichtbar und via `python -m rmx_sx_gateway.main --version` abrufbar.

---

## [0.1.1] - 2026-07-13
### Behoben / Verbessert (Versionierung)
- `protocol.py`: `SERVER_VERSION` ist jetzt an `__version__` gekoppelt (Single
  Source of Truth) — kein hartcodiertes Duplikat mehr. `hello_ack.server_version`
  im WebSocket-Handshake spiegelt ab sofort die echte Gateway-Version.
- `systemd/rmx-sx-gateway.service`: `ExecStart`/`WorkingDirectory` korrigiert
  von `/opt/rmx-sx-wlan-gateway` auf den echten Pfad `/opt/rmx-sx-gateway`
  (Pi lief bereits korrekt, Repo-Datei war veraltet).
- CHANGELOG angelegt (analog ESP32-Firmware).
### Technik / Verifikation
- `python -c "import rmx_sx_gateway; print(rmx_sx_gateway.__version__)"` = 0.1.1.
- Bump 0.1.0 -> 0.1.1 (Code-Change ggü. 0.1.0).

## [0.1.0] - 2026-07-13
### Initial / Setup
- Gateway-Code vom Raspi (192.168.0.87:/opt/rmx-sx-gateway) geholt und als
  eigenes Git-Repo unter https://github.com/saaralf/rmx-sx-gateway initial
  committet.
- Versionierung etabliert: `SERVER_VERSION` in `protocol.py` ist jetzt an
  `__version__` (Single Source of Truth) gekoppelt — kein hartcodiertes
  Duplikat mehr.
- `hello_ack.server_version` (WebSocket-Handshake) spiegelt ab sofort die
  echte Gateway-Version an den ESP32-Client (bisher hartcodiert "0.1.0").
- CHANGELOG angelegt (analog ESP32-Firmware).
