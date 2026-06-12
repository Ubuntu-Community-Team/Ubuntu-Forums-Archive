---
title: "DUAL BOOT with WINDOWS 10"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by dr.anandravi on 2016-11-10
Hi!
I have purchased Lenevo yoga 500 with preinstalled windows 10 and I installed ubuntu 16.04 and it has been installed also but system is booting only in windows. I have tried general tricks available like disabling secure boot, etc. I have started using ubuntu with jonty jackpole but now unable to get it on this new machine. Tried boot repair which says cannot be done in legacy mode and UEFI mode does not boot into USB and a lot other. Any help please.

---

### Post by yancek on 2016-11-10
Your first step to get help is to post a link to the output from boot repair.  Run it again and select the option to Create BootInfo Summary and post a link to the output here.  

First guess would be that windows was using UEFI and you installed Ubuntu MBR which always causes problems.  The boot repair output should tell us that.

---

### Post by oldfred on 2016-11-10
There were complaints that Lenovo (with Microsoft) limited systems to Windows only.
[http://news.lenovo.com/news-releases/corporate/lenovo-statement-on-linux-support-for-yoga.htm](http://news.lenovo.com/news-releases/corporate/lenovo-statement-on-linux-support-for-yoga.htm)

Lenovo has so many models, not sure what might be most similar to yours.
 Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)

---

### Post by dr.anandravi on 2016-11-10
Thanks a lot for help, the followings are the terminal lines of boot repair"
```
ubuntu@ubuntu:~$ sudo apt-add-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpy8h1k586/secring.gpg' created
gpg: keyring `/tmp/tmpy8h1k586/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpy8h1k586/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1) xenial Release
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]               
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Get:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial InRelease [17.5 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [159 kB]
Get:8 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial/main i386 Packages [1,864 B]
Get:9 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial/main Translation-en [2,092 B]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]     
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [67.8 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 DEP-11 Metadata [82.9 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [62.9 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages [6,528 B]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en [2,016 B]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 DEP-11 Metadata [199 B]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages [1,196 kB]   
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main Translation-en [568 kB]    
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 DEP-11 Metadata [733 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons [409 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [414 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [161 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 DEP-11 Metadata [334 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [199 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages [6,528 B]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en [2,016 B]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 DEP-11 Metadata [156 B]
Fetched 4,862 kB in 40s (119 kB/s)                                             

** (appstreamcli:5486): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit python-gi
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc python-gi-cairo
Recommended packages:
  gksu
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit
  python-gi
0 upgraded, 8 newly installed, 0 to remove and 519 not upgraded.
Need to get 1,247 kB of archives.
After this operation, 5,219 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 libsigsegv2 i386 2.10-4 [14.0 kB]
Get:2 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial/main i386 glade2script all 3.2.3~ppa1 [36.8 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 gawk i386 1:4.1.3+dfsg-0.1 [407 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 python-gi i386 3.20.0-0ubuntu1 [205 kB]
Get:5 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial/main i386 boot-sav all 4ppa38 [416 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 pastebinit all 1.5-1 [14.6 kB]
Get:7 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial/main i386 boot-repair all 4ppa38 [11.5 kB]
Get:8 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial/main i386 boot-sav-extra all 4ppa38 [142 kB]
Fetched 1,247 kB in 9s (127 kB/s)                                              
Selecting previously unselected package libsigsegv2:i386.
(Reading database ... 191267 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-4_i386.deb ...
Unpacking libsigsegv2:i386 (2.10-4) ...
Setting up libsigsegv2:i386 (2.10-4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Selecting previously unselected package gawk.
(Reading database ... 191275 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.1.3+dfsg-0.1_i386.deb ...
Unpacking gawk (1:4.1.3+dfsg-0.1) ...
Selecting previously unselected package python-gi.
Preparing to unpack .../python-gi_3.20.0-0ubuntu1_i386.deb ...
Unpacking python-gi (3.20.0-0ubuntu1) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.3~ppa1_all.deb ...
Unpacking glade2script (3.2.3~ppa1) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa38_all.deb ...
Unpacking boot-sav (4ppa38) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa38_all.deb ...
Unpacking boot-repair (4ppa38) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa38_all.deb ...
Unpacking boot-sav-extra (4ppa38) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.5-1_all.deb ...
Unpacking pastebinit (1.5-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up gawk (1:4.1.3+dfsg-0.1) ...
Setting up python-gi (3.20.0-0ubuntu1) ...
Setting up glade2script (3.2.3~ppa1) ...
Setting up boot-sav (4ppa38) ...
Setting up boot-repair (4ppa38) ...
Setting up boot-sav-extra (4ppa38) ...
Setting up pastebinit (1.5-1) ...
ubuntu@ubuntu:~$ boot-repair
ubuntu@ubuntu:~$ /usr/bin/glade2script:49: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/bin/glade2script:4800: PyGIWarning: Notify was imported without specifying a version first. Use gi.require_version('Notify', '0.7') before import to ensure that the right version gets loaded.
  from gi.repository import Notify
/usr/bin/glade2script:4804: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as appindicator
And after clicking boot repair in boot repair window the following msg popped up:
The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode.
```

---

### Post by oldfred on 2016-11-10
It is telling you that you have an UEFI system and you booted installer/Boot-Repair in BIOS boot mode.

How you boot install media, is then how it installs.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by dr.anandravi on 2016-11-10
Thanks a lot, I will get back to you after trying suggested threads.

---

### Post by dr.anandravi on 2016-11-11
Hi! 
I started trying the new strategies but i am unable to boot from usb keeping my machine in UEFI mode (as it boots in usb in legacy mode) hence could make no advance. any suggestion please.

---

### Post by oldfred on 2016-11-12
If your flash drive is correct, it will have two boot modes from UEFI.
Some work better with UEFI Secure boot off. Many have to also have allow USB boot or settings on USB to UEFI boot, especially if secure boot is on.

Second screen shows a Toshiba flash drive with UEFI boot and boot (BIOS) options.

---

### Post by dr.anandravi on 2016-11-12
First of all, Thanks a lot!
Ii have prepared my usb using Rufus in GPT - UEFI mode and is working fine under legacy and this way I am able to install also. BUT it is not poping up option to boot selection (ubuntu or windows)and starts in windows automatically. There is already a EFI partition in  my machine. As suggested both install must be same mode, i am trying to also, but in UEFI mode MACHINE IS NOT BOOTING FROM USB and I think this my main problem. Any help please!

---

### Post by oldfred on 2016-11-13
If you have installed Ubuntu in BIOS mode on a gpt partitioned hard drive with an existing ESP, you can use Boot-Repair to convert to UEFI boot.
It actually just uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI). That also does some reconfiguration, but makes it UEFI boot.

Better to install Boot-Repair to Ubuntu installer when booted in UEFI mode, but I think it will still convert if BIOS mode.

You still may need to check UEFI settings for USB boot. My motherboard had settings to allow USB boot. Then it also had USB (or make just any external drive) settings for BIOS, BIOS or UEFI(UEFI first) and UEFI only. And the only setting that worked was UEFI only. Even the UEFI first would not actually boot in UEFI mode.

---

### Post by dr.anandravi on 2016-11-13
Thanks a lot for help
Boot repair out put link: http:/paste2.org/HYaDjekE

---

### Post by dr.anandravi on 2016-11-13
Thanks again and I tried the boot repair link to produce out put link:
[http://paste2.org/HYaDjekE](http://paste2.org/HYaDjekE)

---

### Post by dr.anandravi on 2016-11-13
Thanks again and I tried the boot repair link to produce out put link:
[http://paste2.org/HYaDjekE](http://paste2.org/HYaDjekE)

---

### Post by oldfred on 2016-11-13
Key messages in Summary report, that I see:
>   Windows not detected by os-prober on sda3.
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
SecureBoot maybe enabled.
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue? 



You have installed Ubuntu in BIOS boot mode on UEFI system. 
With Secure boot on, you cannot boot installed system in BIOS mode.
And to boot flash drive with Secure boot on, you normally have to enable/allow USB boot.

If you want BIOS boot mode for Ubuntu you have to add a tiny 1 or 2MB unformatted partition with the flag bios_grub. You can use gparted. But better to use UEFI.
Boot-Repair in advanced mode can convert your install to UEFI boot. But better to boot in UEFI mode.
And often easier with Secure Boot off, but should not be required.

It looks like you left Windows fast start up on. That needs to be off.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

