---
title: "DualBoot Win8/ubuntu 13.04"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by ayman2 on 2013-09-25
Hello,
I have a new vaio with Windows 8 preinstalled, and I've installed ubuntu 13.04 with it (first I had problem booting but after a boot-repair, and desabling sucure boot on the bios. Everything worked well)
But the problem now, is I can't update Windows. In the process of the update after rebooting (and chosing Windows on grub) Windows runs normaly (the update doesn't continue) and it asks me to do the update again.
Anyone have a solution to this problem? 
Thanks.

---

### Post by oldfred on 2013-09-25
Rather than boot Windows from grub, can you not boot it directly from UEFI.
Or did you run the rename function that creates the bkpbootmgfw.efi and the Windows original file was bootmgrfw.efi.

---

### Post by ayman2 on 2013-09-26
I didn't know that I should run the [COLOR=#000000]bkpbootmgfw.efi, thanks it's working now =)[/COLOR]

---

### Post by eGyEm7R on 2013-09-26
Ignore this post

---

