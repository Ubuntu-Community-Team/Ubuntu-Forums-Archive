---
title: "using variables inside user-data autoinstall"
date: 2022-09-22
forum: Installation &amp; Upgrades
---

### Post by nzm96 on 2022-09-22
Hi,

Is it possible to use variables (like: $RELEASE) inside the autoinstaller user-data?

I would like to download an ubuntu release-specific .deb (package-$RELEASE.deb) into my VM, and install it using:

[FONT=courier new]curtin --in-target --target=/target -- wget -O /tmp/package-$RELEASE.deb http://1.2.3.4/package-$RELEASE.deb
 curtin --in-target --target=/target -- sudo dkpg -i /tmp/package-$RELEASE.deb
[/FONT]
$RELEASE would then currently be either jammy or focal.

Or is there another way to achieve that result, while keeping the user-data generic for different ubuntu versions?

Thanks!

---

