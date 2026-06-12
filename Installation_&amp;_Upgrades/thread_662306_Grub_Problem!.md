---
title: "Grub Problem!"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by shwetanshu on 2008-01-08
I had windows XP installed, i then installed Vista.... after that i installed** Ubuntu 7.10**... on a 19gb partition (/dev/sda7) with 1 gb swap (/dev/sda.

after i restarted the PC, i m still getting the same boot option as i got before installing UBUNTU....

1)Previous Version of Windows
2)Microsoft Windows Vista

So i m not able to boot into Ubuntu in anyway... during installation, i did not import any User account from Vista wen it asked me to and installer was not able to download any updates, after that installation went fine... it then asked whether to continue using LIVE CD or Reboot and boot into Ubuntu.... i chose the latter but after rebooting... i still got the above said options...

My PC:
E4600 C2D 2.4 GHz
Intel DG33BU Mobo
2x1GB Transcend RAM Modules @ 667MHz
XFX 8600 GT
Seagate Sata 2 320GB <--- installed all OS in this one
Seagate 160GB PATA
Benq DW 1640 DVD Writer
Pinnacle TV Tuner

then i followed this link : [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

grub did come up, but after i chose vista bootloader, vista bootloader came up.. den i selected Previous Version of Windows and the PC restarted and i happened again and again

so i restored the mbr usng fixmbr and then used fixboot command.. now i boot directly into XP...i have formatted my vista.... now i want just Ubuntu and XP... but stil wen i perform the grub restoration, it stil recognizes the Vista Bootloader... so i cant boot in2 windows... wat to do??

the error shown on choosing Vista Bootloader is NTLDR Missing...

---

### Post by logos34 on 2008-01-08
Post output of the following:

sudo fdisk -l

cat /boot/grub/menu.lst

(i'm thinking grub windows entry is pointing to missing vista partition)

---

