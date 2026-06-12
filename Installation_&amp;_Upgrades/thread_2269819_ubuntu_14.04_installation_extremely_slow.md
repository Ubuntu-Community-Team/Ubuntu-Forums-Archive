---
title: "ubuntu 14.04 installation extremely slow"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by steve195 on 2015-03-18
Hello, I searched a lot and could find no answers about this installation problem

My system consists of the following:
AMD 64 3400+ processor
200 gb hdd
4 gb ram
onboard nvidia graphics

There is no problem installing Ubuntu 10.04 and it runs fine once I get graphics drivers installed
There is no problem installing or running XP

I downloaded Ubuntu 14.04 iso then burned and verified disc
the hard drive is clean with no partitions
Ubuntu is to be the only operating system
upon booting the 14.04 dvd, there are errors about accessing regions and soft lockups
downloaded, burned and verified new disc
same result, however:

After an hour, I get a grey screen with a white bar at the top
After another half hour I have a live cd desktop and choose install
After 15 more minutes I can select an install option
8 hours later install complete so I removed disc and rebooted
running very slow but mouse and keyboard speed are ok

Does this problem have anything to do with onboard nvidia graphics?
I would like to find a way to cut the install time from 9.75 hours to 1 or 2 hours

---

### Post by dino99 on 2015-03-18
thats weird
10.04 is fully dead, so why installing it ?

if you then have done a dist-upgrade, it is verified only if 10.04 -> 12.04 -> 14.04 ; otherwise be ready to find workarounds for what have not been tested.
In all cases, the system might not be disturbed/used for something else than upgrading. All 'extra'/'exotic' packages have to be set back to genuine version first (ppa purged if existing)

---

### Post by steve195 on 2015-03-18
I installed 10.04 only as a test to see if it was slow
it installed in less than 2 hours and ran fine
I cleaned the hard drive then installed xp
it installed in less than 2 hours and ran fine
I cleaned the hard drive and every time I try to install 14.04 I have the same problem I posted about
I am not doing an upgrade, I start with a clean hard drive each time

---

### Post by grahammechanical on 2015-03-18
My machine has a lot less RAM than your machine and it will install the very latest ubuntu in less than an hour. You may need to use an F6 option. Possibly nomodeset or even a combination of F6 options. See, Changing the CDS default Boot Options - section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Once Ubuntu is installed it should not run slow. You might be running on an open source video driver called llvmpipe. System Settings>Details will say if you are using llvmpipe. If it says Gallioum, then it is Nouveau. If it describes the video adapter then you are using a proprietary video driver. There are three reason why we get llvmpipe:

1) we are loading through Recovery mode Resume.
2) the video adapter cannot do hardware accelerated 3D rendering and so cannot run Unity.
3) there is a conflict with the proprietary video driver.

Ubuntu will give us the latest stable video drivers which may not support an older video card. Nvidia is in the habit of dropping support for cards that it considers obsolete from its newest drivers.

Ubuntu 10.04 would have given you a driver that supported that card. Ubuntu 14.04 may be giving a driver that does not support that card. Try installing without ticking "install third party software." Then you will get the open source video driver - Nouveau.

Regards.

---

### Post by steve195 on 2015-03-18
So, I booted up and after a while got a black screen and a mouse.
I pressed Ctrl + Alt + F1 to open terminal (which seemed to be the whole screen)
Once I logged in I started seeing this repeating over and over:

          [ xxx.xxxxxx] [Hardware Error]: MC1 Error: Copyback Parity/Victim error.
          [ xxx.xxxxxx] [Hardware Error]: Error Status: Corrected error, no action required.
          [ xxx.xxxxxx] [Hardware Error]: CPU:0 (f:2f:0) MC1_STATUS[-|CE|-|-|-]: 0x9000000000000171
          [ xxx.xxxxxx] [Hardware Error]: cache level: L1, tx: INSN, mem-tx: EV

As per my original post and comparing these errors with what I found online, 
it seems that my processor is capable of running all Microsoft Operating Systems 
and only Ubuntu or Linux as long as the kernel is version 3.14 or less

I don't know if there is a workaround or some BIOS setting that can fix 
It does not look good for using current kernel releases with older hardware

---

### Post by steve195 on 2015-03-20
Is there any way for me to diagnose why this kernel runs so slow on my hardware?

---

