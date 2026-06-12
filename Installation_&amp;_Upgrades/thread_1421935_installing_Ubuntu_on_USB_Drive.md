---
title: "installing Ubuntu on USB Drive?"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by bds28338 on 2010-03-04
I've been reading up on installing Ubuntu on a USB Drive, but there's so much different documentation that it's kinda confusing me. Had a few questions about it.

I have a 4GB drive that I'll be doing this to. I can install either by booting a LiveCD, or else through Windows 7.

1.) I want a persistent drive (aka, being able to save data and settings)
2.) I don't want the OS itself to be compressed (like on the live CD)

I'm running off the liveCD right now and I was just going to click install and install it directly onto the USB drive... would that work?

---

### Post by earthpigg on 2010-03-04
> **bds28338 said:**
> 
I'm running off the liveCD right now and I was just going to click install and install it directly onto the USB drive... would that work?

yes, but 2 things:

-that method will create a bootable thumb drive that will only work with the hardware on that specific computer.

-towards the end of the partitioning phase, make sure you select "advanced" and specify to install the bootloader specifically onto the thumb drive.

ubuntu has a tool called "usb creator" designed specifically to make a persistent thumb drive that will work on any/all computers. i suggest you give that a try.

---

### Post by mikewhatever on 2010-03-04
> **bds28338 said:**
> 

I'm running off the liveCD right now and I was just going to click install and install it directly onto the USB drive... would that work?

It should, but I'd recommend doing manual partitioning, as 4GB is not a whole lot of space. You should allocate most or all of the space to the system partition, and either make no swap or a very little one, 100MB or so. One other thing to do is to modify the default location GRUB bootloader is installed to, in other words, change it from hd0 to hd1, or whatever that usb drive is.

---

### Post by 2hot6ft2 on 2010-03-04
This was being discussed a little while ago here:
[http://ubuntuforums.org/showthread.php?t=1421878](http://ubuntuforums.org/showthread.php?t=1421878)

But when I tried installing to a 4GB SD card it said it ran out of space during the install.

---

### Post by bds28338 on 2010-03-04
USB Startup Disk Creator under Administration?
can I just slide the slider for "Stored in reserved extra space" all the way over?

it is true that I would like to be able to run this on any computer, so I appreciate the mention of usb creator.

is the OS going to be compressed though? it seems to me that it will only be taking up around 700MB if I use usb creator. Which seems like very little space.

---

### Post by 2hot6ft2 on 2010-03-04
> **bds28338 said:**
> USB Startup Disk Creator under Administration?
can I just slide the slider for "Stored in reserved extra space" all the way over?

it is true that I would like to be able to run this on any computer, so I appreciate the mention of usb creator.

is the OS going to be compressed though? it seems to me that it will only be taking up around 700MB if I use usb creator. Which seems like very little space.
Right and like in the other thread it uses a file to save changes but you will have problems. Check the thread I linked to. I was just telling about my experience doing what you're trying to do.

---

### Post by bds28338 on 2010-03-04
yeah, I'm just being slow at the moment, I hadn't even read anything but the first post. Basically, you make a LiveCD USB Drive and you're going to run into a lot of problems, but if I make a fully installed USB then it's only going to work on the computer I made it on.

---

### Post by 2hot6ft2 on 2010-03-04
> **bds28338 said:**
> yeah, I'm just being slow at the moment, I hadn't even read anything but the first post. Basically, you make a LiveCD USB Drive and you're going to run into a lot of problems, but if I make a fully installed USB then it's only going to work on the computer I made it on.
Either way you'll find there are going to be problems.
9.10 installed to usb for me wouldn't boot with a hard drive in the pc period but 8.10 works fine that way go figure.

9.10 liveusb with persistence updates may cause problems since it can't write to the iso that it puts on the drive and it may not boot. It wouldn't boot for me.

---

### Post by bds28338 on 2010-03-04
now the only way to be able to use the bootable USB Drive on different computers, would be with the Live version right? I'd really just like to be able to drag it around to wherever I happen to be, parent's house, girlfriend's, relatives, whatever, and use it on whatever computer I happen to have access to. Installing Ubuntu onto the flash will not allow this then correct? It will only work on the computer I installed it from.

---

### Post by 2hot6ft2 on 2010-03-04
> **bds28338 said:**
> now the only way to be able to use the bootable USB Drive on different computers, would be with the Live version right?
It would be the way that it "should" work on any computer that can boot from usb provided it's set to in the BIOS.
> **bds28338 said:**
> I'd really just like to be able to drag it around to wherever I happen to be, parent's house, girlfriend's, relatives, whatever, and use it on whatever computer I happen to have access to. Installing Ubuntu onto the flash will not allow this then correct? It will only work on the computer I installed it from.
Me too, and I haven't tried it on any other pc's yet, but since I installed the graphics driver for my pc it may be a problem. I don't know for sure either way at this point.

---

### Post by DZ* on 2010-03-04
> **earthpigg said:**
> that method will create a bootable thumb drive that will only work with the hardware on that specific computer.

Not in my experience. I'm using the same full install (Karmic) on several computers, including a netbook, laptops and desktops.

One may need to get rid of /etc/X11/xorg.conf if it's there.

---

### Post by bds28338 on 2010-03-04
is it true that for the LiveUSB, the largest USB Drive it can utilize is 4GB? or has that changed

would we need to get rid of xorg.conf each time we switched computers? or just once, and how would we go about this

---

### Post by DZ* on 2010-03-04
> **bds28338 said:**
> is it true that for the LiveUSB, the largest USB Drive it can utilize is 4GB?

No I have a 16 Gb flash install and a 320 Gb external WD. Both work fine.

> **bds28338 said:**
> would we need to get rid of xorg.conf each time we switched computers? or just once, and how would we go about this

Just once, and it may not be there in the first place. Just rename it to something from the terminal ```
sudo mv /etc/X11/xorgs.conf /etc/X11/xorgs.conf.backup
```

---

### Post by C.S.Cameron on 2010-03-04
If you don't install restricted drivers the full install drive should work on multiple machines. 
There is also a utility in the repositories named switchconf that allows you to boot different xorg.conf files at start up.
I used to use it to either boot to Nvidia single or duel monitors or to generic machines

---

### Post by tnicewicz on 2010-03-05
Yes, I have done it for my other laptop.

---

### Post by DZ* on 2010-03-05
> **C.S.Cameron said:**
> If you don't install restricted drivers the full install drive should work on multiple machines. 
There is also a utility in the repositories named switchconf that allows you to boot different xorg.conf files at start up.
I used to use it to either boot to Nvidia single or duel monitors or to generic machines

I know you're talking about video drivers. Restricted wireless seem to coexist Ok though. I've activated a broadcom driver on a mini 10v, but when I boot on a laptop with an Intel card, iwlagn driver is used.

---

### Post by DZ* on 2010-03-05
> **bds28338 said:**
> USB Startup Disk Creator under Administration?
can I just slide the slider for "Stored in reserved extra space" all the way over?

it is true that I would like to be able to run this on any computer, so I appreciate the mention of usb creator.

is the OS going to be compressed though? it seems to me that it will only be taking up around 700MB if I use usb creator. Which seems like very little space.

I don't know of any serious drawbacks of just using a full install to a USB. That's how I do it and the installs are fully functional. However, if you've never done this before, be extra careful not to put the bootloader to the hard drive. If in doubt, disconnect the hard drive before you start the installation.

---

### Post by efflandt on 2010-03-05
One advantage of using UUID's for drives is that regular installation to USB should be able to work on any computer that can boot from USB.  I have Ubuntu 64-bit installed on a couple of USB drives, and it works as well on my desktop where it ends up as sdf as on a couple of totally different laptops where it ends up sdb.

And as mentioned even if certain drivers are activated (like Broadcom STA), they are only used when that hardware is found.  So a wireless configuration in Network Connections can work on either a PC with natively supported wireless or a Dell with BCM4311 or BCM4312.

Ubuntu 9.10 does not even use xorg.conf unless you created or added one (or left over from 9.04 to 9.10 upgrade).

However, Linux Mint8 based on Ubuntu 9.10 apparently does not use UUID's by default, so when I did regular install to USB flash as /dev/sdb it would not boot on another computer as /dev/sdf.

The main thing to be aware of for regular installation is to be sure to use **Advanced** button to put grub on the USB mbr.

If you boot on a PC with digitally connected monitor, you may want to disable "splash" boot parameter, because boot may just hang if the resolution in /etc/usplash.conf does not match the native resolution of DVI or HDMI connected monitor (although, removing "splash" on the fly, or a recovery menu entry, should still work).

---

