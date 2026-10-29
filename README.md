# 周大福 · 店务 KPI

给妈妈（周大福厦门吕厝天虹店店长）做的店员 KPI 每日跟进小工具。

- 手机网页（PWA），微信/浏览器打开链接即可用
- 可添加到手机桌面，断网也能打开
- 数据存在手机本地，不上传；支持导出备份/Excel
- 9 项指标、合格线、分值、周期都可在设置里改

## 目录

```
ctf-kpi/
├─ index.html           应用本体（全部逻辑和样式都在这里）
├─ manifest.webmanifest PWA 配置
├─ sw.js                离线缓存
├─ version.json         版本号（更新时改这里）
├─ icons/               桌面图标
└─ README.md
```

## 本地预览

```powershell
cd C:\Windows\system32\ccbots\ctf-kpi
python -m http.server 8765
```

浏览器打开 http://localhost:8765

> 直接双击 index.html 也能用，但 PWA/离线缓存需要 http(s)。

## 部署到 GitHub Pages

1. 在 GitHub 建仓库（例如 `ctf-kpi`）
2. 把本目录全部文件推上去
3. 仓库 Settings → Pages → Source 选 `main` 分支根目录
4. 得到链接：`https://xman0592.github.io/ctf-kpi/`
5. 把链接发给妈妈，按「设置 → 安装到桌面」的步骤添加

国内访问 GitHub Pages 偶尔慢，备选：Cloudflare Pages、腾讯云 COS 静态网站、阿里云 OSS。

## 更新版本

1. 改 `index.html`
2. 改 `version.json` 里的 `version`
3. 改 `sw.js` 里的 `CACHE = 'ctf-kpi-vX.Y.Z'`
4. 上传覆盖

手机端打开时若提示有新版本，刷新即可；本地数据不受影响。

## 数据说明

- 数据保存在浏览器 localStorage，键名 `ctf_kpi_state_v1`
- 自动快照存在 `ctf_kpi_snaps_v1`，保留最近 5 份
- 换手机、清理浏览器缓存前，务必在「设置 → 数据安全 → 导出备份」
- 导入备份会覆盖当前数据

## 指标默认值

| 指标 | 合格线 | 分值 | 周期 |
|---|---|---|---|
| 万相占比 | ≥13% | 监测 | 每日 |
| 传颂占比 | ≥10% | 监测 | 每日 |
| 周二换金破冰 | 完成 | 10 | 每周 |
| 总销售完成率 | ≥100% | 10 | 每月 |
| 钻石占比 | ≥8% | 10 | 每日 |
| 参评率 | ≥80% | 监测 | 每日 |
| CTF FOUR YOU 破冰 | 完成 | 10 | 每月 |
| R+ RU 占比 | ≥30% | 10 | 每日 |
| 高珠启航 | 完成 | 10 | 每月 |

满分 60 分。分值、合格线、周期均可在应用内调整。
