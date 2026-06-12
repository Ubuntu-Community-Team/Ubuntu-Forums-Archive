---
title: "Xubuntu 12.04 install hangs ..."
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2012-05-03
Hi all, 

As the title suggests, I'm trying to install Xubuntu 12.04 but once the details are filled out at the beginning, starts to install then the GUI window for the installer quits and I have a spinning disk cursor which stays that way for hours if I leave it. 

I can operate the machine while all this is going on and when I look in Gparted, the two partitions I am installing to (sdb6 and 7) show /target/ and /target/home/ so I'm figuring it's installing but it never stops and I have no GUI for the installer telling me what's happening. Hmm.

So, my next plan is to see if I can install 10.04 LTS, use that for a year then upgrade to 12.04. I have XP and 8.04 LTS on sda (both solid) and data and nothing else on sdb (where I'm attempting to install 12.04). 8.04 has always been rock solid on this (old) machine and installed without a hitch when I originally installed it.

All suggestions, ideas and advice welcome. Tnx in advance ... ;)

---

### Post by mips on 2012-05-04
What happens if at the boot screen for the cd you select Install Ubuntu instead of Try Ubuntu?

If it was me I would download the 12.04 Alternate CD Image and install from that.

---

### Post by Bucky Ball on 2012-05-04
Thanks mips. 'Try Ubuntu' has always been fine. Trying to install is where the problem is. 

But problem solved. I ended up doing a minimal install of 10.04 LTS instead (with xfce4 DE) and all went without a hitch (more or less but still having some what I think is java issues; no biggie). Installed / and /home to sdb, put the 10.04 grub on sda and used the existing /swap on sda. Grub picked up XP and 8.04 LTS just fine and they all boot just fine.

The machine is the fastest it's ever been and the minimal install was the way to go for it; it's old, low-spec and not used for much anymore so really doesn't need much on it. I'm happy for now. Cheers. ;)

* I'm marking this thread as solved, but I guess, technically, my original problem never was. I didn't try the alternate or the minimal install, though, and I would advise anyone else to go down that route. That is where I was heading before deciding to install 10.04 LTS then upgrade to 12.04 in a year when 10.04 is out of support (or maybe sooner). Good luck ...

---

### Post by mips on 2012-05-04
You could try the Xubuntu 12.04 Alternate CD image.

I ALWAYS use the alternate images and always do a clean install. I also do a minimal/cli install from the alternate image instead of the full install so maybe try out 12.04 alternate minimal install...

---

### Post by Bucky Ball on 2012-05-05
> **mips said:**
> You could try the Xubuntu 12.04 Alternate CD image.

I ALWAYS use the alternate images and always do a clean install. I also do a minimal/cli install from the alternate image instead of the full install so maybe try out 12.04 alternate minimal install...

Happy for now thanks but thanks for the thoughts. I will be installing 12.04 minimal to a partition on my laptop mid-year so might do it from the alternate, as you suggest. Would an install from the Xubuntu alternate cd be a smaller install again than the Ubuntu mini.iso? I'm guessing so, but then again, both would be installing the base system first, regardless? 

I don't have any more time to screw around with the old desktop I have been working on, I just need it to be stable and supported and the install couldn't have gone better. I'll think about 12.04 LTS on that box when 10.04 is reaching eol (or possibly after 12.04.1 or .2). The only reason I've altered it at all is because it was using 8.04 LTS and out of support (and couldn't upgrade to 10.04 through update manager because there wasn't enough headroom on sda ... another story). 

Cheers. ;)

* I've only installed a dozen or so apps on the desktop and it really has given it a new lease of life. Faster, quieter, cooler (the machine does have a quality PSU in it but 8.04 was crammed into a 7Gb partition which was almost full on sda, now has 10Gb and not much installed on a newer IDE drive, sdb; the install is 3Gb or less from memory).

---

### Post by mips on 2012-05-05
> **Bucky Ball said:**
> Would an install from the Xubuntu alternate cd be a smaller install again than the Ubuntu mini.iso? I'm guessing so, but then again, both would be installing the base system first, regardless? 

I think the end result is the same. With the minimal cd packages are pulled off the net unlike the alternate that install them from the cd. The benefit here in using the minimal iso is that all the packages are the latest versions where with the alternate iso they will be older and when you update & upgrade it will pull in a whole lot of new stuff again.

---

### Post by linuxmatt7 on 2012-05-05
I have had this happen to me the other day. When I was installing Xubuntu 12.04 LTS on my system(s). I was installing it over Xubuntu 9.10

Here is a easy work around. File a report on the Debian installer package. Then download Ubuntu 12.04 LTS iso and burn to CD/DVD. Then install Ubuntu 12.04 LTS than install the Xubuntu packages over Ubuntu. With this command.

"sudo apt-get install xubuntu-desktop"

Than run this command to remove Unity

"sudo apt-get remove unity unity-2d"

Now you are with Xubuntu 12.04 LTS with some Ubuntu applications which you can remove in the Ubuntu Software Center.

---

### Post by Bucky Ball on 2012-05-05
> **linuxmatt7 said:**
> 

"sudo apt-get install xubuntu-desktop"

Than run this command to remove Unity

"sudo apt-get remove unity unity-2d"

Now you are with Xubuntu 12.04 LTS with some Ubuntu applications which you can remove in the Ubuntu Software Center.

Thanks but I only use xfce so Unity is not an issue, already running Xfce DE over Ubuntu on a couple of installs on other machines and not interested in doing that on the one in question. ;)

---

