---
title: "Can't boot ubuntu on dell 15z laptop - dual install with Windows 8 in UEFI"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by austinap on 2013-05-28
Hi all, 

I'm trying to dual install ubuntu 12.04 (or 13.04) along side windows 8 on a new Dell 15z laptop (this one: [http://www.dell.com/us/p/inspiron-15z-5523/pd](http://www.dell.com/us/p/inspiron-15z-5523/pd)) but am having difficulties.  I can boot from USB and install 12.04 after switching bios to UEFI mode with secure mode off.  However, when I restart everything is wonky.  If I then boot from usb again into ubuntu and run boot-repair, I can get to GRUB2 in UEFI mode.  I can boot into Windows from the grub options, but everything goes to **** if I try to boot into ubuntu.  

If I try to boot from UEFI mode, I get a flash of the command line printing ramdisk before going black and stalling.  If I boot in legacy mode with recovery mode, I get the same thing followed by a stream of text, and eventually I get to screen giving me options to boot to root / failsafe graphics mode / etc.  If I boot to failsafe graphics, I get a prompt saying that it is going to restart the graphics, and then a blank screen.  I don't know where to go from here.  The only way I seem to be able to boot into ubuntu is from the usb.  I tried wading my way through the sticky at the top as it seems like it might be relevant, but I couldn't really get past step 2.  Any help would be greatly appreciated, otherwise I'm on the verge of having this as a windows only machine.

Edit: I should add that I also tried installing 13.04 initially, with similar problems.  I could get grub loaded, but every time I tried to boot ubuntu from the disk it stalled at "Loading initial ramdisk".

---

### Post by ubfan1 on 2013-05-28
You are using the 64 bit versions of Ubuntu 12.04.2 or Ubuntu 13.04, right?  32 bit versions are not set up with secure boot in mind, which is what you probably need to boot Windows (unless you are one of the fortunate ones whose new pc still boots Windows 8 with secure boot disabled).  You did turn secure boot back on I'm guessing to boot windows, so boot-repair should have fixed up most other things, but it cannot fix a 32 bit kernel.

---

### Post by austinap on 2013-05-28
Both versions I've tried installing (13.04 and 12.04) have been the 64 bit versions.  I have also turned secure boot off, and can boot into windows with secure boot off as well.  I've turned off quick boot (or whatever it's called) in win 8.

---

### Post by austinap on 2013-05-29
Bump.  Any ideas?

---

