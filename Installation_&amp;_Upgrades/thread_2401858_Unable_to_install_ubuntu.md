---
title: "Unable to install ubuntu"
date: 2018-09-23
forum: Installation &amp; Upgrades
---

### Post by trexmkii on 2018-09-23
Hi,
I'm trying to install ubuntu on my Dell Inspirion 7359 laptop.
I've downloaded ubuntu 18.04, installed onto a USB drive and booted into the installation (UEFI mode).
I go through the setup process but before it even starts copying files to the drive it just hangs (at first the mouse cursor is showing busy and then after a few minutes the entire installation just freezes completely including the mouse cursor). Sometimes I'm able to get to the timezone selection screen and other times it hangs even before that. 
I've also tried installing other Linux distros (Mint, Kali) with the exact same results. I've tried using different tools to create the USB installer (Rufus, Win32 disk imager) with no change.

I'm guessing it has something to do with a specific setting in the BIOS but I haven't been able to pinpoint it.
Anyone have this problem? What am I doing wrong here?

Edit: 
My System specs are:
CPU: Intel Core i3 6100U
RAM: 8gb DDR3L
HDD: 500gb WD

---

### Post by RobGoss on 2018-09-23
Hello and welcome, It would be a good idea to post the specs for your machine, that way others can also try to pin point the troubles your having. I have a number of dells running Ubuntu with out any issues so I know it's can be done

---

### Post by trexmkii on 2018-09-23
Hi,
I've added my system specs to the original post.

---

### Post by RobGoss on 2018-09-23
Thanks so much for doing that, Your specs seems more then enough to handle Ubuntu. I'm thinking it's something to do with the Bios settings

How does the Live desktop run when you boot in to it? Have you checked **Fast startup **maybe it needs to be disabled

---

### Post by trexmkii on 2018-09-24
I am a able to boot into the live desktop but after a few minutes the same thing happens, the system freezes. 
So after spending half the night trouble shooting and running diagnostics on my laptop I've figured out that it's a hardware issue, a fault VRM being the most likely culprit at this point.

---

### Post by oldfred on 2018-09-24
Dell needs UEFI update.
And then in UEFI turn off RAID or Intel SRT for drives and set to AHCI mode.

Issues similar across many Dell models.
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
      
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359) 

    Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642) 
    [https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)

---

