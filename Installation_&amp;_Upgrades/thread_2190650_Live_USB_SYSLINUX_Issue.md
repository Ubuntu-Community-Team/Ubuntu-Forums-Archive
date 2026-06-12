---
title: "Live USB SYSLINUX Issue"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by ftbkingsmc on 2013-11-28
Hello,

I am trying to install Ubuntu 13.10 on my Laptop along side of Windows 7. Just as I did on my Desktop. Unfortunately, when I create the live usb, and select it on boot, it comes up with "SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et al"

I have been researching this for the past hour or 2 and what I found was either a bit too confusing or not my issue. I saw the "Type Help" but I can't do anything when I get to that screen. It just says the SYSLINUX thing and there is a blinking bar.

I have tried the following programs:
[LIST]
[*]UNetBootin
[*]LinuxLive USB Creator
[*]Universal USB Installer (The one that worked on my desktop)
[/LIST]

Any ideas on how I can fix this?

HP 2000 Laptop
32-Bit

Also, when selecting the flash drive, it comes up as "USB Floppy          -SanDisk"

---

### Post by sasha1594 on 2013-11-28
I am not an expert but the method I use works flawlessly,

Since you said you have desktop, boot into linux and in terminal type,

fdisk -l
from the output you will know which is your usb drive

sudo dd if=(absolute path to the *.iso file) of=/dev/sdb(this should be from the output you got earlier) bs=4M; sync

simply said

sudo dd if=~/ubuntu-13.10.iso of=/dev/sdb bs=4M; sync

also please note that you shoul not use sdb1 or sdc1 just the drive and no trailing numbers.

Hope this helps

---

### Post by ftbkingsmc on 2013-11-28
Sorry, I forgot to add that I am on Windows, trying to install Ubuntu 13.10. I don't have access to an Ubuntu PC at the moment.

---

### Post by ubfan1 on 2013-11-29
Did you md5sum hashcheck the downloaded iso file?  There should be Windows md5sum programs available.
 See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.

---

### Post by sudodus on 2013-11-29
Welcome to the Ubuntu Forums ftbkingsmc :-)

There are many tips about USB devices, tools and methods to make USB boot drives in this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sasha1594 on 2013-11-29
Try **LILI (Linux Live USB creator)** in windows , google for it.

---

### Post by ian-weisser on 2013-11-30
> **ftbkingsmc said:**
> Unfortunately, when I create the live usb, and select it on boot, it comes up with "SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et al"

It's supposed to do that. It means syslinux worked.

The boot sequence is pretty simple.
a) BIOS loads syslinux
b) syslinux tells the system where to load the kernel (vmlinuz)
c) syslinux tells the system where to load the Linux system (initrd)
d) The system launches the 'init' program, which starts loading Ubuntu.

The kernel and initrd have lots of error messages if something goes wrong.
If you are not seeing those, then your problem may be earlier in the boot sequence.

Open the USB stick in Windows File Manager.
See the syslinux config file? Open that in Notepad.

Check that the syslinux config file is telling the system to boot from the correct vmlinuz file name.
Check that the syslinux config file is telling the system to use the correct initrd file name.

---

### Post by ftbkingsmc on 2013-11-30
Thanks so much for the help guys! I found a way to get it to work by using the "dd" command in Ubuntu. Thank you sasha1954!

After I did the whole Live USB Creator, I decided I would run the .exe in the usb. "wubi.exe"

After that, I got Ubuntu installed and then I did the dd command. (I did this because I wanted to personalize it beyond what "wubi" did.)

Anyways, everything is sorted out now! Thank you guys very much!

---

