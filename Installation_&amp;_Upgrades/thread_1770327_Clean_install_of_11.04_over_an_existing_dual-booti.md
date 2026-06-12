---
title: "Clean install of 11.04 over an existing dual-booting vista+jaunty"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by moebius444 on 2011-05-29
I'm planning to upgrade from jaunty to natty, while retaining vista. I have legacy GRUB as my bootloader.

sda1 : jaunty
sda2 : jaunty swap
sda3 : vista
sda4 : general ntfs

if i remember correctly, grub is installed to sda.

If i were to just format the jaunty partition, install natty in there, and install the new bootloader to sda, is there a chance that i would mess up the dual boot configuration? i am concerned of the transition from legacy grub to grub2.

---

### Post by mikewhatever on 2011-05-29
By reinstalling, you'll be overwriting all dual boot configurations, GRUB, and everything else on that partition with new stuff. Since the old configs are going away, it's pretty pointless to worry about messing them up. I think you'll be all set and good to go if the reinstall goes well.

PS: I'd like to mention the reinstall once again. Do not upgrade, because upgrading from Jaunty to Natty is unsupported. Good luck.

---

### Post by moebius444 on 2011-05-30
alright. thanks. i'm giving it a go.

anyway, jaunty works like a charm, and still does.

---

### Post by moebius444 on 2011-05-30
it worked without incident. thanks for the assurance. ;)

---

