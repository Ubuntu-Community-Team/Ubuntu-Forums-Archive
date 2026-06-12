---
title: "Grub dont load after installation"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by tpiardi on 2013-09-03
I`m tryeing to install ubuntu on my new pc, that already has windows 8 running.
But everytime I install ubuntu, it`s dont recognize the grub and or boot direct to windows or give me grub rescue.
Used boot-repair, and the boot come back to work, but past that, my ubuntu don`t recognize my mouse and web.
Before restarting popup about low graphic setting apears on the screen, but i coudnt do nothing...
Did the reinstall several times, same result  :(

Here my boot-repair report
[http://paste.ubuntu.com/6060792/]("http://paste.ubuntu.com/6060792/")

Anyone has any Idea what can I try?

---

### Post by oldfred on 2013-09-03
It looks like sda is BIOS/MBR but you have gpt partitions on sdb.

If you can boot then the issue is not booting, but drivers for video and perhaps Internet. Mouse may be related to Internet.

What systems is this.
And what video does it have?

This normally is just to get you into system so you can install proprietary drivers.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by tpiardi on 2013-09-04
I can boot only after usng boot repair, but then they give me the drivers errors.

I removed sdb and deleted the windows partition and Installed again, this time 13.10 (b4 was 13.04)
and got this error: 

ERROR: file `/boot/grub/i386-pc/normal.mod` not found
Grub Resce:

About the drivers problems
My pc is:
Intel core i5-3300
MB PCware IPMH51P1
8gb mem
Video Radeon HD 4670

Working perfect fine on live cd.

---

### Post by oldfred on 2013-09-04
The liveCD is using default graphics that nomodeset should give you. 
Perhaps forcing another legacy mode will work also.

This is now older, so I am not sure they all work, most use nomodeset now.
 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

I think the current AMD drivers only support 5000 and above versions. You will need the legacy drivers or just the open source drivers.
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by tpiardi on 2013-09-04
Thanks, solved it deleting all partitions and reinstalling,
It was some bug on mbr/gtp stuff.

---

