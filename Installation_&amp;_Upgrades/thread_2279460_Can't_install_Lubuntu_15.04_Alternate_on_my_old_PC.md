---
title: "Can't install Lubuntu 15.04 Alternate on my old PC"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by madden.playss on 2015-05-23
Hello. I'm trying to install copy of Lubuntu 15.04 on my old PC using USB method. Everything boots up, I configure language, keyboard layout and other settings and then the installation starts. But the problem is, that when the second dialog appears (Checking CD-ROM, I think), it makes a quick test, and after that, there's nothing happening. It just won't continue installation.
At first, I thought that it is USB's fault, but successfully installed Lubuntu on my netbook using the same USB.

Also, my old PC specs:

Pentium 4 - 3.00GHz
3GB of RAM
1TB hard drive
Nvidia Geforce FX 5600
Ethernet connection

---

### Post by mattharris4 on 2015-05-23
I am running Xubuntu 14.04 LTS right now (and have run Edubuntu in the past) on a computer with that same processor, 3.25GB RAM, a 500GB HDD and it is connected to the intenet using an ethernet card.  We can eliminate those as the issues (assuming they aren't defective) right now from my personal experience.  However, you have an Nvidia graphics card.  Nvidia support is dodgy at best especially on that era equipment.  Can you try the integrated graphics in the CPU rather than using the Nvidia card and see if you can complete the install using that (there should be two VGA ports on your computer because of the added Nvidia card, use the other port)?

It is theoretically possible (although not that likely) that Canonical has eliminated Pentium 4 support from the later version.  If bypassing the Nvidia card doesn't work, I would try installing Lubuntu 14.04 on the computer and see if it works.  You really should be using an LTS version anyway and the current LTS version is 14.04.  With a non-LTS version you would need to update to the next version every six months, with version 14.04 LTS you have security support until 2019.  I would also install 14.04 on the netbook for the same reason.

---

### Post by Vladlenin5000 on 2015-05-23
> **mattharris4 said:**
> Can you try the integrated graphics in the CPU rather than using the Nvidia card and see if you can complete the install using that (there should be two VGA ports on your computer because of the added Nvidia card, use the other port)?

P4s didn't have any GPU on die; there could be an (Intel??) integrated graphics in the motherboard, not the CPU. Many motherboards of that time didn't have it either.
*If* it has [and integrated graphics] then it's a good troubleshooting suggestion, just in case. However, I suspect the problem is somewhere else, considering the installation is being done with the _alternative_ installer, hence basic VESA graphics = nothing that could possibly be affected by the presence or absence of a nvidia card, irrespective of how dodgy the support is (it isn't).

---

### Post by mörgæs on 2015-05-24
> **madden.playss said:**
> ...there's nothing happening.

For how long did you wait?

---

### Post by sudodus on 2015-05-24
Lubuntu 15.04 works in my Dell with a Pentium 4 processor. I think you have problems with the graphics (or you did not wait long enough, as indicated by mörgæs). Please try the [boot option]("https://help.ubuntu.com/community/BootOptions") **nomodeset**.

---

### Post by mattharris4 on 2015-05-24
^  Sudodus, if you are running the 3.0GHz version like the OP and I both are  that rules out lack of support (but I am running 14.04 which is an older OS version so I could not say for sure regarding support in OS 15.04).  I sort of thought that was not likely as computer makers were still installing that CPU new on computers made in 2006-2007, IMO that would be too soon to not support it in an OS (manufacture of this CPU started in 2002-2003, it was the first hyper-threaded or dual-core CPU from Intel according to a Consumer Reports magazine of that era).  I didn't want to completely rule out loss of support until I knew someone else was not having that issue with the same CPU, though.  

I obviously suspect the Nvidia card.  Nvidia's support for Linux in the 2000's was so poor that Linus Torvalds (the creator and maintainer of the Linux kernel) told Nvidia "f**k you" and extending his middle finger while lecturing to a college computer science class, video of this is posted on YouTube.  If I were the OP I would attempt to find another brand graphics card (assuming there isn't integrated graphics as an option) that is compatible with both the computer and Linux if this is a desktop computer.  If it is a laptop the OP may as well replace the computer, it is extremely difficult for the average Linux user to tear down, replace a part and reassemble a laptop and this era computer isn't worth someone spending $100 plus to replace a graphics card on a laptop computer that is 8-12 years old if that is even still an option.

I do have some more questions, these are actually about the netbook.  How well is Lubuntu running on it?  Is the OS relatively smooth on it (there aren't too many pauses before a page will scroll, the bookmarks list will move for you, pages will load from bookmark without a long pause, etc.)?  Also, what are the model and specs of that netbook?  I ask because the first mass-produced netbooks (from about 2007-2010) were underpowered messes that many times were very aggravating to attempt to use with a modern OS, they were made for a special version of Win XP which would run on 128MB RAM and a Pentium 2-level performing CPU, for comparison in my experience Lubuntu 14.04 requires 750MB-1GB of RAM for many websites and for some it requires 1.25GB RAM to run properly, I know it will run on an AMD E1-2100 which is about equal to a Celeron from 2010 or a recent Intel Atom according to Passmark, all three score in the 600's, I suspect that it would run on a Pentium 4 3.0 GHz (which Passmarks at 358) reasonably well with some light pausing and glitching on CPU intensive websites as I can personally say that Xubuntu does, Xubuntu runs on very slightly higher specs than Lubuntu IME.

---

### Post by mörgæs on 2015-05-24
There is no reason to suspect lack of support for the Pentium 4 processor nor the graphics card. The latter might need the nomodeset option as mentioned above but that's all.

The middle finger appeared much later in history than the FX 5600 which had and has fine support. It was pointed at a unrelated series of graphics cards. 

Let's not scare original poster nor other people who might find the thread. Your hardware is most likely fine (except possibly the CD drive but we don't know that yet). Don't go buy anything.

---

### Post by mattharris4 on 2015-05-25
Apologies, Morgaes.  With so many Nvidia cards not having good support in Linux and the OP having tried a USB install already (ruling out the CD drive being defective as the issue) that is what I zeroed in on as a possible solution.  This is quickly becoming something that I cannot assist with knowledgeably but I do have a few suggestions (I know Morgaes thinks the hardware is fine but since the HD and RAM haven't been ruled out I think it is appropriate, my explanation of this is below).  Is it possible to do a live boot off of the USB (you may need the full version and not the alternate installer for this) and run Lubuntu's RAM tester for you?  Here is a link to instructions:  [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest) .  If that doesn't show any problems, run the hard disk analyzer in Lubuntu ( [http://neanderslob.com/2013/10/06/how-to-check-the-health-of-ones-hard-disk-a-step-by-step-pictoral-tutorial/](http://neanderslob.com/2013/10/06/how-to-check-the-health-of-ones-hard-disk-a-step-by-step-pictoral-tutorial/) ).  The way to get to the terminal will be different but once you are in the terminal the instructions are the same.  If this isn't possible with the USB try downloading the ISO of the alternate installer to a CD-R (the full version will not fit) -- if it works  you know the USB controller is likely at fault.  You evidently don't have a DVD drive so that isn't an option (if you do  download the full version to a DVD-R on another computer and attempt an install off of  that).  If you cannot get a live session up with a USB or a CD-R/DVD-R obviously you cannot use Lubuntu to test your RAM and HD.

I don't see where this is a USB stick issue, you actually used it successfully to install on another computer.  This computer is too old to have UEFI in it so that isn't the issue.  Morgaes has confirmed that the Nvidia card you have is supported in Lubuntu (and the other Canonical OSes).  You are getting into the installer so it isn't a boot order issue.  If you cannot get a live session to work off of the USB I suppose the USB controller could be flaky and only working part time but if that were the case it would likely not stop in the same place every time, you need a computer tech with the proper equipment to test this for certain.  However, if the USB controller works properly (you would likely rule that out if the CD-R or DVD-R does not work either, that is the best you can do for free) and you still cannot get it to install after the above steps you could also try a non-Canonical OS to see if it is something in Canonical's code that isn't compatible with something in your computer (not likely but at this point we are grasping at straws without a computer tech and his equipment available for free) -- I would try Puppy Linux, you would use UNetbootin to make the USB; if you can run and install another organization's Linux OS that can run with your computer hardware and you have tested the RAM and HD (Puppy is small enough that it might work with semi-defective RAM and HD) we know that Canonical's code is not working with something in the computer.  Ruling out these things tells me that it is indeed a hardware issue (anywhere from a blown capacitor to a CPU about to completely fail) and you need a computer tech to hook up their testing equipment to the computer to figure out what is wrong, you will have to decide if it is worth the cash to have it done (with this old of a computer it likely isn't).

Good luck and I hope a solution short of buying another computer and/or expensive diagnostics/repairs can be found.

---

### Post by v3.xx on 2015-05-25
> Good luck and I hope a solution short of buying another computer and/or expensive diagnostics/repairs can be found.
Thats why were here, we work for beans :D
> I would try Puppy Linux
Recommend Puppy?  Is Puppy going to have better drivers?

Nomodeset is a very good bet.  Are you familiar with it?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mattharris4 on 2015-05-26
V3, Puppy claims to support almost any computer pre-UEFI with the 4.3 version (I know for sure it is 4.something).  Furthermore I suggested that as a last-resort to see if maybe it is a problem in Canonical's code that is causing this issue.  My suggestion is mainly to rule out any software issues before telling him to replace his computer -- I am actually really grasping at straws with that piece of advice.

Nomodeset may help if he can get far enough into an install to use it.  However, he needs to get to a terminal to use it and it sounds like he can't do that.  If the computer will boot to a "Try Ubuntu" live USB session that may be an option as he could get to a terminal and possibly save the setting to his USB stick, carrying that over to the installer and the finished install (I don't know if that is even possible -- that is getting outside my expertise).  If he cannot get to a terminal via "Try Ubuntu" or a finished install nomodeset is of no use to him.  If he can get Puppy to boot and install that might show that something related to nomodeset is the issue at hand (Puppy supports older graphics cards without that change in the kernel needed) but that still doesn't help him installing a Canonical OS.  If it gets that far your link could be of great assistance for him (although the pictures are long gone as they were hosted by a third party hoster and are no longer available), unfortunately the instructions for adding nomodeset temporarily to the install are for version 10.04 and may no longer be of help with the current versions of Canonical OSes (I don't have a spare computer that I can get away with ruining the current install with to check).  The permanent change instructions once the OS is installed are tried and true, however, and should still work at least with versions as new as 14.04.  Your link is now bookmarked in my computer, thanks for the link.

---

### Post by v3.xx on 2015-05-26
Me thinks, you have no idea what your talking about.

---

### Post by Geoffrey_Arndt on 2015-05-26
Matt, as info, if I recall right (it's been a while) . . . nomodeset is invoked via modifying boot options/parameters (_prior to starting install_ OR next startup).  That allows for PC to utilize the generic vesa video driver, and  navigation to the systems settings for install of proprietary driver.

---

### Post by mörgæs on 2015-05-27
Correct.

I think it's time to let the thread rest. More than enough (dis)information here, let's wait for original poster to return.

---

