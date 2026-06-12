---
title: "Fails to debootstrap Impish. No zstd extractor"
date: 2022-01-07
forum: Installation &amp; Upgrades
---

### Post by triplek2 on 2022-01-07
```
I: impish uses zstd compression, setting --extractor=ar option
E: Unknown compression type for data.tar.zst in .//var/cache/apt/archives/base-files_11.1ubuntu5_amd64.deb
```

Im using the latest debootstrap package from impish repositories. The man page doesnt mention extractors other than ar and dpkg-deb

---

