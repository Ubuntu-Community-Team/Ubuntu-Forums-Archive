---
title: "[SOLVED] Help for Laptop Distro"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by iaculallad on 2008-03-30
I bought an old laptop from a friend and im wondering of what Linux distro should i install. I tested installing Gutsy but it shows a black screen and details about CS,ES, etc.. (just like assembly language instructions), tested Daryna too but does not install.
Has somebody succesfully installed a Linux distro on Samsung SENS Q S760 laptop?
Here are the specs if it could help:

Model No:   	  SAMSUNG SENS Q S760
Processor: 	 Intel Mobile Penium3-M 750Mhz (not desktop processor!!)
Graphic Card:  Integrated in S3 Savage IX Hardware 3D Acceleration (Dual VGA support)
Memory 	Type: 100MHz Synchronous DRAM Memory
Memory:           128MB SDRAM SODIMM
Hard Drive 	 20GB Ultra ATA100, EIDE
Networking 	56Kbps V.90 Modem(Universal Modem), Integrated 10/100 Base-TX Etherner
Floppy Drive 	3.5" 1.44MB ( Left Bay of Slice Dock )
Lcd 	12.1" XGA TFT 1024-768
I/O Port&Expansion
on system 	SIO or RJ-45 LAN Port
External VGA Port
USB Port (3 ea)
RJ-11 Modem Port
Cable Lock Hole
Docking Port
RJ-45 Lan Port
2 USB Ports
Composite TV-out Port

Thank you.

---

### Post by Pumalite on 2008-03-30
Try Xubuntu Alternate CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
If it doesn't work, try Puppy.

---

### Post by tht00 on 2008-03-30
If it were mine, I'd probably put Gentoo (running fluxbox or openbox window manager) on it... but Gentoo is difficult to install/work with.  Next, I would probably look at Arch, though, I've never used it.


But hey, you aren't me.

My suggestion is to check out the more popular distros until you find something that works.  You might be hitting a hardware/kernel bug and a different distro might work fine -- simply because the configuration is slightly different.

Try distros like Fedora, Debian, SUSE.  See if any of those work.


Then again, the alternate install CD Ubuntu provides might work too.  You might not have enough RAM to run the liveCD installer.

---

### Post by wolfen69 on 2008-03-31
i just installed gutsy on a 10 yr old compaq laptop with 400mhz and 160ram. granted, i couldnt just pop in the ubuntu live cd and go. i did a minimal install (command line) of ubuntu and put the openbox desktop on it. it would not be easy for a novice to do though. here is a link for the how to [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by iaculallad on 2008-03-31
Thank you all for the fast reply with regards to my query. Right now, I'm downloading Xubuntu 7.10 alternate CD and Gentoo's 2007 liveCD for my testing. Gentoo :-) ?? if this distro would be successful for this laptop, well, this would be my first time to be with this distro, expecting to have the rough roads with Gentoo. I'll be posting the results...

---

### Post by wolfen69 on 2008-03-31
not trying to rain on your parade, but with only 128ram, xubuntu gutsy will run like molasses. if you're going to put gutsy on it, you're going to need a little more ram. 160mb is about the minimum  you need. ***and*** put a lightweight DesktopEnvironment on yourself.

---

### Post by iaculallad on 2008-03-31
I tried installing Gentoo 2007 LiveCD but with an error on the very stage of installation:
Error says:

CP: Write Error: No Space left in device

But this laptop has 20GB of space with XP preinstalled which I wanted to overwrite.
How can I solve this problem?

---

### Post by Pumalite on 2008-03-31
Stick to a light Desktop:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
If that doesn't work, try Puppy or DSL

---

### Post by squirlbuntu on 2008-03-31
> **iaculallad said:**
> I bought an old laptop from a friend and im wondering of what Linux distro should i install. I tested installing Gutsy but it shows a black screen and details about CS,ES, etc.. (just like assembly language instructions), tested Daryna too but does not install.
Has somebody succesfully installed a Linux distro on Samsung SENS Q S760 laptop?
Here are the specs if it could help:

Model No:   	  SAMSUNG SENS Q S760
Processor: 	 Intel Mobile Penium3-M 750Mhz (not desktop processor!!)
Graphic Card:  Integrated in S3 Savage IX Hardware 3D Acceleration (Dual VGA support)
Memory 	Type: 100MHz Synchronous DRAM Memory
Memory:           128MB SDRAM SODIMM
Hard Drive 	 20GB Ultra ATA100, EIDE
Networking 	56Kbps V.90 Modem(Universal Modem), Integrated 10/100 Base-TX Etherner
Floppy Drive 	3.5" 1.44MB ( Left Bay of Slice Dock )
Lcd 	12.1" XGA TFT 1024-768
I/O Port&Expansion
on system 	SIO or RJ-45 LAN Port
External VGA Port
USB Port (3 ea)
RJ-11 Modem Port
Cable Lock Hole
Docking Port
RJ-45 Lan Port
2 USB Ports
Composite TV-out Port

Thank you.

A good amount of RAM would be 318 MB. That would open a lot of new doors.

I know people may bring up PcLinux a lot but, but the 93a minime version does great, about the best I've seen with a 750 processor, there is only one repository that  supports it and it's out of date, but I just update the necessary stuff myself. 

Then there is the Pclinux minime 2008, if you get 318 MB of ram you would likely make this the system.

---

### Post by tht00 on 2008-04-04
> **iaculallad said:**
> I tried installing Gentoo 2007 LiveCD but with an error on the very stage of installation:
Error says:

CP: Write Error: No Space left in device

But this laptop has 20GB of space with XP preinstalled which I wanted to overwrite.
How can I solve this problem?

If you really want to install Gentoo, use the Gentoo handbook.  
[http://www.gentoo.org/doc/en/handbook/](http://www.gentoo.org/doc/en/handbook/)

It will walk you through everything.  Read carefully, there's a lot in there.

It is important not to use any of the automated installers.  They pretty much suck.  Plus, doing a manual install teaches you how to maintain the system.  The first time I did an install, I used the GUI and had a machine I didn't know how to maintain.  I hated it and ended up right back with Ubuntu.  It was only through (several tries) at a manual install that things made sense and I learned to love Gentoo.

With a slow machine, expect at least a week until you have a 'useable' X11 system.  I installed Gentoo on an old Mac (PPC ~300 mhz) and after I had Xorg installed, it took about 12 hours to compile Firefox and its dependencies IIRC.

It is a difficult distro to tame.  Packages break on installation/upgrade.  Once setup, I've found it rock-solid, but save upgrades of critical packages for rainy days.. just in case.

> **Pumalite said:**
> Stick to a light Desktop:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
If that doesn't work, try Puppy or DSL

If Xubuntu doesn't work, there's a load of things I'd try before Puppy or DSL.  (and besides Gentoo, of course ;) ).

Probably a ground-up Debian install running Fluxbox or Openbox.

---

### Post by Pumalite on 2008-04-04
I like Zenwalk too.

---

