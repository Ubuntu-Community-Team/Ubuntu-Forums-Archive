---
title: "Frustrated with installing Ubuntu on an Asus x75a laptop"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by John_Mamish on 2013-08-20
Hi Ubuntu Forums,

With the new UEFI interface starting to replace BIOS, I'm sure my question has been asked before (and believe me, I've looked), but all the other solutions haven't worked for me.

I recently got a new laptop after my old Dell (which I was using Ubuntu on) broke.  After trying to install 12.04 LTS from a live USB created with Linux Live usb creator, I'm at my wits end and tempted to give up.  My new laptop is an ASUS x75a with Windows 8 preinstalled and a UEFI firmware interface with no option to use BIOS.  The ethernet controller is an Atheros AR8161.  I need to dual-boot and keep windows (for now).
 
I successfully managed to boot off of the live USB, at which point, a menu (unlike GRUB) came up asking if I wanted to install Ubuntu, try Ubuntu, etc...  I installed Ubuntu, selecting the option to install alongside Windows 8.  Everything seemed great, until I rebooted.  The GRUB menu never came up and I was sent straight to windows.  At that point, I tried following the guide posted [here]("https://help.ubuntu.com/community/UEFI"), but when I boot using the "Try Ubuntu" option, I don't get an internet connection which I can use to install boot-repair.  (I have tried wireless AND hardwired.  Both work on Windows, but the drivers are missing on Ubuntu).  Trying to fix the networking was very frustrating.  I tried downloading a .deb package with the Ethernet drivers on another computer and transferring it to the Ubuntu computer, but running dpkg -i <package name> ended in a missing dependency message
```

dependency problems prevent configuration of linux-backports-modules-cw-3.6-3.2.0-33-generic:
linux-backports-modules-cw-3.6-3.2.0-33-generic depends on linux-image-3.2.0-33-generic; however:
Package linux-image-3.2.0-33-generic is not installed.

```

Downloading the boot-repair ISO and transferring it to the system in question with a usb drive resulted in a message saying that the 9660 format wasn't supported, which I also couldn't resolve.

I want to resolve my booting issue before I try to resolve my networking issue.  I would appreciate it if someone could help me get grub running so I wont have to boot from USB every time.


Sorry this post is a bit of a mess.  I found other posts that addressed similar problems, but they all either didn't apply to me or needed an internet connection to work.

Thanks for your help,
John

---

