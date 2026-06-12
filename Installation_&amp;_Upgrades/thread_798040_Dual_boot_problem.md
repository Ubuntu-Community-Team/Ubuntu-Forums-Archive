---
title: "Dual boot problem"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by penguinhack62 on 2008-05-17
I just installed Ubuntu Server on a dual boot system. 1st HD has Windows Vista Ultimate and second HD I installed server. I installed Grub during installation to MBR like I've done is past installs. Only windows boots up, Ubuntu is not even an option. How and where can I check the MBR and fix problem. I know Vista treats other operating systems of their own family as foreign objects. Please help.

---

### Post by logos34 on 2008-05-17
maybe grub installed on the mbr of the ubuntu drive.  try changing the boot order in the Bios.  If it works edit menu.lst so you can [also boot vista]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

---

### Post by teaker1s on 2008-05-17
stop do not install grub onto master mbr it will stop vista sp1 installing and if you use bit locker/ or tpm it will kill it.
you need to chain load boot loaders vista to grub. 

[http://ubuntuforums.org/showthread.php?t=724817]("http://ubuntuforums.org/showthread.php?t=724817")

---

