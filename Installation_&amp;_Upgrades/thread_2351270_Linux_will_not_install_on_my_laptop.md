---
title: "Linux will not install on my laptop"
date: 2017-02-01
forum: Installation &amp; Upgrades
---

### Post by kristinareynolds on 2017-02-01
My brother has a Compaq Presario CQ57 laptop.  It had Windows 7 installed, but for some reason the computer stopped booting into the operating system.  He was about to get rid of the computer and buy a new one, so I recommended to give Linux a try first.  


We have tried a few different types of Linux and none of them will even load into the live session.  This problem is happening with Ubuntu, Xubuntu, Elementary OS, Linux Mint, and even Puppy Linux.  We have tried both live CDs and live USBs, and checked to see that they work on another laptop.  All of the live disks will boot up, but then there's a crash before we ever reach the desktop. At this point I'm wondering if there might be some kind of hardware problem.  I did a memory check in the BIOS and it said that it passed.  I have never had a hard time installing Linux on a computer before, so I am very confused what might be causing this.  


Here is a picture of the error message I get when trying to install Ubuntu 16.10.  [http://imgur.com/a/juj04](http://imgur.com/a/juj04) 


We get a similar message with Linux Mint and Elementary OS.  Puppy Linux gives a message about restarting X.  


Thanks for any thoughts.  I would love to get this computer working again.

---

### Post by TheFu on 2017-02-01
What CPU?  Compaq - that's like 15 yrs old, right?  Most 32-bit Linux distros require an i686 compatible or higher CPU.  Almost any cheap chromebook would be at least 2x faster, some could be 10x faster.

Try TinyCore - I think that is the last of the i386 distros left.  There's also the mini-installer for Ubuntu, but that doesn't have a GUI. You'll need to select the networking and any GUI manually, methinks.  I've only used the mini-install for servers.

---

### Post by kristinareynolds on 2017-02-01
It came pre-installed with Windows 7.  Here are some of the system specs.  I would think that the computer should be able to handle Ubuntu.  

**CPU:**  AMD E-300 1.3 GHz (Dual Core)
**RAM:**  2 GB DDR3 SDRAM
**Graphics: ** ATI Mobility Radeon HD 6310

I used the 64 bit AMD version of Ubuntu.

---

### Post by Bucky Ball on 2017-02-02
> **TheFu said:**
> What CPU?  Compaq - that's like 15 yrs old, right?

That CPU release date = 08/22/2011. ;)

You could try [the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") and see if you can boot with that. Your problem might be a graphics one and the mini uses a text-based installer so you might be able to get installed and then build it up from there and see when it breaks. You'll also have a better chance of fixing graphics drivers if you can get an install. 

It is odd, though, because I don't see any reason Xubuntu or Lubuntu wouldn't run on that so it is a problem with the install. My guess is a graphics one, but don't quote me (as [according to this page]("https://help.ubuntu.com/community/RadeonDriver") that card works fine with 16.04).

Have you wiped Windows 7 from the drive or it is still there? You haven't got that in hibernation mode or installed in UEFI or another oddity? Can you boot to Windows or not? If not, you could try taking the drive out of the machine, putting in a docking bay connected to another computer, wipe it there, back in Compaq and try again.

Just a thought. ;)

---

### Post by gdesilva on 2017-02-02
> **TheFu said:**
> What CPU?  Compaq - that's like 15 yrs old, right?  Most 32-bit Linux distros require an i686 compatible or higher CPU.  Almost any cheap chromebook would be at least 2x faster, some could be 10x faster.


The CPU supports 64bit OSs. See [here]("http://www.cpu-world.com/CPUs/Bobcat/AMD-E%20Series%20E-300.html") so any 64bit OS should work.

Given even Puppy Linux installation failed, I suspect it might be an issue with the DVD Drive not reading the media correctly? Try LiveUSB to see whether you will have any luck.

---

### Post by Bucky Ball on 2017-02-02
> **gdesilva said:**
> Try LiveUSB to see whether you will have any luck.

And right there in the OP's first post. 

> **kristinareynolds said:**
> We have tried both live CDs and live USBs

Been there, done that. :)

---

### Post by TheFu on 2017-02-02
My reasoning for 15 yrs old is that HP bought Compaq in 2001. ;)  Appears they kept using the name until 2013 on "low end computers."

I have an AMD E-350 on a microITX MB. Used it as an XBMC machine before HiDef video made that impossible. The E300 is in the same family, just about 15% slower. Both are 64-bit APUs with onboard GPUs. If I get a chance, I'll try to boot a 16.04 lubuntu today. It will be a flash boot - no optical drive. It will take a little setup to make this happen. My machine was $99 - $50 for the case and $50 for the MB+APU.  I added some left over RAM and a HDD. Ran it for about 3 yrs before it couldn't playback the hidef media I wanted and was replaced by a $50 Rasperry Pi v2.

My test isn't the same as the OPs, but at least we'll know if the CPU/APU/GPU work with a newer Ubuntu version. I expect it will work, which won't really help the OP. Laptops tend to get bounced around and some connections can get loose over time.

---

