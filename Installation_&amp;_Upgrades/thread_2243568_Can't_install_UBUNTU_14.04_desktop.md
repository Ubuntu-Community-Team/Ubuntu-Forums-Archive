---
title: "Can't install UBUNTU 14.04 desktop"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by red16 on 2014-09-09
Hello.

I am trying to install UBUNTU 14.04 Desktop from USB, but after I click 'Install Ubuntu' the screen get stuck.


Please help me!!

---

### Post by yancek on 2014-09-09
You would have to post some information on the hardware you are using.  Unless you indicate otherwise, we will expect that there is no other operating system on the computer and it is a blank drive.

---

### Post by ubfan1 on 2014-09-09
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
3) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

---

### Post by red16 on 2014-09-10
I have windows XP installed.

Machine is pretty old. Intel core 2 duo 2.8 Ghz, 1,5 GB RAM, 160 hdd, ATX Radeon (I forget which one) 1 GB PCI Express

@ubfan 1 I did not checked from md5sum, but if I try to check media I get the same thing.
I will also check the memory.

---

### Post by oldfred on 2014-09-10
You probably need nomodeset. I have similar system but with 4GB of RAM and nVidia and have to use nomodeset to get system to boot live installer and after install first boot or until proprietary driver is installed.

You need to know AMD version. Current AMD driver only supports newer cards and you may need legacy driver for older one. Or open source driver may be ok?

       open (Gallium3D) and closed-source (Catalyst) driver
      
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
      
 This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for several versions of Ubuntu.
[URL="https://launchpad.net/~makson96/+archive/fglrx"]https://launchpad.net/~makson96/+archive/fglrx

      [/URL]
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    [URL="https://launchpad.net/~makson96/+archive/fglrx"]
[/URL]

---

