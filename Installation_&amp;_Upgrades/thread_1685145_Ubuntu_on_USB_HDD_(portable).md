---
title: "Ubuntu on USB HDD (portable)"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by ian_hawdon on 2011-02-10
Hi, sorry if this has been answered before, I just haven't been able to find it!

I'm wondering how I'd go about installing Ubuntu on an external Hard Drive for use in many machines.

I've been using an Ubuntu Live USB with a casper-rw partition for a while, but I've been finding it hard to keep it from filling the drive up to 100% (some of the software I use isn't exactly light-weight!)

I was wondering how I'd do the same sort of thing on a USB hard drive?

Do I: Install Ubuntu onto the drive as I would if it was internal?

Or

Install Ubuntu on the drive the same way I'd install it onto a USB stick (i.e. with a hudge Casper-RW and Home-RW partition)

The feature of being able to probe for hardware on boot (like the Live CD) is the feature I'm looking for.

Cheers

---

### Post by P4man on 2011-02-10
Just do a regular install on the USB drive. LiveCD isnt different from a regular install when it comes to probing hardhare, as long as you dont use proprietary videodrivers, you can boot a linux install on pretty much any PC. One of the big differences with a livecd is the compression (slow boot) and read only root file system. You probably dont want either.

Just make sure you install grub on the USB drive rather than the internal one, if you want to be able to boot the drive on different machines. And then configure your bios to boot from USB first.

---

### Post by oldfred on 2011-02-10
+1 P4man's suggestions.

A good example with pictures:
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

I suggest partitioning in advance and using manual install so you will get the combo box on which drive to install grub2.

---

### Post by C.S.Cameron on 2011-02-10
It is best to disable your internal HDD before installing to the external drive. 
If you can not disable it, use manual partitioning and be sure to put grub on the external drive.
You might want to make the first partition NTFS so Windows can see the external drive.

---

### Post by ian_hawdon on 2011-02-10
just a few questions:

How will it handle network cards? I've had issues when moving an internal drive from one machine to another, and I had to edit a config file to make the system forget the old MAC address. That might only have applied to the server edition though.

Secondly, how well does it handle system updates? I know system updates shouldn't be done on a live USB, but on a fully installed USB HDD I can see issue when it comes to Kernel updates, and GRUB... or does the system know to update grub on the USB drive, rather than /dev/sda?

Cheers

---

### Post by P4man on 2011-02-10
> **ian_hawdon said:**
> just a few questions:

How will it handle network cards? I've had issues when moving an internal drive from one machine to another, and I had to edit a config file to make the system forget the old MAC address. That might only have applied to the server edition though.

Shouldnt be a problem, at least i never encountered it with desktop installs.

> Secondly, how well does it handle system updates? I know system updates shouldn't be done on a live USB, but on a fully installed USB HDD I can see issue when it comes to Kernel updates, and GRUB... or does the system know to update grub on the USB drive, rather than /dev/sda?


Again, not a problem. Grub has two parts, a tiny bootloader (stage 1) which sits on the master boot record of your boot drive. Its 512 byte (or a bit less). It points to the harddrive and partition where the rest of grub can be found, and that is usually in /boot/grub on your linux drive. That is also where your kernels reside. And those are the ones that will be upgraded. Just make sure you put grub on your USB drive (that is, the MBR). You can configure that in "advanced" I think, one of the last steps of the installation, or you can do as someone above suggested, simply disconnect/disable all other drives before installing, then you cant go wrong and grub will be installed on the USB drive for sure.

---

### Post by oldfred on 2011-02-10
It used be be an issue as it new drive by sda, sdb etc, but now has more detailed drive info. If correctly installed initially then it should be ok. If not and you reinstall grub to repair it then you may need to run this to reset it.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by ian_hawdon on 2011-02-11
Cheers, I just remember Grub being a pain sometimes, but from what you say, it seems to be a much more stable beast now.

Right, guess it's time to acquire a hard drive and give it a shot :-)

---

### Post by ian_hawdon on 2011-02-16
Ok, so it will boot fine from one machine, but some machines fail to see the hard drive at all (probably a BIOS issue) and some just get stuck at grub with an "Unknown File System" error... 

Interestingly, it's the machine I installed it on that comes up with that last error, even if it's the only drive on the system!

The one system that it DOES boot on, needs a driver for the Wifi card to get online, which is, annoying, online! (the good ol' "The drivers for you modem can be found at www.modem-driver-site-which-is-no-good-as-youre-offline.com" joke)

Any suggestions on getting round this grub issue?

---

### Post by P4man on 2011-02-16
What version of ubuntu (and grub) are you using? 
Can you download and run bootinfoscript:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by ian_hawdon on 2011-02-16
Ubuntu 10.10

I reformatted the drive and out the /boot partition at the beginning of the drive. Sadly, the installer crashed when installing this way (I tried twice).. it crashed near the end, so I ended up reinstalling GRUB manually, by mounting the drives and chrooting into the USB Hard Drive.

Now it'll boot on the machine I installed it on, but when I took it to another machine off site, selecting Ubuntu from Grub just causes it to reboot. Failsafe mode just hangs.

I can mount the drives from my Ubuntu USB Live Disk... so, where do I go from here?

---

### Post by P4man on 2011-02-16
Hmmm. The installer really ought not to crash, thats a first big red flag that something is wrong. The fact some machines apparently fail to detect the drive at all, is another one. 

Wild guess; this is a USB powered external drive, with no power supply?

---

### Post by ian_hawdon on 2011-02-16
Power seems to be fine, my USB 3.0 interface card has a molex connector plugged into it, so I can't see how power would be an issue.

It installed fine when I used just one partition at the end of the drive, but then I read that some BIOS's wont boot if the boot files are further than 128GB into the drive (I don't understand that either, as GRUB2 Is in the MBR regardless)

But when there's a /boot partition at the beginning of the drive, the installation seems to fail at the same point (Looking for software to remove.. or something like that, sorry, this is from memory)

---

### Post by P4man on 2011-02-16
> **ian_hawdon said:**
> Power seems to be fine, my USB 3.0 interface card has a molex connector plugged into it, so I can't see how power would be an issue.

I take it my guess was correct then? Having a powered USB controller doesnt mean a lot, especially if the drive is pulling all the power from a single USB plug. I dont remember what those are rated for, but its barely enough for a slow 4200 rpm laptop drive. Having owned such a drive once, I learned my lesson: external harddrives really need their own powersupply. Anything else is just asking for trouble.

Now, Im not saying that explains the installer crashing, but I would suspect it plays a big role in the machines not even detecting the drive, and generally I would avoid using such drives as the plague.

> It installed fine when I used just one partition at the end of the drive, but then I read that some BIOS's wont boot if the boot files are further than 128GB into the drive (I don't understand that either, as GRUB2 Is in the MBR regardless)

I suspect that is for grub1, and it wouldnt relate to where the files are, but where the partition starts. If you dont create a /boot partition, you should always be okay.

> But when there's a /boot partition at the beginning of the drive, the installation seems to fail at the same point (Looking for software to remove.. or something like that, sorry, this is from memory)

Well, Id rather see the install finish successfully before experimenting with anything else. Perhaps you can try installing without a separate /boot partition?

---

### Post by ian_hawdon on 2011-02-16
> **P4man said:**
> I take it my guess was correct then? Having a powered USB controller doesnt mean a lot, especially if the drive is pulling all the power from a single USB plug. I dont remember what those are rated for, but its barely enough for a slow 4200 rpm laptop drive. Having owned such a drive once, I learned my lesson: external harddrives really need their own powersupply. Anything else is just asking for trouble.

My drive has a DC input on it too, but the cable that came with it, has a USB plug on it. Guessing that plugging that into the other port isn't going to increase the power much, if at all!

> Now, Im not saying that explains the installer crashing, but I would suspect it plays a big role in the machines not even detecting the drive, and generally I would avoid using such drives as the plague.



I suspect that is for grub1, and it wouldnt relate to where the files are, but where the partition starts. If you dont create a /boot partition, you should always be okay.

Yeah, what I meant before is, that my boot files (not in their own partition) were in a partition at the end of the drive, some machines could boot this, others couldn't. The accepted solution I could find, by using google, was to make sure the boot files were on a partition near the beginning of the disk. I think they were referring to Grub 2


> Well, Id rather see the install finish successfully before experimenting with anything else. Perhaps you can try installing without a separate /boot partition?

I'll give that a shot tonight.

---

### Post by P4man on 2011-02-16
> **ian_hawdon said:**
> My drive has a DC input on it too, but the cable that came with it, has a USB plug on it. Guessing that plugging that into the other port isn't going to increase the power much, if at all!

I strongly suspect it does (assuming the drive isnt expecting 12V from a transfo that just uses USB connector). Each USB port has its own max powerdraw: 500mA for USB2, twice that I think for USB3.  Drawing from 2 USB ports really does double the power when you are using a powered hub or controller that can deliver more than 1A, not all controllers can. 

My drive had a Y cable with 2 USB connectors and I needed to connect both, for that very reason. But even that is often not enough, especially not on a laptop with a crappy USB controller.

> I'll give that a shot tonight.

Let us know.

---

### Post by ian_hawdon on 2011-02-16
Ok, just for the crack, I decided to plug in the drive into my laptop. It Kernel Paniced on boot (flashing Caps Lock), maybe different machines act differently when there's a kernel panic, I don't know.

Anywho, I was able to go failsafe on this one, and rebuilt the grub config again. Also, I checked the fstab and noticed there was an entry for /dev/fd0. Yes, there is a floppy drive on the machine I installed the copy of Ubuntu on. But I removed the entry just in case. Now it boots fine on my laptop.

Would having an entry in the fstab for a floppy drive cause problems on machines that don't have one? I'd have just assumed it would have thrown an error, rather than causing a kernel panic...:confused:

---

