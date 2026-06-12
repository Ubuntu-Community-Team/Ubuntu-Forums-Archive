---
title: "Setting a default OS"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by happysmileman on 2006-10-04
I just downloaded Ubuntu recently but as I am the only person using this computer who will use it(for now :) ), I would like to set it up so that the computer will load windows automatically unless i enter using F8, I only have one HDD so it isn't just a matter of setting the bootable hard drives in order, can you use the setup (by pressing th "delete" key on startup) to change the default partition and if you do will there be a noticable difference when using the computer with Windows

---

### Post by aysiu on 2006-10-04
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by Kateikyoushi on 2006-10-04
You can change the grub menu to make it boot windows by default, if you rather boot another OS you can select it from the grub menu.

[Read this how to do change the default OS.]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by happysmileman on 2006-10-04
Thanks, seems helpful, would setting the "timeout" value to 0 make it load straight away or does it have to be a minimum of 1

---

### Post by Kateikyoushi on 2006-10-04
You can hit space or enter to boot instantly.
If you set it to 0 you won't have time to select Ubuntu.
I leave it at 3.

---

### Post by happysmileman on 2006-10-04
> **Kateikyoushi said:**
> You can hit space or enter to boot instantly.
If you set it to 0 you won't have time to select Ubuntu.
I leave it at 3.

Would F8 still work like this, because it wouldn't bother me and everyone else is a technophobe who would blame me for destroying the PC if it acted any different at all.

---

### Post by Kateikyoushi on 2006-10-04
You can try that anytime and if works for you then set grub accordingly.

---

### Post by happysmileman on 2006-10-04
K, got it

---

