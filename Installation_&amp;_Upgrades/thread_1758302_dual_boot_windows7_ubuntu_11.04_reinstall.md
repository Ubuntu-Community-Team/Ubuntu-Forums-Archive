---
title: "dual boot windows7 ubuntu 11.04 reinstall?"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by Wetmewhistle on 2011-05-14
hi,

I have done some commands in ubuntu 11.04 and got problems, thinking of reinstall it. (laptop acer 5738zg)

Previously when i have dual booted win7 and ubuntu10 and linux mint i always get "grub rescue" when i try reinstall my linux partition, and it ends with i have to do clean reinstall of both windows and linux, which is a major pain in the rectum area

Is there a way to make my linux go back to original state without reinstall, and if i reinstall, how can I do this without loosing win7 partition and get this awful grub rescue message. I have searched the net, and I have not found any good guides on this subject, please link me if there is some good guide on this.

Any help is much appreciated!

Bernt

---

### Post by zvacet on 2011-05-15
If you want to reinstall then when you come to the partition stage choose manual way and select existing linux partition for your new install.Mark it as / root and format as ext4.Install grub on MBR and you should be able to boot both OS without problems.

---

