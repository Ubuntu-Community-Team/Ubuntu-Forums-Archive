---
title: "Trying to install to an i386 Dell with 250GB disk succeeds then boots to Grub Rescue"
date: 2020-10-21
forum: Installation &amp; Upgrades
---

### Post by mikeyrg65 on 2020-10-21
I am completely new to Linux and successfully had the machine running with a small hard disk.  Now I have put in a 250GB Hard Disk and have used a lubuntu 18.04.5 LTS disk to install.  All appears to go well unil the stage where one has to remove the media and reboot.  When the machine restarts there is a black, blank screen with the following at the top of the screen
error: Attempt to read or write outside of disk 'hd0'
entering rescue mode...
grub rescue>

How do I get the thing to run properly?
This message was entered on the machine with Lubuntu running from the disk media.

---

### Post by TheFu on 2020-10-21
My mirror only shows amd64 ISOs for Lubuntu. [http://cdimage.ubuntu.com/lubuntu/releases/20.04.1/release/](http://cdimage.ubuntu.com/lubuntu/releases/20.04.1/release/)

No i386 versions (which are actually i686).  If you cannot find an i386/i686 ISO, then you'll want to change distros. 

It appears that 18.04.5 Lubuntu has a i686 ISO file here: [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by guiverc on 2020-10-21
Did you verify the ISO as being perfect?  (an example of a check can be found in the Lubuntu manual, see [https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html))

And in my experience, more likely to be a problem, perform the media validation step?  (ie. validate a perfect write to install media using the "*Check disc for defects*" option in the first screen found in the Lubuntu manual - [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html))

Note: The Lubuntu manual is setup for Lubuntu 20.04 LTS, so what you'll see on your screens will differ, but be mostly the same.  (18.04 uses `ubiquity` as it's installer for example, where as all later releases use `calamares` as seen in the manual).

I've seen the issue you describe before, but not recently so I can't remember the cause. I have a feeling it's due to a inconsistency in either *file-system* or *partition table*, so I'd firstly boot *live media* (such as your Lubuntu install media; assuming it was checked as being perfect) then use the partitioning tool (`gparted` for 18.04 using GUI, `fsck` for CLI) to check your disk for errors. I'd also check SMART (`smartctl`, `gparted` etc) but that would be my habit..

---

