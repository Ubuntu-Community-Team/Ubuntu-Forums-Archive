---
title: "Neither live CD or alternate CD will boot"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by rsambuca on 2006-09-19
Hi all,

Never tried linux before, but decided to give ubuntu a go...

Specs:

MSI RS482M4 motherboard s939
AMD64 3500+ CPU
1 GIG RAM (2x512)
Asus 6600GT 128MB PCIe video
lite-on 48X CD/DVD burner
Sapphire theatrix 550 pro TV Tuner
233 GB IDE hard drive
6GB IDE hard drive set as slave

I have tried the ubuntu live CD for AMD64, and it hangs at the "mounting root files" stage, which appears to be a common problem.  After some reading, I tried disconnecting my USB devices and still no go.

Thought I would try installing ubuntu onto an old 6GB HD which I installed, so I can dual boot.  Tried the alternate CD, but it gets to a stage where I believe it said detecting hardware, then the screens go blue and freeze.  (Kinda funny, as I have never had the blue screen of death with XP, but I get one trying to install linux!)

Anyways, from what I can tell, the ATI theater pro 550 is not compatible with linux - will I have to remove it to install linux?  Any other potential compatibility issues?  I have tried different CD burning speeds and am tired of making coasters.

Any help would be appreciated.

rsambuca

---

### Post by zxee on 2006-09-19
Have you checked the md5sums of the iso image before burning?
I just ask because of your line about coasters.
You may need to use different boot options but I don't know for sure which ones work in ubuntu-I've used knoppix cheatcodes to get past some obstacles in exotic hardware. [http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt](http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt)
No one here seems to have an answer for using different boot parameters-is that correct? The pcie card/slot might be a source of trouble.

---

### Post by wpshooter on 2006-09-19
I don't know about the AMD64 but I have seen many suggestions on these forums advising to try the 32 bit version instead.

If I were you, I would consider investing in some good name brand CD-RW media.  That's all I use.  If it does not work then just erase it and try again and again and again.

Good luck.

---

### Post by rsambuca on 2006-09-19
Thanks for the suggestions guys.  Before I start altering the boot parameters (which I know virtually nothing about), I'll probably try a 32 bit version first.  Is there much of a difference between the 32 bit and 64 bit?

---

### Post by zxee on 2006-09-20
> **rsambuca said:**
> Thanks for the suggestions guys.  Before I start altering the boot parameters (which I know virtually nothing about), I'll probably try a 32 bit version first.  Is there much of a difference between the 32 bit and 64 bit?

Since the 64 bit version is optimized for that processor it should be faster but how much of a speed hit the 32 bit version takes is a subjective thing. 
I would recommned the alternative cd of the 32 bit version also as it gives you more options. Good luck and let the thread know how you make out.

---

### Post by N!zzo on 2006-09-20
If you have windows on your pc, you can try doing an online install.

I had the same problem installing with cd.

heres a link, but not sure if it installs dapper or a 64bit version
(if you do this right click linux.bin link and save as 'linux' in the instructions)
[http://ubuntuforums.org/showthread.php?t=28948]("http://ubuntuforums.org/showthread.php?t=28948")

---

### Post by rsambuca on 2006-09-21
I did a little more homework and after reading through many (MANY) websites, I simply tried adding:

ide=nodma

to the boot options.  Everything worked pretty quickly this time.  Took a couple of minutes to do its stuff and I am now running the 64bit version of Ubuntu off of the live CD.

To be honest, it really bothers me to enter stuff like this to the boot options when I don't know what it is doing.  Can someone please tell me what ide=nodma actually does?

---

### Post by N!zzo on 2006-09-21
I think *ide=nodma* turns off Direct Memory Access off your optical drive, you might need to turn that back on if you plan to burn disks fast

heres a link
[http://ubuntuguide.org/wiki/Dapper#How_to_speed_up_CD.2FDVD-ROM]("http://ubuntuguide.org/wiki/Dapper#How_to_speed_up_CD.2FDVD-ROM")

---

### Post by PointSource on 2007-01-29
From what I've seen compaq computers don't like having DMA on their optical drives (as well).

---

