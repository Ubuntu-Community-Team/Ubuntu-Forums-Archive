---
title: "Trying to install Ubuntu, getting read errors and GRUB issues, been trying a while"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by condona on 2016-09-19
Hi, new to the forum. 

I'm trying to install Ubuntu 16.04.1 onto an HP Pavilion G6 laptop. It's a 4 year old machine which recently had its HDD replaced, so I needed a new OS and thought Ubuntu would be a great idea since it's free and I have some experience with it (not a huge amount, but I'm really excited about learning more!).

Installation was successful, but I'm having read errors. I've tried various things, such as reinstalling in a couple of different ways, running Boot Repair on Grub2 (since about half the time I'm getting Grub errors), and manually partitioning (but I'm not sure if I had done it right as I am relatively new to Ubuntu, followed instructions best I could). I MD5SUM checked the integrity of the installation DVD, no problems there. Most recently, I performed the "wipe HDD and reinstall Ubuntu" option to start off clean. Still errors. Ran Boot Repair again, still errors. 

Here's the paste: [http://paste2.org/L1FtFBP9](http://paste2.org/L1FtFBP9) 

Hoping it's not the hardware, but it's possible? From my limited understanding, it SEEMS fixable. Any help is appreciated.

---

### Post by oldfred on 2016-09-19
System is installed in BIOS boot mode on MBR partitioning with one large / (root) partition.

Is drive set for AHCI in BIOS/UEFI?
The old IDE setting can cause issues with a large / partition. IDE systems often could only boot from first 137GB of a drive. Often better to have a 25GB / (root) partition and use rest of drive as /home or /mnt/data partition(s).

---

### Post by condona on 2016-09-21
Thanks for responding. 

I don't have the option to change those BIOS settings. I've seen instructions about the process and have tried, but I don't have access. Just did some research, apparently HP computers around the time mine came out just didn't allow you to see and change those settings? Trying to see now if that will just completely disallow me from using Ubuntu.

---

### Post by oldfred on 2016-09-21
If UEFI system, Microsoft then required vendors to let users turn off UEFI secure boot. 
Actually Windows 7 did not support Secure boot and many customers wanted Windows 7, so they had to allow it.

---

### Post by condona on 2016-09-22
My machine came with Windows 7 preinstalled and is a BIOS system. I think if I updated the BIOS, that might mean I have the option to change the AHCI setting, but that's risky.

---

### Post by condona on 2016-09-22
Or should I try manually partitioning again in order to get around the 137gb problem? If so, do you know of a guide which would help me, a relative novice, not mess that up terribly?

---

### Post by oldfred on 2016-09-22
I always partition in advance with gparted, but still have to choose which partition is / and which is swap. Once with new drive I also made my large data partition and forgot which was which and did not pay attention. Install went into data partition. But no data yet, so just reinstalled.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 
   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

