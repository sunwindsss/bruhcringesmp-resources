# BruhCringeSMP Resource Pack

Main custom resource pack for the bruhcringeSMP Minecraft server.

This repository is public so the server can serve the resource pack directly to players when they join.

## Supported Version

- Server: Paper 26.1.2
- Minecraft Java: 26.1.2
- Resource pack format: `84.0`

## Features

- Adds a custom Selfie Stick item model and texture.
- Adds a custom Adamantium Boots item model and texture.
- Overrides vanilla item model definitions so custom model data can swap:
  - `minecraft:bone` -> `bruhcringesmp:item/selfiestick`
  - `minecraft:netherite_boots` -> `bruhcringesmp:item/adamantium_boots`
- Keeps vanilla fallback models when the custom model data does not match.

## Repository Layout

- `bruhcringesmp-resourcepack/` - editable source folder for the resource pack.
- `bruhcringesmp-resourcepack.zip` - packaged resource pack used by the server.
- `common issues.txt` - old troubleshooting notes.

## Implementing On The Server

1. Edit files inside `bruhcringesmp-resourcepack/`.
2. Recreate `bruhcringesmp-resourcepack.zip` from the contents of that folder.
3. Make sure the ZIP root contains `pack.mcmeta` and `assets/` directly.
4. Push the updated ZIP to this public GitHub repository.
5. Use the raw GitHub ZIP link in `server.properties`.
6. Download the final ZIP from the raw link and calculate its SHA-1 checksum.
7. Put that checksum in `resource-pack-sha1` in the server properties file.
8. Restart the server or make players reconnect so Minecraft downloads the new pack.

Recommended raw URL:

```text
https://raw.githubusercontent.com/sunwindsss/bruhcringesmp-resources/main/bruhcringesmp-resourcepack.zip
```

In `server.properties`, escape the colon:

```properties
resource-pack=https\://raw.githubusercontent.com/sunwindsss/bruhcringesmp-resources/main/bruhcringesmp-resourcepack.zip
resource-pack-sha1=<sha1 checksum here>
```

Players do not need to install the pack manually. The server sends it automatically when they join.

## Troubleshooting

### Clients do not download the resource pack

- Make sure the GitHub repository is public.
- Use the real raw GitHub file link, not a normal GitHub page link.
- If the repo is private, clients will usually receive a `404` and the pack will not download.

### Resource pack loads but nothing changes

- Check that `pack.mcmeta` and `assets/` are at the root of the ZIP.
- Do not zip the outer folder itself. The archive should not contain an extra `bruhcringesmp-resourcepack/` folder above `pack.mcmeta`.
- Check that the custom model data values used by the plugin match the values in the resource pack item definitions.

### Minecraft says the pack is incompatible

- Check `pack.mcmeta`.
- For Minecraft/Paper 26.1.2, the pack format should be `84.0`.
- If the server updates to a newer Minecraft version, check the current pack format on the Minecraft Wiki and update `pack.mcmeta` if needed.

### Clients keep using an old version

- Recalculate the SHA-1 checksum after every ZIP change.
- Update `resource-pack-sha1` in `server.properties`.
- Have players reconnect after the server has the new URL/checksum.

SHA-1 helper:

```text
https://emn178.github.io/online-tools/sha1_checksum.html
```

Pack format reference:

```text
https://minecraft.wiki/w/Pack_format#List_of_pack_formats
```

## Credits

- sunwindsss
- Mangalis
- prodigylock
