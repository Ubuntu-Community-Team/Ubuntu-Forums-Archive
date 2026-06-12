---
title: "hoping for a quick answer: installing ubuntu from IDE drive"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by kylegio on 2010-09-10
OK heres the issue, im in a panic and need a working operating system.

i have 4 CD drives and they are all messed up, i have one sata cd/dvd drive but the computer cant boot from the sata cd drive for some stupid reason.

what i do have
1) another working computer
2) a copy of the install image
3) an ide hard drive
4) a rubber band
5) 2 popsicle sticks

what i need:
1)macgyver


i have done this with windows before but cant find any documentation on it for linux.
what i want to do is extract the iso to the ide drive, then put that ide drive in the other computer and boot to the ide drive to launch the installer. 

of course the IDE drive is not bootable by just extracting the setup files onto it, is there a way to do this? all normal install paths are closed to me

network install: not compatible
USB stick install: not compatible/no usb stick
CD install: no working/useable cd drive

---

### Post by kylegio on 2010-09-10
just an update: 

i can get to the installer using unetbootin to make the install drive, however the install crashes once it can not locate a CD drive. i dont understand why it should need one, is there a way to specify that it can get the files from the disk itself and not a cd drive?

---

### Post by coffeecat on 2010-09-10
Will the drive that will go in the computer with the messed up CD drives (let's call that computer 1) go into the working computer? That is, if the drive is IDE, does the working computer have an IDE connector, or if SATA, a SATA connector?

If yes, then the answer is easy.

Remove or disconnect the internal drive(s) in the working computer so that they don't interfere or complicate things. Connect the HD from computer 1 into it. Boot up with the install CD in the working computer. Install Ubuntu in the normal way to the HD that belongs in computer 1 but is now a temporary internal drive in the working computer. Remove HD and put back in computer 1. (You can reconnect the original drives in the working computer now.) Now boot up computer 1.

You don't have to do anything more sophisticated than that. So long as you don't install any proprietary video drivers while the HD is still in the 'working computer' it will boot up just fine once it's put back in computer 1.

---

### Post by kylegio on 2010-09-10
solved

used unetbootin to make a installer on a crappy 2gig IDE hard drive, put that in the other computer and booted, installer wouldnt continue without a cd drive, but at this point i was able to install my sata cd/dvd drive that my motherboard couldnt use as a boot drive.

---

### Post by kylegio on 2010-09-10
> **coffeecat said:**
> Will the drive that will go in the computer with the messed up CD drives (let's call that computer 1) go into the working computer? That is, if the drive is IDE, does the working computer have an IDE connector, or if SATA, a SATA connector?

If yes, then the answer is easy.

Remove or disconnect the internal drive(s) in the working computer so that they don't interfere or complicate things. Connect the HD from computer 1 into it. Boot up with the install CD in the working computer. Install Ubuntu in the normal way to the HD that belongs in computer 1 but is now a temporary internal drive in the working computer. Remove HD and put back in computer 1. (You can reconnect the original drives in the working computer now.) Now boot up computer 1.

You don't have to do anything more sophisticated than that. So long as you don't install any proprietary video drivers while the HD is still in the 'working computer' it will boot up just fine once it's put back in computer 1.


will it work that way if they are completely different architecture? the working one is AMD 64bit brand new, the other one is intel P4 at best, maybe 5 years old?

---

### Post by coffeecat on 2010-09-10
> **kylegio said:**
> will it work that way if they are completely different architecture? the working one is AMD 64bit brand new, the other one is intel P4 at best, maybe 5 years old?

Yes, absolutely. Don't forget that Linux probes for hardware during the bootup process. The only things that might cause problems are proprietary video drivers (where a xorg.conf has been created) and possibly sound which will just need re-configuring. 

However, the one limitation in your instance is that you must use a 32-bit installer. But since you would have been installing on the AMD64 to use in the P4, that wouldn't have been a problem, since you need 32-bit for the P4 and AMD64 CPUs run happily on 32-bit systems.

3-4 years ago, when I was fairly new to Linux, I installed a (32-bit) version of Foresight Linux to an AMD64 machine with a VIA chipset motherboard. I then took the HD out and put it in a Celeron (cheapo P4) machine with Intel motherboard. It booted up with nary a peep and everything just worked. Being used to Windows I was impressed! :)

---

### Post by kylegio on 2010-09-10
thats good to know, i use linux pretty much exclusively but i dont know enough about the boot process to assume that it would work where 9x out of 10 with windows it wouldnt work, another point for linux.

i was also hesitant to try that because im using a raid card and wasnt sure it would play nicely moving the raid over to a new setup after installing. didnt want to go through the effort to have it all wasted. 

either way it worked out and i thank you for your reply

---

### Post by coffeecat on 2010-09-11
> **kylegio said:**
> where 9x out of 10 with windows it wouldnt work, another point for linux.

I think you could say 11x out of 10 for Windows! :) I think the problem with Windows is two-fold. First, its odd way of dealing with drivers. You just have to plug a different mouse in and it goes 'ding-dong - new hardware found' and seems to go into a breathless panic for a few moments. Just imagine what it would do when confronted with a whole motherboard of different components. More importantly is its inbuilt anti-piracy measures. It keeps some sort of tally of hardware and keeps a score of hardware changes. If the score gets too high you have to re-activate it, and if the score gets impossibly high it simply refuses to work, assuming that it's been illegally cloned to another machine.

> **kylegio said:**
> i was also hesitant to try that because im using a raid card and wasnt sure it would play nicely moving the raid over to a new setup after installing.

Tbh I have no experience of RAID so I don't know whether that would have been a problem. With a movable RAID card I would think not though. 

Good luck!

---

