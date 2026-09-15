# NetPet 创意工坊

NetPet Studio 客户端从这里下载角色皮肤。客户端默认只内置“NetPet 经典像素小脸”，
其他皮肤（木偶猫、神里绫华，以及 Codex 宠物）都在本仓库通过创意工坊下载。

## 目录结构

```
workshop/workshop.json     目录索引（客户端拉取的入口）
workshop/packs/*           皮肤包（.netpetskin / .netpetv2）
workshop/previews/*        列表缩略图
```

客户端默认基址：

```
https://raw.githubusercontent.com/taixiansen2/netpet-workshop/main/workshop/
```

该地址可在客户端设置或环境变量 `NETPET_WORKSHOP_URL` 中覆盖。

## workshop.json

```json
{
  "schema": 1,
  "updated": "2026-09-15",
  "skins": [
    {
      "id": "puppet_cat",
      "name": "木偶猫",
      "author": "NetPet 同人设计",
      "format": 1,
      "version": "1.0.0",
      "size": 7170,
      "sha256": "…",
      "preview": "previews/puppet_cat.png",
      "download": "packs/puppet_cat.netpetskin",
      "tags": ["角色", "v1"],
      "license": "unofficial-fanart",
      "description": "…"
    }
  ]
}
```

- `format`：`1` 为 `.netpetskin`（八表情），`2` 为 `.netpetv2`（多动作）。
- `preview` 与 `download` 可以是相对 `workshop/` 的路径，也可以是完整 URL。
- 客户端会校验文件大小与 `sha256`，并用皮肤包解析器确认有效后才安装。

## 维护

在 NetPet 主仓库运行：

```powershell
.\.venv-gui\Scripts\python.exe .\tools\build_workshop_index.py `
  --packs host_gui\assets dist\codex-pets-v2 `
  --out ..\netpet-workshop\workshop
```

然后提交并推送本仓库。

## 素材与授权

- 木偶猫、神里绫华为 NetPet 原创同人设计，公开销售或分发前请自行确认授权。
- Codex 宠物（Codey、BSOD、Dewey、Fireball、Hoots、Null Signal、Rocky、Seedy、
  Stacky）为 OpenAI Codex 客户端内置素材的只读提取结果，仅供个人演示与非商业用途；
  版权归 OpenAI 所有，请勿用于销售或商业分发。
