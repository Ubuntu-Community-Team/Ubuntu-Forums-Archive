---
title: "Installation on new partition a few questions"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by rreyes3713 on 2011-05-24
I know this has been discuss a million times on this forum but when I do query, a million posts comes out and I'd have to sort through each one.
 
Anyway, I installed Ubuntu 10.04 on my laptop. It was a Wubi installation then I did the "migration" to a new partition so it dual boot in Window 7 and Ubuntu 10.04. I was in Linux heaven. (Well I used to use UNIX attending school so I felt at home using commands at the prompt).
 
But then my laptop died!!! Just two weeks after the one year warranty expired the laptop died. I won't tell you the make of the laptop just the initial, HP (lol). It was diagnose with a bad motherboard. Imagine, a mid-price laptop's motherboard died just a year and two weeks of use.
 
Anyway, a buddy of mine is going to give me his Dell Inspiron 8600. It was an upper price laptop at the time (2004) and it has XP.
 
I will be partition the hard drive and I want this laptop to dual boot in both XP and Ubuntu.
 
So my question is which version of Ubuntu should I download? Just wondering if the newer version will have trouble installing on an XP computer.
 
I'm looking at the instruction of installation of Ubuntu seems like most installation is a Wubi installation. Where's a link that gives me instruction on installation on a new partition?
 
Yes, I'm lazy sorting out through the many posts that discuss this. But at the same time I don't expect you members to hold me by the hand to do this installation. I think I'm adquate enough to do the installation. Just need to read up on it.
 
Thanks for at leasting reading my post. :)

---

### Post by aphatak on 2011-05-24
[LIST=1]
[*]I wouldn't expect any trouble whatsoever for Linux to co-exist with Windows XP on the same computer.  The choice of Linux version has nothing to do with it.  Your choice of Ubuntu version will depend on how you use Ubuntu - if you use it day in and day out with important stuff, you would want a stable, reliable version.  In that case, I would go with Ubuntu 10.04 LTS ("Lucid Lynx").  If you want Ubuntu only to play with, or to discover what it is like, go with the latest version - 11.04 ("Natty Narwhal").
[*]Whichever version you choose, you should re-size the Windows XP partition (which most likely will be labeled '/dev/sda1' in Linux), so that you have about 20GB free space; this should be used as 16GB or thereabouts for the root partition, and the remaining space for the swap partition.  I have seen it suggested that you should use Windows to reduce the Windows partition size, and Linux for creating Linux partitions.  However, I have used Linux for reducing the Windows partition size without any ill effects.
[*]Boot from the Live CD, and select the Install option.  You will get a choice to use the entire drive for Linux (which you should NOT take).  Select manual partitioning instead.  Create a 16GB (or thereabouts) partition, mount it as ext4, format it, and the mount point should be '/' (root).  Create a swap partition in the remaining area.
[*]Allow the installation to proceed.  Sensible defaults will be suggested, so it is usually okay to accept them.
[/LIST]
When you reboot after the installation, you should get the Grub menu giving you a choice of booting into Windows and Ubuntu.

---

### Post by oldfred on 2011-05-24
The main issue may be how much memory does computer have. Hard disk space should not be an issue, but I normally suggest smaller system partitions and separate data either shared NTFS if using windows or /home if just a new install.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

---

### Post by aphatak on 2011-05-24
I agree with oldfred.  However, if the laptop can run XP, memory should be comfortably large for Linux.
I normally mount the Windows partition as a data drive, but a shared NTFS partition is a perfectly good way to share data between Windows and Linux, too.  That would mean another partition, though.

---

### Post by rreyes3713 on 2011-05-25
Thanks guys, 
 
oldfred, yes my soon-to-mine laptop's system requirments checks out fine for Ubuntu installation. 
 
aphatak, thanks, I still think I have 10.04 Ubuntu formatted[sic?] on on my USB drive.
 

So here's my plan of attack: [LIST=1]
[*]Defrag the current hard drive (XP).
[*]Then partition (likely equal part). Not sure the HD capacity I'm guessing 60 Gigs. Yeah, I know, that's not much. (30 Gig each)
[*]Set the bios to read the USB port first.
[*]Then boot.
[/LIST]* I'd say I use Ubuntu 70% of the time. The only time I use Window XP is with Adobe PhotoShop / Image Ready, VB / VBA, M-Audio Fastrack USB interface (haven't found a script to install the Fastrack in Linux yet, but I read some have been successful), and Krystal Recording software. Rest of the time I'm using Ubuntu's apps whether its PHP / mySQL, Perl, Java, and other programming languages. I even like the PitVi video editor and Audcity Recording software (I know recording engineers are laughing at me using these user friendly recording software).
 
 
 

> **aphatak said:**
> [LIST=1]
[*]...
[*]Boot from the Live CD, and select the Install option. You will get a choice to use the entire drive for Linux (which you should NOT take). **Select manual partitioning instead. Create a 16GB (or thereabouts) partition, mount it as ext4, format it, and the mount point should be '/' (root). Create a swap partition in the remaining area.**
[*]Allow the installation to proceed. Sensible defaults will be suggested, so it is usually okay to accept them.
[/LIST]When you reboot after the installation, you should get the Grub menu giving you a choice of booting into Windows and Ubuntu.So what I highlight above is a given step in the installation instruction?
 
Otherwise, seems very routine installation. (I've installed Ubuntu 3 times, once for my laptop, twice on my buddy's, very clean).

---

### Post by aphatak on 2011-05-25
You are right on the button - the highlighted part correspnds with creating the partitions you have mentioned; the only point is, you can do it either before (as you have listed in *your* step 2) or during (as I had suggested in *my* step 2) installation from the live CD.
There is nothing wrong with giving 30GB to Linux;  however, it hardly needs that much space.  I allocate 16GB to my various Linux installations, and they are hardly half-full.  Windows XP (and later versions of Windows even more so) can hog hard disk space, though, and might complain at having only 30GB.  Give it a try;  if you find Windows does not like 30GB, you can always boot with your live CD and re-arrange the partitions later.

I know a couple of red-blooded, green-eyed graphics guys;  like them, if you have to work in CYMK space and cannot use RGB, you are stuck with Photoshop.  If not, you might want give GIMP a try for photo editing.  It is pretty powerful, there are tons of filters and plug-ins you can download, and it's free.  So if you can't use it, you still haven't lost anything.

And you are right, this should be a pretty straightforward installation.  Unlike the old distros, you do not have to turn handsprings and double-somesaults to install Ubuntu.

---

### Post by rreyes3713 on 2011-05-26
O-kay, I didn't realize you could partition during the installation steps. So I'll skip 'my' step 2 and use your step 2!
 
Yeah, I'm getting familiar with GIMP 'cause it has features just like PhotoShop. I even like the right click and a menu pops up instead of going to the platte [msp] to change your tools. In Gimp, you could select a tool from via right click then menu. 
 
But like PhotoShop there's a learning curve for GIMP. PhotoShop has the utliity app ImageReady which I could do animation gifs. But dang, I would have to purchase $500+ for newest PhotoShop (I'm still using my 5.0). So going more to GIMP.
 
Side Note: 
Yeah, talked my buddy into using Linux. Since I do a lot of computer programming, database adminstrating and web programming he just thought I was just pushing him to some programmer's operating system.
 
But he didn't want to purchase MS Office using Word and Excel so I turned him onto Office.Org. 
 
Once I help him installed Ubuntu, he never looked back at Window. He saids Windows runs too slow. Heh, heh.
 
Thanks aphatak, you answered my post.

---

