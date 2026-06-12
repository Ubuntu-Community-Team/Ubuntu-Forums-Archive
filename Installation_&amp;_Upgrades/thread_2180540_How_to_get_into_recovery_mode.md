---
title: "How to get into recovery mode"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by blom0344 on 2013-10-13
Would you explain HOW you get into recovery mode?   Where do you issue  the  **sudo apt-get isntall nvidia-173 ****comma**[B]nd ?  , on what command line?  Where?

Do you mean the installation was not complete without the nomodeset?[/B]

---

### Post by ibjsb4 on 2013-10-13
> **blom0344 said:**
> Would you explain HOW you get into recovery mode?   Where do you issue  the  **sudo apt-get isntall nvidia-173 ****comma**[B]nd ?  , on what command line?  Where?

Do you mean the installation was not complete without the nomodeset?[/B]

Hi blom0344

If you would start your own thread with a link to this one, it would be a good idea.  Answering to other than the original poster will become confusing.

---

### Post by Iowan on 2013-10-13
New thread created from here:
[http://ubuntuforums.org/showthread.php?t=2180173](http://ubuntuforums.org/showthread.php?t=2180173)

---

### Post by grahammechanical on 2013-10-13
Recovery mode is different to going into Grub command line mode which is for entering commands that Grub will use to boot Linux. May be. May be not. Are running a Wubi installation of Lubuntu or Ubuntu? Do you see a Grub menu?

At the Grub menu you select Recovery mode. If it is 12.04 the Recovery mode will be in the list. If it is 13.04 then we look in the Advanced Options for Ubuntu. At the Recovery menu we get these options

resume                  - Resume normal boot
clean                     - Try to make free space
dpkg                     - Repair broken packages
failsafeX                - run  in failsafe graphic mode
fsck                      - Check file system
grub                     - Update grub boot loader
network                - Enable networking
root                     - Drop to root shell prompt
system-summery  - system summery

You want root but the file system will be in read only mode. So, we cannot make changes to system files. We need read/write mode. A simple way is to first run network. We may need this if we wish to run apt-get to install something. That will return us to the recovery menu with the file system in read/write mode and then we can choose root.

We can also try Resume. that can get us to a working desktop without activating a video driver. We may then be able to use Additional Drivers to change video drivers.

Regards.

---

### Post by ibjsb4 on 2013-10-14
Hi blom344 :)

Have you solved this?

---

### Post by blom0344 on 2013-10-14
Actually no..  I got the tip to try puppy linux first.  Downloaded it, installed it, got a working Linux out of the box running on my 9 year old laptop.
I fear that old hardware and the latest Ubuntu version is asking for trouble...   :(

---

### Post by ibjsb4 on 2013-10-14
> **blom0344 said:**
> I fear that old hardware and the latest Ubuntu version is asking for trouble...   :(

This can be a problem.  There is Lubuntu and Xubuntu that uses less resources and runs better on older computers.  But Puppy Linux is a good choice, it has been around for years and is compatible with Ubuntu.  Meaning that it will run Ubuntu software.

---

