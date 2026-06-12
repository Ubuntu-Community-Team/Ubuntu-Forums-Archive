---
title: "Cannot setup dual boot windows 10 and ubuntu 16.1 with RAID partition"
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by john0246 on 2016-12-15
I've been trying for about a week to get ubuntu setup for dual boot with windows 10 but it doesn't work.  If I even want to be able view my partitions in ubuntu when i'm trying to install it i have to turn off RAID in BIOS.  When i do install Ubuntu it only works if I turn off RAID in the BIOS.  And windows 10 only works if RAID is on.  When I try to create a RAID partition in ubuntu and click the drop down menu for Use as: to try to create a RAID partition, it doesn't list the physical volume for RAID.  Is there an easier way to set this up? This seems far to complicated.  I only have one SSD 512 Gb and my laptop is xps 15 (9550).

---

### Post by oldfred on 2016-12-16
I thought it was not really RAID but a caching program like Intel SRT. RAID is really for systems with more than one identical drive.

The desktop installer does not yet work with RAID, you can use the server installer. 

Are you changing from RAID to AHCI, not IDE?
Are you booting in UEFI mode?

There are multiple threads on similar Dell systems. And a couple are mega threads (many pages). Best to start reading those from the end.
       XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[URL="http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241"]http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241
[/URL]
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843) 

[URL="http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241"]
[/URL]

---

### Post by fdanai on 2017-01-03
GM oldfred.
I read above that the DESKTOP installer does NOT YET work with RAID and you suggest the server installer, but on UBUNTU server downloads is stated that the server installer will **not **install a graphical user interface!!
Since I'm not an experienced user of UBUNTU and I need some GUI, please let me know about...

---

### Post by oldfred on 2017-01-03
Some with sever just want a gui/window manager, but not all the desktop gui packages.
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I do not normally install server, but one of its last install options is tasksel. It offers sets of packages for configuring server as Web, Data, or File. Not sure if it also offers a gui or not?

But if you want the entire desktop gui & default set of packages.
       The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
ubuntu-mate-desktop

to install at terminal then:
sudo apt-get install ubuntu-desktop

---

### Post by fdanai on 2017-01-03
Thanks again for valuable info oldfred...

---

