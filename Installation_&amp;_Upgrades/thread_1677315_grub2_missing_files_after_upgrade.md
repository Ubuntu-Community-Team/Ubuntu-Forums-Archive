---
title: "grub2 missing files after upgrade"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by type11error on 2011-01-28
Last night I attempted to upgrade my Ubuntu 10.10 (amd64) machine. After reboot (it installed a new kernel), the grub menu only had the memtest. Booted into a livecd and it seems that I was missing most of the files in /etc/grub.d/. Reinstalled grub-common and grub-pc didn't seem to restore the files. I ended up having to download the dpkg, expand it and copy the files manually so I could get the box generate grub.conf and boot up. I think grub may have been broken before the upgrade but exhibited the problem when it upgraded the kernel and reran upgrade-grub but I can't seem to figure out why reinstalling grub doesn't add the files back. Anyone had this issue or have any ideas how to fix it? Thanks.

---

### Post by sikander3786 on 2011-01-28
Welcome to the forums :-)

So from the booted Live CD, please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help diagnose any problems related to Grub.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by type11error on 2011-01-28
Thanks :P

So I don't need to boot from the livecd any longer. I was able to copy the files grub was missing out of /etc/grub.d/, generate the grub.conf and boot up the OS. My problem is that I had to manually copy the files out of the grub-common package to fix it and I'd like to figure out why. Attempting to reinstall chrooted on the live cd and once I booted didn't add the files (I tried moving grub.d aside after uninstalling). As far as I can tell listing the files out of dpkg they should be there but there not. So I can boot but reinstalling grub-common and grub-pc doesn't add the missing files :(

---

