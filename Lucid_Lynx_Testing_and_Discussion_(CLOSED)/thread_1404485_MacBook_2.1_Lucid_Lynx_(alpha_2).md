---
title: "MacBook 2.1 Lucid Lynx (alpha 2)"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sirbats on 2010-02-11
[FONT="Tahoma"]Dear Folk,
I got MacBook 2.1 with T7400 Intel Santarosa (cmiiw) core 2 duo from my wife, since she will find new laptop to follow her organization's software policy to use W******XP. Sure we can install winxp on the macbook, but her boss prefer to buy her new laptop ... :D

I have no problem to use OSX, but my wife's data is lay in the hard-disk and I have no time (yet) to tranfer. I was the user of ThinkPad T61 since 2007. My eldest son asked the T61 since I got macbook. In all respects (minus design), T61 is better than this macbook. Thus I decided to install ubuntu on the book, just ubuntu not dual boot :P

Fisrt, I plug the HDD ex-T61 with Lucid alpha2 on it, and everything fine. I have to remove nvidia drivers and other nvidia vga related drivers, since the macbook have intel vga (945),

after 5 days, I decided to do fresh install LL 10.04 alpha-2, installation went well, but I can not log in, due to the macbook's keyboard completely not work.

I change fresh install with karmic and do # ... dist-upgrade, after 7-11 rebooting the syetem just hang with blank screen. I did reinstall again with LL alpha2 to ensure that the keyboard is really NOT WORK. Well that is true, the keyboard did not work at all. I can not choose recovery mode due to never able to do FIRST LOG-in.

By using 'alternate cd' I get into recover broken system. Removing mouseemu as suggested by some forum, modify grub-setting to enable get grub menu on booting. everything fine, I can log in and do some modification, adding application etc. However after 5-7 rebooting system back to hang with black blank screen .... :P

So, I have to accept and happy with karmic which is everything went well, but I wants LUCID on this piece of beautfull hardware.

After reading from googling result, Im aware the most problem is lucid is hal free, change from usplash to plymouth. I do little trial, removing hal in Karmic system, caused broken of GDM, xserver, xorg. Thus I install xdm first, during installation change default dm from gdm to xdm (I hope at least I can login), removing ubuntu-desktop (meta package ?), removing all xserver-sxorg-video-driver, unless intel, vesa, v4l.

change kamic repository to lucid repository and deactivate lucid-backport. do # aptitude dist-upgrade ..... <I will tell you the result later> ...[/FONT]

---

### Post by sirbats on 2010-02-12
> **sirbats said:**
> [FONT="Tahoma"] ...
change kamic repository to lucid repository and deactivate lucid-backport. do # aptitude dist-upgrade ..... <I will tell you the result later> ...[/FONT].I will tell little details as sharing, since 10.04 is on alpha-2 stage. I believed 10.04 will be great at the released stage.

First : install xdm $ sudo aptitude install xdm, during installation choose xdm as your dm. (suggest: do this in recovery mode, terminal log-in only, but you better have terminal browser like lynx, links for asking any help in case face problem). But I did on full desktop environment :D for convenient searching help by firefox

Second : remove ubuntu-desktop (meta-package), the reason is : ubuntu will find other window manager other than metacity without unbuntu-desktop meta-package <Note : Im just normal user, thus this opinion could be NOT CORRECT).

[HTML]The following packages will be REMOVED:
  ubuntu-desktop 
0 packages upgraded, 0 newly installed, 1 to remove and 1004 not upgraded.
Need to get 0B of archives. After unpacking 57.3kB will be freed.
Writing extended state information... Done
(Reading database ... 140274 files and directories currently installed.)
Removing ubuntu-desktop ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done[/HTML]

Third : remove the following package : 
[HTML]sudo aptitude remove hal empathy-doc libdbusmenu-glib0 libdbusmenu-gtk0 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 usplash usplash-theme-ubuntu
[/HTML]

Fourth : after all above done, change karmic repository to lucid repository, deactivate ***lucid-backports*** repository to ensure only basic ubuntu system will be upgraded.

Fifth : $ sudo aptitude dist-upgrade

After completing upgrade : reboot and everything fine. sure I got ugly XDM log-in screen, but everything worked well. Next just install gdm and other applications we need as normal ubuntu 

**Testing** by doing more than fifteen times reboot ... and everything went well. So I have complete **single boot** Lucid Lynx on MacBook 2.1

**iSight, Keyboard-Map and other stuffs** easily to be found on the net.

This is my output on lspci command
[HTML]mac@APPLE:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
[/HTML]

---

