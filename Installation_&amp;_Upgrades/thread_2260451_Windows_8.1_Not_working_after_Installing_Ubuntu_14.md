---
title: "Windows 8.1 Not working after Installing Ubuntu 14.04 LTS"
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by Vikas_Chaudhary on 2015-01-12
Dear All , 

I have installed the Ubuntu 14.04 LTS along side Windows 8.1. After it installed it did not run Ubuntu but booted always to Windows 8.1 , i checked the forum and ran boot repair after which i get the GRUB and i am able to logon into Ubuntu. The issue is that Windows 8.1 is not booting.

Here is the link i got from Boot repair - [http://paste.ubuntu.com/9717071/](http://paste.ubuntu.com/9717071/)  after i fixed the boot error.

Can someone help me out - I am new to Ubunto.

WR,
Vikas Chaudhary

---

### Post by Gordonbp531 on 2015-01-12
What make and model of computer?

---

### Post by ajgreeny on 2015-01-12
It looks as if Win 8.1 is installed as UEFI but Ubuntu is using legacy BIOS, which is going to give you huge problems.

Backup any personal files you have already made using Ubuntu, if there are any, and start again for the best way forward, following very closely the info in [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by oldfred on 2015-01-12
It looks like you originally installed a wubi install which will never work. You can delete that in Windows.

Then it looks like you did a BIOS boot install as you have grub in MBR and a bios_grub partition. But now you have ubuntu entry in UEFI. 

Does Lenovo let you boot ubuntu entry in UEFI. Have you tried with secure boot off?

If not, there are several work arounds for all those vendors that modify UEFI to only boot Windows entry.

       Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)

---

