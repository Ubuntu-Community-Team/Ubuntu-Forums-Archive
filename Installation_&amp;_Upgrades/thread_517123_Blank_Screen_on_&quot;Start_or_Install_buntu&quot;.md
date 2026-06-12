---
title: "Blank Screen on &quot;Start or Install *buntu&quot;"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by paperBag on 2007-08-04
Alright, so here's the skinny. I just started a programming internship at a company in town, and all they use is Linux (specifically Gentoo). So, in order to hone my skills, I'm ATTEMPTING to install *buntu on my home machine. I chose Ubuntu because every raves about how easy it is to install and whatnot, but to be honest, I had an easier time with Gentoo.

I'm on my 4th livecd (different versions including Kubuntu 7.04, Kubuntu 6.06 and Ubuntu 6.06 Server Edition). No matter which disk I try to install with, I still end up with the same problem. After clicking "Start or Install *buntu" I get the scrolling progress bar, maybe some text with the earlier versions, and then just a blank screen with an _ in the upper left hand corner. Nothing happens. After a few seconds, I'll hear some sounds (I presume the *buntu installer), but the screen still stays completely blank (sans the underscore). System specs are below. I've tried everything I can think, and nothing's working. md5sum is fine, there is nothing wrong with the disks - I even tried burning with my MacBook Pro and Disk Utility instead of Vista, and still nothing. So, here I am, on my knees, pleading. If I can't get this to work I'm just gonna say "**** It" in befuddlement of how "easy" the installation was.. Many thanks in advance for any help.

AMD Athlon64 X2 4200
Dual Nvidia 7800 GTs in SLI
2GB RAM (make and model eludes me and I'm to lazy to check)
250GB SATA WD Caviar HDD
120GB IDE Samsung HDD
NEC DVDR+/-
MSI K8N Neo4 Mobo

---

### Post by Alexander2007 on 2007-08-04
> **paperBag said:**
> Alright, so here's the skinny. I just started a programming internship at a company in town, and all they use is Linux (specifically Gentoo). So, in order to hone my skills, I'm ATTEMPTING to install *buntu on my home machine. I chose Ubuntu because every raves about how easy it is to install and whatnot, but to be honest, I had an easier time with Gentoo.

I'm on my 4th livecd (different versions including Kubuntu 7.04, Kubuntu 6.06 and Ubuntu 6.06 Server Edition). No matter which disk I try to install with, I still end up with the same problem. After clicking "Start or Install *buntu" I get the scrolling progress bar, maybe some text with the earlier versions, and then just a blank screen with an _ in the upper left hand corner. Nothing happens. After a few seconds, I'll hear some sounds (I presume the *buntu installer), but the screen still stays completely blank (sans the underscore). System specs are below. I've tried everything I can think, and nothing's working. md5sum is fine, there is nothing wrong with the disks - I even tried burning with my MacBook Pro and Disk Utility instead of Vista, and still nothing. So, here I am, on my knees, pleading. If I can't get this to work I'm just gonna say "**** It" in befuddlement of how "easy" the installation was.. Many thanks in advance for any help.

AMD Athlon64 X2 4200
Dual Nvidia 7800 GTs in SLI
2GB RAM (make and model eludes me and I'm to lazy to check)
250GB SATA WD Caviar HDD
120GB IDE Samsung HDD
NEC DVDR+/-
MSI K8N Neo4 Mobo

Did you try "Safe Graphics Mode"?

---

### Post by paperBag on 2007-08-04
Oh, sorry I didn't mention it, but yes I did, and still no go.

---

### Post by Alexander2007 on 2007-08-04
Hmm...It appears that Ubuntu has some conflict with your graphics card configuration. Don't loose hope just yet. I'm sure someone else with give you the answer you are looking for, but in the mean time try Google. I'm sure it is simple problem that can be fixed. :)

---

### Post by Alexander2007 on 2007-08-04
> **Alexander2007 said:**
> Hmm...It appears that Ubuntu has some conflict with your graphics card configuration. Don't loose hope just yet. I'm sure someone else with give you the answer you are looking for, but in the mean time try Google. I'm sure it is simple problem that can be fixed. :)

Check that link, hope it helps:
[http://ubuntuforums.org/showthread.php?t=379807](http://ubuntuforums.org/showthread.php?t=379807)

---

### Post by paperBag on 2007-08-04
> **Alexander2007 said:**
> Hmm...It appears that Ubuntu has some conflict with your graphics card configuration. Don't loose hope just yet. I'm sure someone else with give you the answer you are looking for, but in the mean time try Google. I'm sure it is simple problem that can be fixed. :)

Thanks for the encouragement :)

I've been all over, and I can't seem to find anyone else that's having quite the same problem I am. I suspected it might have something to do with my graphics cards, but at this point, I'll believe the magical evil fairies that live inside my computer are up to their old antics....

---

### Post by paperBag on 2007-08-04
> **Alexander2007 said:**
> Check that link, hope it helps:
[http://ubuntuforums.org/showthread.php?t=379807](http://ubuntuforums.org/showthread.php?t=379807)

AH! Nice detective work! I'll give it a try. Many thanks...damn Nvidia.

---

### Post by Alexander2007 on 2007-08-04
> **paperBag said:**
> Thanks for the encouragement :)

I've been all over, and I can't seem to find anyone else that's having quite the same problem I am. I suspected it might have something to do with my graphics cards, but at this point, I'll believe the magical evil fairies that live inside my computer are up to their old antics....

Try this link: [http://ubuntuforums.org/showthread.php?t=379807](http://ubuntuforums.org/showthread.php?t=379807)

---

### Post by paperBag on 2007-08-04
Live chat FTW! >.<

Hmm, I tried that fix with Kubuntu 7.04 and still no go. I get a little farther, but then just a COMPLETELY blank screen.

---

### Post by paperBag on 2007-08-04
I've been working on it for hours and still nothing. Damn you Ubuntu. "Just Works" my ***, more like "Mostly Works....unless you have hardware that isn't ancient..."

---

### Post by Alexander2007 on 2007-08-04
> **paperBag said:**
> Live chat FTW! >.<

Hmm, I tried that fix with Kubuntu 7.04 and still no go. I get a little farther, but then just a COMPLETELY blank screen.

When you say "get farther", how far?

---

### Post by paperBag on 2007-08-04
It actually isn't any further along, it just looked different and that got my hopes up. Since the culprit seems to be my graphics cards, but the fix didn't work, maybe the problem is SLI? Anyone else with SLI have isues?

---

### Post by Alexander2007 on 2007-08-04
> **paperBag said:**
> It actually isn't any further along, it just looked different and that got my hopes up. Since the culprit seems to be my graphics cards, but the fix didn't work, maybe the problem is SLI? Anyone else with SLI have isues?

Well it looks like SLI is currently problematic on Linux (and Windows too).
Check this site: [http://www.linuxquestions.org/questions/showthread.php?t=499317](http://www.linuxquestions.org/questions/showthread.php?t=499317)
And don't give up on Ubuntu, its not Ubuntu's fault.

SLI isn't popular at present time, so there aren't many tools to configure SLI based graphics cards.

This site contains the latest driver release: [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)
This driver claims to fix many problems, currently being experienced.

---

### Post by paperBag on 2007-08-04
I was able to get the Ubuntu 6.06 Server Edition installed because there is no GUI. From there I was able to apt-get elinks to browse to the NVIDIA site and download the drivers, but they won't install because I don't have make and gcc installed? WTF? Is that even possible? Why anyone would CHOOSE to use Linux is beyond me, but I don't have a choice. Here goes my entire weekend crying lonely in the dark at a terminal....

---

### Post by Alexander2007 on 2007-08-04
> **paperBag said:**
> I was able to get the Ubuntu 6.06 Server Edition installed because there is no GUI. From there I was able to apt-get elinks to browse to the NVIDIA site and download the drivers, but they won't install because I don't have make and gcc installed? WTF? Is that even possible? Why anyone would CHOOSE to use Linux is beyond me, but I don't have a choice. Here goes my entire weekend crying lonely in the dark at a terminal....

Ubuntu works on 90% of hardware, you just happen to be one of the unlucky ones because you own an SLI configuration. Don't give up hope.

---

### Post by Alexander2007 on 2007-08-04
> **paperBag said:**
> I was able to get the Ubuntu 6.06 Server Edition installed because there is no GUI. From there I was able to apt-get elinks to browse to the NVIDIA site and download the drivers, but they won't install because I don't have make and gcc installed? WTF? Is that even possible? Why anyone would CHOOSE to use Linux is beyond me, but I don't have a choice. Here goes my entire weekend crying lonely in the dark at a terminal....

Hey, If you got Ubuntu 7.04, try booting it again, if you manage to get a terminal, then do the following: ```
sudo aptitude install linux-generic nvidia-glx
``` 
```
sudo nvidia-xconfig
```
```
sudo startx
```

If that doesn't work then consider yourself unlucky.

---

### Post by pxwpxw on 2007-08-05
1. Install ubuntu 704 server (no gui). 606 is old.
2. Install X windows and desktop meta package. 
 ubuntu-desktop, kubuntu-desktop, or xubuntu-desktop. Fixup for workable desktop.
3. Install nvidia specific stuff (posts and links above).

---

### Post by paperBag on 2007-08-05
Thanks everyone for all the help. I'm just frustrated and confuzzled >.< On a good note, I'm writing this from my Ubuntu installation :D I just said f*** SLI and removed my second video card so I could get everything installed and updated before I throw it back in. And in case you're wondering, I ended up installing Feisty ^.^ I was amazed at how easy the installation actually was though. And I certainly don't hate Ubuntu or Linux, I'm just angry at Nvidia for selling my oddball video card for only like 2 months and providing little support on any platform (especially for SLI).

Thanks again all!
Cheers!

---

### Post by Jabb3r on 2007-12-02
Hi guys. I'm having this exact problem. CD boots, choose Start or Install, loads kernel, goes to another screen and then blank, nothin, nada. I'm using a Nvidia 8800GT, but no SLI, but I do have 2 monitors plugged in.  I dunno what to do with it.

Should add that I'm trying to load the  64bit 7.10 desktop version.

Any suggestions apppreciated

Thanks

---

### Post by Jabb3r on 2007-12-02
Managed to use a nosplash suggestion I found in a  thread on the F6 params

Hangs @ a screen after I click the contine on the low graphics mode prompt, tryin alternative installation cd

Edit: Alternative instaklllation CD worked fine.

---

