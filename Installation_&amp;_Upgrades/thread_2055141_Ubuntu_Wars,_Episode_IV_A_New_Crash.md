---
title: "Ubuntu Wars, Episode IV: A New Crash"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2012-09-08
Once again, I beseech the Ubuntu Gods for release from my suffering.

My configuration:
[LIST]
[*]Gigabyte GA-MA78-US2H motherboard, 8 GB RAM, AMD x6 1100T CPU
[*]NVidia 460 family GPU card
[*]Ubuntu 11.10 OS, 64-bit, no other operating systems to complicate matters
[*]Two hard drives operated in RAID1 configuration, administered by *mdadm*
[/LIST]

_[I have found that I need a very recent NVidia GPU driver (version 295.59)]("http://ubuntuforums.org/showthread.php?p=12022500#post12022500")_ to get this system to boot.  Frequently, when Linux kernel upgrades come in, my system initially refuses to reboot.  About four times out of five, I have to rebuild the video driver manually.  I'm an old hand at this by now.

_[Due to some other problems which I believe were inconsequential]("http://ubuntuforums.org/showthread.php?t=2039073")_, I did a fresh re-install of 11.10 recently, and I got kicked all the way back to the 3.0.0.12 kernel.  Yesterday I accepted the kernel upgrade to 3.0.0.25.

On reboot, I got the high-resolution Ubuntu splash page and I thought -- good, I don't have to rebuild the video driver this time.  Usually, when I have to rebuild the driver, I don't even get the splash page, just a blank Aubergine screen.

But then, the system just hung.  Ctrl-Alt-F1 through -F6 did not bring up any terminals for me to use to log in and recompile the video driver.  I shut the system down and restarted it.  This time I did not get the splash page, only Aubergine.

This made me think that I had to go back and rebuild the video driver the way that I have to do when I first install the OS.  So I got out my alternate install CD, booted into a rescue shell, and  recompiled my video driver.

On reboot, I got the Ubuntu splash page again... and then it hung, again.  I watched the system for several minutes.  Occasionally I would see a little hard disk activity.  Every 30 seconds or so I'm used to seeing a quick flash of my hard disk activity light, I think it's the ext4 file system doing some housekeeping.  Interspersed with that, I saw a few, longer bits of hard disk activity.  Ctrl-Alt-F1 through -F6 did nothing.  After a while I rebooted with Ctrl-Alt-Del.

The system will still boot from the standard 11.10 CD.  As long as I remember to go to the boot options menu, select the *nomodeset* option, and then "Try Ubuntu without installing", I can get the system to the GUI.  Of course, I don't have *mdadm* when I boot from the CD, so I can't mount my RAID.  But I can see both hard drives and all of their partitions if I run *gparted*.  Everything seems to be intact.

So, does anyone have an idea what my problem might be **this** time?  Thanks!

_EDIT:_ 

On re-reading my own earlier post, I noticed that I had similar symptoms once before.  Linux kernel 3.0.0-12 through -20 would run with NVidia driver 295.40.  When I upgraded the kernel to -21, I HAD to upgrade the NVidia driver to 295.59.

I'm currently investigating the hypothesis that I need to upgrade to a more current NVidia driver once again to support the -25 Linux kernel.  I visted the NVidia web site, and the current Linux driver version is 304.43.  I'll report back.

I find this maddening.  Is there any way to AUTOMATE this part of the Linux upgrade process?

---

### Post by ladasky on 2012-09-08
I have confirmed it, the video driver needed to be upgraded again.  The installation process was messier than usual, however.  I'll post the details to the ever-popular and long-running _[graphics driver troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1743535")_.

---

### Post by BicyclerBoy on 2012-09-08
Don't take this the wrong way..but your graphics driver problems are self-inflicted.

If you go outside of package management system & use the nVidia installer method it is locked to the kernel version at build time.
You also need build dependencies & 32 bit stuff for 64 bit OS.

The best way to get an up-to-date nVidia driver (if required) is from x-swat or if real desperate, xorg-edgers ppa.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

These package install using dkms & survive (rebuild triggered) kernel updates.

I would strongly recommend to never update nVidia graphics driver & kernel at the same time.

---

### Post by ladasky on 2012-09-16
> **BicyclerBoy said:**
> Don't take this the wrong way..but your graphics driver problems are self-inflicted.

If you go outside of package management system & use the nVidia installer method it is locked to the kernel version at build time.
You also need build dependencies & 32 bit stuff for 64 bit OS.


No offense taken, BicyclerBoy.  Although I am a programmer, I'm no systems administrator.  I learn what I can from people here in the forums.

When I started having video driver problems _[about six months ago]("http://ubuntuforums.org/showthread.php?t=1960714")_, using an NVidia 8800 card and the 280.13 series driver (along with THOUSANDS of other people), I read and followed the advice _[in this thread]("http://ubuntuforums.org/showthread.php?t=1743535")_, without understanding all of it completely.  _[This post]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")_ was the most important one for me.  I had some special extra concerns due to the fact that I used RAID.  My modified procedure is found _[here]("http://ubuntuforums.org/showpost.php?p=11918272&postcount=1003")_. 

Looking back, it appears that the advice to take manual control of driver updates and rebuilds might have been due to the fact that NVidia went through a phase where the "latest" drivers were NOT universal.  Initially, some of their new drivers broke older cards.  Then they released drivers which fixed the older cards, but broke the newer ones!  Is that all in the past now?  Then I might be able to return to letting Ubuntu manage video driver updates automatically.  It's clear that some video driver updates are NOT optional in my current configuration, when the kernel bumps.

The last time that I rebuilt my RAID, I deliberately left a spare partition so that I can install 12.04.1 without uninstalling 11.10 (which works, more or less, although I just received a notice that it's time to bump the kernel again, grumble).  

I've been using Ubuntu since 6.06.  Perhaps I can set up 12.04.1 to do things correctly, the way everything seemed to work until six months ago?

> **BicyclerBoy said:**
> 
The best way to get an up-to-date nVidia driver (if required) is from x-swat or if real desperate, xorg-edgers ppa.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

These package install using dkms & survive (rebuild triggered) kernel updates.

I would strongly recommend to never update nVidia graphics driver & kernel at the same time.

OK, I just read about DKMS, and obviously that's what I want.  I don't understand x-swat -- is that a repository that I can (and perhaps must) add to apt-get?

---

### Post by BicyclerBoy on 2012-09-16
Yes the x-swat ppa should be added to package management via apt-add-repository or pasting URL into synaptic etc.
It is possible to just download a deb package from the ppa.
[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

The 8800 was reinvented (by marketing dept) with at least 3 GPU versions so maybe nVidia forgot how to make them all work.

Some of the 8800 (G80) don't have video decode vdpau etc.

The GTX460 has support from driver version 275 (& maybe earlier)..

Altho 30x series came out 3? months ago, the driver branch 295 has had a bug fix 2 weeks ago.

---

