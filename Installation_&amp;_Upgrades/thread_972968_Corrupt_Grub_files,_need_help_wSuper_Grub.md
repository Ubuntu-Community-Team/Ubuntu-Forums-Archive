---
title: "Corrupt Grub files, need help w/Super Grub"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by Sweet Spot on 2008-11-06
On my last attempted install of Intrepid, everything froze as a partition was on 5% formatting, so I tried again with a different disc. Unfortunately I was getting a "Loading Grub stage 1.5, error 15" message. 

First I tried putting super grub on a usb stick, and got an error saying that there was no partition volume on the drive, so now I'm at the point of where I have Super Grub burned to a disc and it has booted, but I don't know which option to choose. My architecture is 64 bit (if that's relevant) and will be installing 8.04 (8.10 wasn't working well enough for me) and the options are:
> DISTRO
Choose language and help
Choose language and no help
Quick. menu help
GRUB MBR & Linux (1)  AUTO
GRUB MBR & Linux (2) Manual
LINUX ! (1) Auto
LINUX ! (>=2) Manual
WIN 
WIN > MBR and WIN
EASY LIVE SWAP

Pretty obvious that it's not the Win options, but I'm not sure of what the differences are for all the other choices. Thanks for help, I really need my Ubuntu back !

Doug

---

### Post by Matt_D on 2008-11-06
Always start with:

LINUX ! (1) Auto

Without knowing your actual setup it's hard to say with 100% certainty.  

Do you have other distros or versions installed?  If not, and you're trying to install, it should be booting to CD and not using GRUB, so that's a bit confusing.  

I know that LINUX ! (1) Auto will restore the Ubuntu grub menu nicely though if you have a Windows/Ubuntu dual-boot system, or an Ubuntu only system.

---

### Post by Sweet Spot on 2008-11-06
My setup was as such... 

I had 8.10 installed, and chose to reformat my HD with an 8.04 disc, so in the process, I had chosen to delete all partitions and start from scratch.  After creating my three partitions (root, swap and home) it said it was formatting, but hung on 5% for what seemed like forever, and so I had to re-try, but with no luck.  

After hard booting, I kept getting that grub error, and that's where I'm at right now. So, I don't think that there are any partitions set up on the HD, if that matters any. 

Doug

---

### Post by Matt_D on 2008-11-06
seems strange to me, you should be able to boot into the CD without getting the grub error and start a new install.  Check your boot order in BIOS.

---

### Post by Sweet Spot on 2008-11-06
That was the first thing I tried, and kept failing.

---

### Post by Matt_D on 2008-11-06
I'd try using a gparted cd and seeing that will boot.  If so, try and partition your drive first with that, then boot the live cd and see if the install works.  I've had good luck with supergrub, but it that's not working I just don't know (I'm not exaclty an expert, sorry).:confused:

---

### Post by Sweet Spot on 2008-11-06
Wow, this sucks. Any option I choose comes up with :

>  findf /boot/grub/menu.lst/grub/menu.lst/.boot/grub/grub.conf/grub/grub.conf

Error 15: File not found
press any key to continue.... 

I'm then taken back to the main menu


This is very lame. 

Doug

---

### Post by Sweet Spot on 2008-11-06
Downloaded gparted, burned it to disc, inserted.. rebooted and same error. Is my entire system just shot ?!

---

### Post by Sweet Spot on 2008-11-06
I'm starting to think that my DVD drive is at fault. I've tried so many things, and now I've inserted a random 7.10 disc (*which I had tried before) and it is booting, so wish me luck w/the install

edit:so far so good. too bad I chose 7.10 though

---

### Post by Sweet Spot on 2008-11-06
This has to be a hardware issue. 7.10 installed just fine, so I decided to try 8.04  

When I reboot, the DVD drive didn't even spin up, and the BIOS had not detected anything except for the hard drive and the ethernet device. This was happening on and off during my previous attempts, so it has to be that either there is not sufficient power going to the DVD drive, or the drive is simply junk. (and I just bought it).

---

### Post by Matt_D on 2008-11-06
that's almost definitely a hardware issue.  Good news is DVD drives are pretty cheap these days.  I just had my DVD drive go bad, I used a cd-rom from an old pc I had laying around to make sure it was the drive and not the connector.  Worked fine, so I replaced the DVD.  Got an LG lightscribe that records/plays all formats (except blu-ray of course) for $50, you can get it cheaper online I'm sure.

---

