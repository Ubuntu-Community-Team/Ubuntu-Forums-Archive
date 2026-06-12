---
title: "Sata Dual Boot Windows Xp"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by ralphz on 2007-03-04
Hi

I was installing Ubuntu on one of my desktops with Windows XP already on it. The installation went smoothly but after reboot I can't get to the Ubuntu.  Windows is loading as an default OS. There is no boot menu or anything like that...
How can I correct my installation. Preferably without reinstalling Ubuntu.

My partitions look like this:
$ cat /proc/partitions
major minor  #blocks  name

   8     0  244198584 sda
   8     1   51199123 sda1 (windows xp)
   8     2  102398310 sda2
   8     4   90598567 sda4
   8    16  195360984 sdb
   8    17  102398278 sdb1
   8    18   20635492 sdb2 (ubuntu)
   8    19    1012095 sdb3 (swap)
   7     0     647432 loop0

Both drives are SATA II.

During the installation I was informed that grub will be installed to (hd0). I presume it was not correct choice.

Please help.
Ralph

---

### Post by Kateikyoushi on 2007-03-04
Did you try to boot from the other disc ?

---

### Post by ralphz on 2007-03-04
What do you mean form the other disc ?

---

### Post by Kateikyoushi on 2007-03-04
Change the boot order between the two hdd.

---

### Post by ralphz on 2007-03-04
How can I do this?

I think what i want to achive is the boot menu (from windows or grub) so i can choice the system i'd like to boot to. 

Just want to rremind that the drives are SATA not PATA and the Ubuntu is on the secand partition of the second drive /dev/sda2.

---

### Post by Kateikyoushi on 2007-03-04
You can nter the bios by holding down the del button at boot this is so on most bios but it is displayed at boot, also newer bioses let you change boot order by pressing a button at boot.

What I think happened that grub was installed on the second drive and you are booting from the first so you go to windows just like before the installation.

---

