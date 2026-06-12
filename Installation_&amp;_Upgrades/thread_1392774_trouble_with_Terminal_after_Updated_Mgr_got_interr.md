---
title: "trouble with Terminal after Updated Mgr got interrupted"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by wanderingarticfox on 2010-01-28
I was running Update manager and my old system pull a 'freeze/lockup' before things were completed so I have tried using apt-get ; I first updated then upgraded and get the same issue as in Update mgr with 2 small packages, 1 Rythmbox and 1 software center. This is the terminal just before, during and after:

               -desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libsmbclient libwbclient0 rhythmbox samba-common
  samba-common-bin smbclient software-center
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 18.4MB/20.2MB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main libwbclient0 2:3.4.0-3ubuntu5.4 [102kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main libsmbclient 2:3.4.0-3ubuntu5.4 [1,652kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main smbclient 2:3.4.0-3ubuntu5.4 [11.4MB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main samba-common 2:3.4.0-3ubuntu5.4 [387kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main samba-common-bin 2:3.4.0-3ubuntu5.4 [4,787kB]
Fetched 18.4MB in 3min 11s (95.8kB/s)                             
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.2_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libwbclient0_2%3a3.4.0-3ubuntu5.4_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libsmbclient_2%3a3.4.0-3ubuntu5.4_i386.deb
E: Prior errors apply to /var/cache/apt/archives/smbclient_2%3a3.4.0-3ubuntu5.4_i386.deb
E: Prior errors apply to /var/cache/apt/archives/samba-common_2%3a3.4.0-3ubuntu5.4_all.deb
E: Prior errors apply to /var/cache/apt/archives/samba-common-bin_2%3a3.4.0-3ubuntu5.4_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/software-center_1.0.3_all.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-deb: `/var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.2_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.2_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
(Reading database ... 206820 files and directories currently installed.)
Preparing to replace libwbclient0 2:3.4.0-3ubuntu5.3 (using .../libwbclient0_2%3a3.4.0-3ubuntu5.4_i386.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace libsmbclient 2:3.4.0-3ubuntu5.3 (using .../libsmbclient_2%3a3.4.0-3ubuntu5.4_i386.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace smbclient 2:3.4.0-3ubuntu5.3 (using .../smbclient_2%3a3.4.0-3ubuntu5.4_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 2:3.4.0-3ubuntu5.3 (using .../samba-common_2%3a3.4.0-3ubuntu5.4_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-common-bin 2:3.4.0-3ubuntu5.3 (using .../samba-common-bin_2%3a3.4.0-3ubuntu5.4_i386.deb) ...
Unpacking replacement samba-common-bin ...
dpkg-deb: `/var/cache/apt/archives/software-center_1.0.3_all.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/software-center_1.0.3_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.2_i386.deb
 /var/cache/apt/archives/software-center_1.0.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
           -desktop:~$ place samba-common-bin 2:3.4.0-3ubuntu5.3 (using .../samba-common-bin_2%3a3.4.0-3ubuntu5.4_i386.deb) ...
bash: syntax error near unexpected token `('
           -desktop:~$ Unpacking replacement samba-common-bin ...
Unpacking: command not found
           -desktop:~$ dpkg-deb: `/var/cache/apt/archives/software-center_1.0.3_all.deb' is not a debian format archive
> dpkg: error processing /var/cache/apt/archives/software-center_1.0.3_all.deb (--unpack):
>  subprocess dpkg-deb --control returned error exit status 2
> Processing triggers for man-db ...
> Errors were encountered while processing:
>  /var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.2_i386.deb
>  /var/cache/apt/archives/software-center_1.0.3_all.deb
> E: Sub-process /usr/bin/dpkg returned an error code (1)
>           -desktop:~$ 
> 
 I know that is long but I'm newbie and figure better a little to much than not enough information. help if you can.

---

### Post by wanderingarticfox on 2010-01-29
I'm still trying to figure out what is wrong here. I've read this many times and do not know what to do. I would appreciate any help in learning and fixing. Thank You.

-desktop:~$ dpkg-deb: `/var/cache/apt/archives/software-center_1.0.3_all.deb' is not a debian format archive
> dpkg: error processing /var/cache/apt/archives/software-center_1.0.3_all.deb (--unpack):
> subprocess dpkg-deb --control returned error exit status 2
> Processing triggers for man-db ...
> Errors were encountered while processing:
> /var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.2_i386.deb
> /var/cache/apt/archives/software-center_1.0.3_all.deb
> E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wanderingarticfox on 2010-01-29
I ran   sudo dpkg --configure -a    in the terminal, and this is what I got back   
     Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-esound-compat (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Errors were encountered while processing:
 rhythmbox
 pulseaudio
 pulseaudio-module-bluetooth

Please help. I'm trying to learn here.

---

### Post by wanderingarticfox on 2010-01-29
I'm reading a this info and have tried installing the rhythmbox and pulse audio stuff, even tried uninstalling and reinstalling all of rhythmbox. I think something is 'hung' up or broken from when my system locked-up/froze during the use of update manager. these are the latest:

33333333333-desktop:~$ sudo dpkg --configure -a
[sudo] password for 33333: 
dpkg: error processing rhythmbox (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of rhythmbox-dbg:
 rhythmbox-dbg depends on rhythmbox (= 0.12.5-0ubuntu5.2); however:
  Version of rhythmbox on system is 0.12.5-0ubuntu5.1.
dpkg: error processing rhythmbox-dbg (--configure):
 dependency problems - leaving unconfigured

 Package pulseaudio-module-raop is not configured yet.
dpkg: error processing pulseaudio-module-raop-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-esound-compat:
 pulseaudio-esound-compat depends on pulseaudio (= 1:0.9.19-0ubuntu4.1); however:
  Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-esound-compat (--configure):
 dependency problems - leaving unconfigured

I imagine I have overlooked something but being new to terminal commands that should not be surprising  Help if you can..

---

