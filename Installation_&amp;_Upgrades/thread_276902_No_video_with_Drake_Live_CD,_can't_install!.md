---
title: "No video with Drake Live CD, can't install!"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by jtrahan on 2006-10-13
trying to boot using the Dapper Drake cd so I can install Ubuntu on a pc. Before the cd boots to the desktop the screen goes black with a "Out of Range" message on the video screen. I know this is because the cd is trying to boot using 87.8 khz instead of 83.

So how do i specify 83 khz as a boot option for the Live CD to use? There is no OS insalled on this pc, so there are no conf files to edit.

Thanks,

---

### Post by Kateikyoushi on 2006-10-13
Try the safe video mode installation, if still no go the alternate cd has text mode install.

---

### Post by jtrahan on 2006-10-13
Sorry, forgot to put that in. "safe video mode" does the same thing, and even the F4 option at the bottom and going down to 640x480 does not help.

What is the "alternate cd" ?

thanks

---

### Post by Kateikyoushi on 2006-10-13
The alternate install uses text mode interface.

> The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
creating pre-configured OEM systems; 
setting up automated deployments; 
upgrading from older installations without network access; 
LVM and/or RAID partitioning; 
installing GRUB to a location other than the Master Boot Record; 
installs on systems with less than about 192MB of RAM.

You can find it on every mirror but here is a [LINK]("http://ubuntu-releases.cs.umn.edu//6.06/") just in case.

---

### Post by meng on 2006-10-13
What sort of system specs do you have (esp. RAM)? If your system is way underpowered, you may need to consider another more lightweight distro.

---

### Post by jtrahan on 2006-10-13
It's a brand new Dell Optiplex GX620, the problem is the 21 inch flat panel Sony montior. My old machine had the same problem, but Breezy did not have to boot into a live demo to do the install, so i was able to install it and then edit xorg.conf.

I just thought there would be an easy way to pass 800x600 83 khz as a boot option?

thanks again

---

### Post by meng on 2006-10-13
Ah I see. Although you may be able to run
sudo dpkg-reconfigure xorg-xserver
from the LiveCD, it's probably easier to install from the Alternate CD as already suggested.

---

