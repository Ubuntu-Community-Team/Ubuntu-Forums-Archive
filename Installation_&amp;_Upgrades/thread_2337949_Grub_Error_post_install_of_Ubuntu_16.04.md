---
title: "Grub Error post install of Ubuntu 16.04"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by mylesh on 2016-09-23
Hello,

I recently decided to install Ubuntu, after playing around with Knoppix. At first I simply wanted to use a Linux distro on a bootable usb, though that changed after I downloaded the Ubuntu iso.

So, right now, I'm stuck on Ubuntu Live from the usb where I downloaded the ISO. Upon starting my PC, I have to hit F12 in order to bring up the boot screen. Selecting the usual hard drive partition which has Windows 7 installed, no longer works. I'm prompted with a Grub Rescue terminal. The only way I can successful boot my PC, is by running Ubuntu off of my usb.

Initially, after selecting to install Ubuntu, I decided to click the option "Install alongside Windows 7" in the installer menu. Things seemed to have been installed fine and, I didn't have any issues. Until I tried to reboot my PC. Following the advice of several Google results, I used Boot-Info to generate [this report]("http://paste2.org/adAUA0sX").

In the report, a few things will be evident, I have two usb drives plugged in. One with the Ubuntu 16.04 ISO on it (Which I'm currently booted into), and another with Knoppix. The internal hard drive, labelled sda1(?) is my Windows 7 installation.

Ideally, I'd like things to be resolved so that I can dual boot, and eventually eliminate my Windows 7 installation once I'm more comfortable with Ubuntu. At this point it should be evident that I'm not an experienced Linux user. Though, I do own a ageing Mac book, so I am familiar with terminal some what. This whole not being able to boot my PC without having this USB drive plugged in is rather an inconvenience, lol. So if you can help, I'd be very appreciative.

-- Additional Comment --
Upon reviewing several Google results, I  found a user that mentioned something about Grub dumping files onto the  USB device rather than into the appropriate boot folder on the new  Ubuntu installation. After reviewing the USB drive and, Windows 7  installation. It appears to me that maybe this is what has happened in my situation. As under the Windows 7 installation, I have a folders at the following path: Windows/Boot/; such as DVD, EFI, Fonts and, PCAT. Which doesn't seem typical, though I've never been into the path on Windows 7 to notice anything different. On the Ubuntu installation, I only have the following files in this path: /boot/grub; gfxblacklist.txt, grubenv, unicode.pf2. I tried copying the files previously mentioned into the latter path, but ran into some permissions issues so I couldn't test it on my own. These files may also be in the Windows 7 path due to Boot-Info repair tool, as I think I did select to add Grub to that partition :/

---

### Post by kc1di on 2016-09-23
First Welecome to Ubuntu, 

you may want to give Boot-Repair a try you can find it here:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Follow the instructions carefully.  It should repair grub for you and allow you to boot.
if not it outputs a file that will help us determine the problem.

---

### Post by mylesh on 2016-09-23
> **kc1di said:**
> First Welecome to Ubuntu, 

you may want to give Boot-Repair a try you can find it here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Follow the instructions carefully.  It should repair grub for you and allow you to boot.
if not it outputs a file that will help us determine the problem.
I'm not trying to sound rude or, anything, but I did include a Boot Repair report in the original post.

---

### Post by kc1di on 2016-09-23
Sorry about that missed it. 

Any way it says that sdb3 has an error.  is sdb you usb stick?  if it is they it's trying to install grub in that drive instead of the sda /master boot record and that will not work.

---

