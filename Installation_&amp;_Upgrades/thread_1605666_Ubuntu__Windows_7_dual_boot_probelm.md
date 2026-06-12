---
title: "Ubuntu / Windows 7 dual boot probelm"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by pandrangi on 2010-10-25
I have windows 7 64-bit OS on my desktop. I have installed Ubuntu 10.10 desktop 64-bit on my machine y'day. While installing I have given 500GB to Windows and 100GB to Ubuntu. I did not create separate partition for Ubuntu. Once I am done, I restarted my PC. At start up, I see black screen with couple of options to boot with: Ubuntu .....& Windows etc. The first four options are for Ubunto and next three are Windows. However, when I try to change the selection using my keyboard, it did not work. It always boots with Ubuntu. Then I called one of my friends. My friend told me to change the default parameter from "0" to "4" in grub.cfg. I did. Now, my computer is booting with Windows 7 through grub.cfg file. However, I don't see the 100GB that I have allocated for Ubuntu from Windows 7. My friend is a good Unix guy and he asked me to send the grub.cfg. He said he could edit that file so that I will be able to boot my PC with choice of Ubuntu or Windows. Since I don't see Ubuntu partition any more from Windows, How can I see and edit the grub.cfg? 
 
Since now I am in Windows, do you think I can make any changes to windows boot script so that I can boot my pc with Windows or Ubuntu? How? 
 
PLEASE HELP ME.

---

### Post by oldfred on 2010-10-26
Welcome to the forums.

You need to use a live CD to edit grub.

Have you checked your BIOS settings. A couple of years ago I installed a new motherboard and only in grub would keyboard not work. It turned out to be a setting in BIOS that both windows & Ubuntu ignore, but grub uses. Look for USB keyboard and set it to use that from BIOS.

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Once you get into Ubuntu you can use SUM - startup manager to set which system to default boot. You have to download it with synaptic.

---

