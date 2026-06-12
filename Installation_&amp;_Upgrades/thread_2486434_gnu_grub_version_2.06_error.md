---
title: "gnu grub version 2.06 error"
date: 2023-04-30
forum: Installation &amp; Upgrades
---

### Post by VMC on 2023-04-30
This started out as partition failed fsck. Fount that e2fsck needs to be upgraded to 1.47.0. My ubuntu LTS has the old version 1.46, which fails any fsck check of all Lunar (mate, ubuntu, kde, etc).
I installed ubuntu-lunar.
Now everything works except trying to boot other distros.

```
grub> ls (hd2,5)/ 
error: unknown filesystem
```[hd2,5 is manjaro partition]

Oddly enough, booting ubuntu, I can mount Manjaro and view the filesystem. I just can't boot it?!

My question then, Is there a way to upgrade Ubuntu **gnu grub to version 2.06.r456**?

---

### Post by oldfred on 2023-04-30
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by VMC on 2023-05-01
The problem is grub 2.06 not bootinfo. I'll come back with some info , link, along with bootinfo. 2.06 is a know issue.
[https://forum.manjaro.org/t/im-not-getting-the-option-to-boot-into-manjaro-from-the-ubuntu-grub/97978/7](https://forum.manjaro.org/t/im-not-getting-the-option-to-boot-into-manjaro-from-the-ubuntu-grub/97978/7)
Read up on the four links inside the link above.

---

### Post by VMC on 2023-05-01
Boot-Repair never finished, failed. [yannubuntu]("https://sourceforge.net/u/yannubuntu/profile/") needs to investigate the issue. This i a grub issue, and not boot issue. Ubuntu and Manjaro both boot.

---

### Post by Dennis N on 2023-05-01
> Now everything works except trying to boot other distros.
Are you trying to boot other distros (like Manjaro) from the Ubuntu grub menu?

---

### Post by VMC on 2023-05-01
Several issues afoot: ubuntu-jammy doesn't have e2fsck 1.47, with grub 2.06.r.456 installed at manjaro, ubuntu grub 2.06 doesn't recognize the partition.
To work around it, but not solve it, is to format the partition using ubuntu then install manjaro without formatting, then turn around and make ubuntu the active grub.
I'm just going to make this as solved, as is.

---

