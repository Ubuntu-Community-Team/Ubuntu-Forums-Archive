---
title: "miss 5.9.0-0900 header package when install 5.9.0 generic kernel"
date: 2020-11-30
forum: Installation &amp; Upgrades
---

### Post by haojian-zhuang on 2020-11-30
I wanted to install 5.9 kernel on arm64 from "https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/".

[ATTACH=CONFIG]287480[/ATTACH]

It listed 3 deb packages above. When I install them, I failed to install headers package since it reported missing 5.9.0-0900 package. When I checked the part of amd64, I found there's a one package in amd64. But it's missing in arm64. So I think it's a bug.

---

