---
title: "Installing Ubuntu on Acer nitro 5"
date: 2020-01-23
forum: Installation &amp; Upgrades
---

### Post by albrechtmyers on 2020-01-23
I have an Acer model of AN 515 52 58JV and I am not able to complete the installation due to the following:
  You need at least 8.6 GB disk space to install Ubuntu. This computer has only 4.0GB!?
  And GParted showed me this only: /dev/sdb1 directory only.
  What can be done? I have windows 10 installed.
[https://4kpornindex.com/](https://4kpornindex.com/)

---

### Post by RobGoss on 2020-01-23
> **albrechtmyers said:**
> I have an Acer model of AN 515 52 58JV and I am not able to complete the installation due to the following:
  You need at least 8.6 GB disk space to install Ubuntu. This computer has only 4.0GB!?
  And GParted showed me this only: /dev/sdb1 directory only.
  What can be done? I have windows 10 installed.

Are you saying your machine only has 4.GB of storage or 40.GB

---

### Post by ajgreeny on 2020-01-23
We need a lot more information in order for anyone to help you with this problem.

Boot to your live Ubuntu USB or DVD system and using that run terminal command ```
sudo fdisk -l
``` then still using the live system come back here and copy the output you get from that command in a reply to this thread.  That will give us a lot of information about the hard disk(s) on your computer and their current usage.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by oldfred on 2020-01-24
It seems like it is only seeing flash drive.
Update UEFI and SSD firmware if SSD.

[SOLVED]Acer Nitro 5 (with Ryzen 7 2700U, RX 560X) Ubuntu 18.10  
[https://ubuntuforums.org/showthread.php?t=2413504](https://ubuntuforums.org/showthread.php?t=2413504) &
[https://ubuntuforums.org/showthread.php?t=2412117](https://ubuntuforums.org/showthread.php?t=2412117) &
[https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42](https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42)
Acer Nitro 7 Missing AHCI mode Ctrl + S in UEFI
[https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969](https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969)
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
A

---

