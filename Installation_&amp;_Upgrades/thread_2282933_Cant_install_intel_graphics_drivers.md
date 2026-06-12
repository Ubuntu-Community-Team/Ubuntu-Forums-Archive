---
title: "Cant install intel graphics drivers"
date: 2015-06-17
forum: Installation &amp; Upgrades
---

### Post by dan176 on 2015-06-17
[SIZE=1][SIZE=2]so i recently got a Gigabyte Brix [FONT=Arial][COLOR=#111111]GB-BXBT-2807 and it is well documented that by default this cpu is not hardware accelerated out of the box with Ubuntu so getting the graphics drivers is needed. [/COLOR][/FONT]
[FONT=Arial][COLOR=#111111]No [/COLOR][/FONT][COLOR=#111111]matter what way i try to install them i always get the same error though. Error shown in screenshot, using the following steps: [/COLOR]http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html[COLOR=#111111]
this persisted even when i upgraded from 14.04 to 14.10 FYI.

as you can see, it is clearly not able to download these two files that are apparently needed for the driver install?
[/COLOR]```
[COLOR=#111111]/glasen/intel-driver/ubuntu/dists/trusty/main/binary-amd64/Packages[/COLOR]
```[/SIZE][COLOR=#111111][SIZE=2]
and[/SIZE]
[/COLOR][/SIZE]```
[COLOR=#111111]/glasen/intel-driver/ubuntu/dists/trusty/main/binary-i386/Packages[/COLOR]
```[COLOR=#111111]

then it gives me the error
```
the following packages have unmet dependencies: 
xserver-xorg-video-intel : depends on
 xorg-video-abi-15
 xserver-xorg-core(>=2:1.14.99.902)[FONT=Arial]

unable to correct problems, you have held broken packages
[/FONT]
```[FONT=Arial]

what do i do?[/FONT][/COLOR]

---

### Post by mc4man on 2015-06-17
Well you stop trying to use packages for 12.04 on 14.04/14.10 
I guess if you need need that latest Intel drivers for that little box then you can find an installer here,  **14.10 only**
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

---

### Post by dan176 on 2015-06-17
wow cant believe i made that mistake...... please hold while i go up to 14.10 and try again

---

### Post by dan176 on 2015-06-18
ok ive run into a major problem while updating to 14.10. i get the black screen. using ctrl+alt+f1 does bring up the terminal but everything ive tried from other threads has not worked.

---

