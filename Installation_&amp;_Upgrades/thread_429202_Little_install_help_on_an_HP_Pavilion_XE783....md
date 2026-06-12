---
title: "Little install help on an HP Pavilion XE783..."
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by crispy_420 on 2007-05-01
Ok i'll start with the why I am installing on such an old system:

The girlfriend talked me into it. It is her old computer as a gift for a coworker. And being a relative novice and such a low end system, I said no to Windows. Why, after installing all needed security software, the comp would just crawl. To pick up the pace I wanted Xubuntu, so no Gnome or KDE.

Specs:

---HP Pavilion XE783---
Intel 810 chipset mobo ( onboard video, sound, etc. )
256MB DDR
Intel Celeron 700MHz
Maxtor 30GB hard drive
52x CD-ROM

What I've tried for install:

7.04 -> alternate install and regular (standard and safe mode)
6.10 -> same
6.06 -> standard and safe mode via "shipit" disc

What I've tried hardware:

updated bios (via bios flash from floppy)
cleaned all dust out of system
I swapped out a CD-RW/DVD-ROM for that CD-ROM (user would not need)
cleaned up wiring (it was a rats nest in there)

My issues:

When it comes to install I get xorg issues. I have no option to get to command line now but when I did it only listed resolutions like 200 x wahtever (not even 640x480). I'm starting to think there is an on board video issue (hardware failure).

Where do I go from here? I was going to do it all alone but lost patience after two days. Then I thought, hey this is Ubuntu and I have a community to help me.

Need anymore details? I did install version 6.06 on this same system once upon a time before.

---

### Post by amohanty on 2007-05-01
Can you do a base install and run lspci at the terminal to see if the chipset is detected at all?

If it checks out then run:

sudo dpkg-reconfigure xserver-xorg

In there select the i810 driver (instead of the vesa thats selected by default) and later on select the resolution you want, default the rest and then hit a Ctrl+Alt+Backspace to restart X.

If that crashes, post the output of:

cat /var/log/Xorg.0.log | grep EE

AM

---

### Post by crispy_420 on 2007-05-01
Video chipset is seen correctly as Intel i810. But now I think I have a file system error. When I tried to reconfigure my xorg, I got an error saying file system error, it is read only. So now I will try to wipe the entire drive and start with scratch. I plan on using gparted livecd to wipe drive. Maybe I'll try a "lighter" distro to see if system has functional video.

---

### Post by amohanty on 2007-05-01
Hold on! did you do the **sudo**?

If you did, its possible that the partition was mounted read-only, thats an easy fix.

AM

---

### Post by crispy_420 on 2007-05-01
Sure did. I'm now starting to lean towards failed hardware though. I think it maybe a messed up video card. For example, if I look at my xorg it only lists 240xsome number.

---

### Post by crispy_420 on 2007-05-01
Try to wipe the hard drive with Darik's Boot and Nuke to see if a fresh install will help it all. Post back in a few hours with the results....

---

### Post by crispy_420 on 2007-05-01
OK that did not help. Now I'm lost. On live cd I get an xorg error right away, so not gui to install. The alternate cd leads to a dead end, install but no gui. That is why I'm leaning toward video chipset error.

Anywhere to get a bios guide for this mobo? It is a Asus CUW-AM.

---

### Post by Alacrity on 2007-05-02
Hey Crispy,

Funny you think you hava a dinosaur PC!  Mine is about the same but never thought about it being slow.  Dual boot with XP and a Linux Distribution with all the anti virus software.

Anyway, you want an idea or two?

For fun, pull down and burn 3-5  of the latest Linux Live CD Distros.  Knoppix 5.1, OPEN SUSE, Mandrivia, and so on.  Stick each one in turn into your CD and boot up.  ONE OF THEM will work.  Then install.  

Thank me later.

Alacrity

---

### Post by crispy_420 on 2007-05-02
OK another idea/issue:

When I look at my xorg in live (remember i have no gui), shouldn't the norizontal sync go up in value. For example, my functional install says 30-60. On the failed unit it says 20-12. Could this be the issue? Is the monitor I am using for setup not be seen for it's true values leading to failure in gui? Maybe look up the stats for this monitor and manually add in to xorg?

I think I solved my hard drive issues. For that I erased entire disc via Darik's as I mentioned before. As a test I used the original restore discs from HP and the install went fine. I have a functional (if you can call it functional) install of WinME. So I know hard drive, video, etc. are all functional.

I still can't figure out what the problem is. I did an install on the same system when 6.06 came out almost a year ago.

---

### Post by crispy_420 on 2007-05-02
OK I tried several distros as below with a quick note on each: (day off of work so many attempts)

Gentoo Linux 2006.1 Live/Installer - base config worked but no gui
Ubuntu 7.04 - no gui
Ubuntu 6.10 - no gui
Ubuntu 6.06 - no gui
Dream Linux 2.2 - booted and loaded fine, functional gui till it locked up
Ubuntu 5.10 LiveCD - actually worked, opens up a path to upgrade to current version (?) that will take a long time and switch to xfce
Berry Linux - no gui
Mandriva One 2007 - success but slow, too much for the hardware (disc I have has no install option & xfce would be nice too)
Dynebolic 1.4.1 - works but no installer
Knoppix 2005 (CD) - no gui, just scrambled screen
Dream Linux 2.1 - no gui and rebooted 
Linux Mint 2.2 - no gui but no surprise as it is Ubuntu based (no offense implied)

Ended up getting DesktopBSD installed but I hope to change that later.

---

### Post by snortman36 on 2007-05-03
crispy,

I unfortunately have one of those 783s at home as well. Even with a different pci graphics card in there (ATI-based), most modern distros that I have tried go blank screen (or X just pukes) when switching to X mode. Even (ahem) Windows 2000 fails to startup after the install. It gets stuck at the Starting Windows screen and will sit there all day. Haven't tried XP Home yet, mainly just afraid that it will fail also. I may give the Desktop BSD a shot, since it worked for you.

Personally, I wouldn't wish one of these systems on anybody, and I'm hoping that I will be able to replace mine soon. Good luck with your attempts, and if you find some magic fix, I would greatly appreciate hearing it.

---

### Post by crispy_420 on 2007-05-03
What is bothering me most is that it did have Ubuntu 6.06 pn it to start with. It was my girlfriend's pc (she now has taken my laptop0 and it ran ok, granted it was not fast but it got the job done for baisc tasks. I never had this issue until now. But I will keep trying on occasion or when I see some new "light weight" distro on distrowatch. At this point I have nothing to lose by trying, except time. But it is worth it to learn how to resolve issues.

On a side note see did have XP Home on there. It was a upgrade install from ME. With that old of hardware, I talked her into Ubuntu and she loved it.

If I get a functional install of a distro I'll post back. I would prefer linux to BSD, but I have no choice. I did manage to get a livecd/installer of Mandriva One running but failed to boot after install.

---

### Post by crispy_420 on 2007-05-04
OK now I reporting back with some good news. I finally found a distro that worked after a reboot. And it is Zenwalk v4.6. It even works pretty well. 

Also I failed to mention it earlier but I was wrong about the amount of RAM I had. I was under the belief that I had two sticks of 128MB to get 256MB. Turns out it was 192MB (128MB + 64MB). But oh well, I don't think this influenced my testing too much as most distros recommend 128MB at a minimum. At least the "light" ones I were looking to use.

Next step is to look into a lighter load on the hardware. Zenwalk uses xfce as desktop, I think I can trim that down. And the same with other components too. Worst case scenario, this could always become a FreeNAS box and save me all this gui headache.

For those looking for another "light" distro look into [Absolute]("http://www.pcbypaul.com/absolute/"). Think Zenwalk but even slimer. I would be using it but it failed on install and I think I may have the option of copying their concepts for my uses. Or maybe switch to [Fluxbuntu]("http://fluxbuntu.org/") when it is released.

I just hope my frustrations help another user with older hardware get a system up and running. Or maybe get someone to dust off that odd PC in the garage, attic, etc.

---

