---
title: "Can I install 9.10 from disk with Legacy Grub?"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by eakergd on 2010-04-19
OK, so I have been using 9.04 since its release.  Really got hooked on Linux.  Got a new laptop (Asus G50-x5) and installed 9.10.  Grub2 hangs for 40 seconds before booting Ubuntu.  Destroyed my MBR several times trying to fix it - had to reinstall windows because of it (I keep it around because Linux doesn't play MW2 or BF2).  Anyway, I went through a period of not using Linux on this laptop for several months, but I finally couldn't stand it anymore.  Installed 9.10 again with the same results as before (grub2 hangs).  Argh!  At least this time, I restored the Windows MBR without having to reinstall everything.  So then I get an old 9.04 disk and load that.  Golden -- everything works, and Grub legacy breezes right through -- super fast boot time.  

First attempt to upgrade was disastrous (corrupted packages).  I finally get 9.10 running after a couple reinstalls of 9.04 and upgrade attempts.  Now I have a system that is about 95% functional, but I keep running into bugs that I suspect are because I went the upgrade path instead of reinstalling a clean copy of 9.10.  The only problem with reinstalling 9.10 from the disk is that I am afraid I will be stuck with grub2 again, which I do not want on this computer.  So is there a way to do a clean install of 9.10 or the upcoming 10.04 with the option of keeping my Grub Legacy?

---

### Post by Neds Moar Salt on 2010-04-19
> **eakergd said:**
> OK, so I have been using 9.04 since its release.  Really got hooked on Linux.  Got a new laptop (Asus G50-x5) and installed 9.10.  Grub2 hangs for 40 seconds before booting Ubuntu.  Destroyed my MBR several times trying to fix it - had to reinstall windows because of it (I keep it around because Linux doesn't play MW2 or BF2).  Anyway, I went through a period of not using Linux on this laptop for several months, but I finally couldn't stand it anymore.  Installed 9.10 again with the same results as before (grub2 hangs).  Argh!  At least this time, I restored the Windows MBR without having to reinstall everything.  So then I get an old 9.04 disk and load that.  Golden -- everything works, and Grub legacy breezes right through -- super fast boot time.  

First attempt to upgrade was disastrous (corrupted packages).  I finally get 9.10 running after a couple reinstalls of 9.04 and upgrade attempts.  Now I have a system that is about 95% functional, but I keep running into bugs that I suspect are because I went the upgrade path instead of reinstalling a clean copy of 9.10.  The only problem with reinstalling 9.10 from the disk is that I am afraid I will be stuck with grub2 again, which I do not want on this computer.  So is there a way to do a clean install of 9.10 or the upcoming 10.04 with the option of keeping my Grub Legacy?

I think grub and grub-pc (grub2) are conflicting  packages, in which case the upgrade might remove your old grub, in which case you will need to reinstall it from a live cd or without rebooting if you can.

---

### Post by tommcd on 2010-04-20
After you first install 9.10, and before you try to boot Windows, the first thing you should do is to get all the updates for Ubuntu. There have been a number of updates for grub2 since Ubuntu 9.10 was first released.
When I first installed 9.10 it did not detect any of my linux distros (Zenwalk and Slackware) or Windows XP. After I got all the updates for Ubuntu, and ran **sudo update-grub** from the terminal, all my operating systems were detected and added to my grub.cfg file.
BTW, What version of Windows are you running there? Is it XP, Vista, or 7?
BTW #2, Did you first check your Ubuntu 9.10 CD for defects? This is always the first thing you should do, especially if you end up with a failed install like you did.
> **eakergd said:**
> 
 So is there a way to do a clean install of 9.10 or the upcoming 10.04 with the option of keeping my Grub Legacy?
See this to revert to grub-legacy:
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)
*One caveat*: I have never actually tried to do this. I just read about it when I found that tutorial. So I have no way of knowing how well grub-legacy would work with Ubuntu 9.10.
I would first try to fix the problems with grub2, since that is obviously the bootloader that Ubuntu will be using from now on.

---

### Post by eakergd on 2010-04-20
> **tommcd said:**
> After you first install 9.10, and before you try to boot Windows, the first thing you should do is to get all the updates for Ubuntu. 

Yes, I did that.  Updating Grub2 didn't help.  Still took 40 seconds just sitting there saying "loading grub", then it gave me a regular boot menu and everything worked fine after that.  I updated everything, and even tried a couple of fixes that ended up messing up my grub cfg (resulting in a reinstall) but couldn't make grub2 stop hanging up when first booting.

>  BTW, What version of Windows are you running there? Is it XP, Vista, or 7?  Vista -- why else would I not be able to stand it anymore?  :-P

>  BTW #2, Did you first check your Ubuntu 9.10 CD for defects? This is always the first thing you should do, especially if you end up with a failed install like you did.

Technically it wasn't a failed install -- everything worked perfectly, except Grub2.  It worked a whole lot better than the upgrade version I am running now.  Lots of bugs now, which is why I am interested in running a clean copy off a disk.  But to answer the question, yes, I checked for defects.  The same thing happens when I load it from a downloaded ISO burned to disk or from the disk distributed with Linux Format magazine.


> See this to revert to grub-legacy:
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)
*One caveat*: I have never actually tried to do this. I just read about it when I found that tutorial. So I have no way of knowing how well grub-legacy would work with Ubuntu 9.10.

OK, this seems helpful. I might do a clean install and see if I can make this work.

>  I would first try to fix the problems with grub2, since that is obviously the bootloader that Ubuntu will be using from now on.

Agreed.  Sort of sucks that they won't give me the choice.  "Do you want to upgrade Grub" would be a nice question to ask.  Its just a dang bootloader, and for the average user, all the extra bells and whistles that grub2 is supposed to add are not going to be used.  All we want is something that will ***QUICKLY ***let me choose the OS and move on.

Thanks for your help.  That last tip seems promising.  Not sure at this point whether to mess around with that or just go ahead to the beta of 10.04.  I'll probably read up a little before I do either one.

---

### Post by oldfred on 2010-04-21
Is this an install on more than one drive?

There is a known bug in grub 1.97 that if it is installed on a different drive than the Ubuntu install it will take 20+ sec to search before loading the grub menu. The work arounnd is to make sure grub is on the same drive as the Ubuntu install and make that drive the boot drive in BIOS.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

Another alternative:
Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)

---

### Post by eakergd on 2010-04-22
> **oldfred said:**
> Is this an install on more than one drive?

There is a known bug in grub 1.97 that if it is installed on a different drive than the Ubuntu install it will take 20+ sec to search before loading the grub menu. The work arounnd is to make sure grub is on the same drive as the Ubuntu install and make that drive the boot drive in BIOS. 

Yes it is a dual drive system.  Unfortunately, there is no option in the bios to decide which drive to boot from -- that is left up to the boot loader.  Grub is on the same drive as my ubuntu install (sdb), but the first time I installed it, I had it on sda along with the windows install (effectively destroying the windows mbr).  This is a laptop, so I can't go in and change the cables around.

Anyway, I find it interesting that this was pointed out as a bug prior to Karmic's release, and we still weren't given an option to install grub legacy.  This has been a major pain in my neck for a while now.  Reminds me of the first time I tried Ubuntu back at 6.04 and left it alone for 2 years because of all the hassles.

Makes me think maybe it is time to try another flavor of Linux.  I'll probably take a look at 10.04 and see if it is fixed there.

Thanks for the info.

---

### Post by oldfred on 2010-04-22
If your BIOS supports SATA it just about has to have a way to select which drive is primary master (boot drive). Old IDE drives you had to set jumper to specify primary master, but SATA drives do not have jumpers.

---

### Post by ScarySquirrel on 2010-04-22
Ugh. I share your frustration with Grub2, and I do not know why they have included Grub2 just when I had mastered editing menu.lst. 
It ignores hard drives. It hangs. It leaves menu.lst around, like a mirage, to tempt unsuspecting noobs like myself. These may not all be directly Grub2's fault, but because ubuntu with grub1 had no such problems, I blame grub2. Can't Grub2 at least include better detection scripts included by default? 
WE HATES IT.

---

### Post by eakergd on 2010-04-30
Well, I am happy to report that all is well with the new version.  I did get Slackware installed, but it defaults to the KDE desktop, and I've never really liked that.  The Lilo boot manager was working fine, though.  Anyway, I decided to try 10.04 with the hopes that they did something to fix the bug in Grub2.  With my fingers crossed, I rebooted after the install, and I immediately got a grub menu, chose Ubuntu, and got to my desktop in under 30 seconds.  Sweet!

Thanks to those who attempted to help.  I gotta go play now.  :-)

---

### Post by tommcd on 2010-05-01
> **eakergd said:**
> Well, I am happy to report that all is well with the new version.  I did get Slackware installed, but it defaults to the KDE desktop, and I've never really liked that.  The Lilo boot manager was working fine, though.
For future reference, you can configure what desktop environment you want as the default in Slackware by running **xwmconfig** as a regular user from the terminal. It presents you with a ncurses interface that lets you choose between KDE, XFCE, Fluxbox, Blackbox, and a few others. I always use XFCE in Slackware.

---

