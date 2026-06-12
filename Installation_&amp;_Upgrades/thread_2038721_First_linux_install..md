---
title: "First linux install."
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by ickPers on 2012-08-07
Im planning to dual boot Ubuntu and Windows 7. 

I have 3 internal hard drives, one for windows, one for all my games and one for downloads and such.

I dont have enough space on the C drive to install Ubuntu on the same drive as Windows so I am planning to install it on the hard drive with my games on it (G: Games).

So these are my questions to get me on my way:
1. Does the "install alongside windows" option mean it will install on my C drive? Or is this just a simple option to get the thing installed and dual booting?
2. Choosing the "something else" option I get asked to define a root file system, which of the options should I choose here?
3. The Games drive is /devsdb, do I choose this for the boot loader installation?

These are probably silly questions but I want to be sure of what im doing before I go ahead in case I end up having to reinstall windows. 

Thanks if you can help.

---

### Post by mastablasta on 2012-08-07
> **ickPers said:**
> 1. Does the "install alongside windows" option mean it will install on my C drive? Or is this just a simple option to get the thing installed and dual booting?
2. Choosing the "something else" option I get asked to define a root file system, which of the options should I choose here?
3. The Games drive is /devsdb, do I choose this for the boot loader installation?

 
careful, since you have windows on same mashcine and maybe some data you want to keep.
 
in dual boot it's always good to backup...
 
1. it's a simple option to install alongside windows. usually it's easy to use if you create an empty disk parititon (non formated space)
2. root is / --- which is kind of like C:\ drive in windows. it' where sytsem will be installed and all files. you can also chose to cretae separate partition for /home (which is kind of liek my documents). if you go manual you need to create a small partition for swap (at least the size of ram or a bit larger). partition is /swap and is like page file in windows.
3. i believe GRUB boot loader goes to sda. but i am not sure here since i usually let the automated process handle the install.
 
sdb is second hard disk, sda is first disk...
 
/sdb1 is first partition in second disk
/sdb2 is second partition in second disk and so on...
 
 
note that unless you use wubi all data on that partition where you install the os will be deleted.
 
some additional info you can read in ubuntu manual (in my signature) and here:
guide with pics: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)
additional info: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
 
additionally it's good to boot live system first (try it option) to see if all works well on your maschine.
 
specificaly dual boot guide: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Kalanac on 2012-08-07
Hi there!

Congrats for taking the jump to Linux.  I'm not sure how much PC experience you have in general so if some of this is a bit basic I'm just covering bases :)

OK, you mention you have 3 drives.  Each of these will have 1 primary partition which takes up all the space unless you've put any partitions in before now.

Ubuntu will need it's own partition in order to install itself.  It'll actually need 2 partitions but will usually use a second "logical" partition for a swap file.  This will be created automatically if you use the guided partition option.

There's a few options for you:

Install alongside windows will try and resize your windows partition and install Ubuntu into the freed up space.  This has a slight amount of risk as data could become corrupted or in the very worst case your entire partition could be ruined.  Such occurrences are very rare though, still it's advisable to back up your irreplaceable data just to be safe.  Also run defrag in windows as this tidies up the drive a bit before changing the partition.

Ubuntu doesn't take up all that much space so you might find you can create a small partition on one of your other drives, like perhaps the download drive (unless you have a LOT of stuff on there :D)  Depending on what you're using Ubuntu for, you'll probably find 10-20gig will be plenty of space.  You could run the whole thing comfortably on a 4gig pen drive :)

If you want to create a partition scheme manually then you'll need to understand some important linux conventions.

Linux has drives, which are the physical storage devices and it has mount points which is where files are located.  Drives are usually called things like sda, sdb, sdc etc.  Mount points vary depending on what they're used for.  The primary root mount point is /.  (Just the slash, not the dot :))  From here your entire file system is constructed.

As mentioned before, Ubuntu needs two partitions to run properly a root partition and a swap partition.  A drive can only have 4 primary partitions on it and inside each partition it can have 4 "logical" partitions.  Often the convention is to create a primary partition with 2 logicals inside, one for swap and one for the file system.  It doesn't matter how you partition the drive so long as there are 2 partitions for use by ubuntu.  The installer can create both of them for you.  If you're going for this option then you'll need to do the following:

Clear a space on one of your drives.  This isn't just a case of deleting files.  You need to resize the partition either using gparted from the ubuntu live environment or using the partition manager in windows (you'll need to drum up a help file on that, I'm not too familiar with it).  Clear up as much space as you think you'll need plus about 4gig for the swap partition.

In the installer, create a 4gig partition and select it for use as the swap partition.  Then create a partition that takes up the rest of the space, format it into ext3 or ext4 and set the mount point to /

That should do it.  Install the boot loader into the MBR of the drive you installed ubuntu onto, it's the easiest and most convenient option.  GRUB, the boot loader, should then automatically configure itself to find all other operating systems and include them in the boot menu.

If you run into problems just post them up, someone will help :)

---

### Post by ickPers on 2012-08-07
Firstly thanks for the replies.

I have went ahead with the installation after backing up windows files and making a restore disk etc..

Linux installed fine and I got my swap partition etc sorted ok. However when the system rebooted it just booted straight into windows without the option to choose to boot to linux.

I guess im glad that windows didnt get corrupted in some way at least. I have EasyBCD open and am thiking about adding a new boot entry.

---

### Post by ickPers on 2012-08-07
Its all working now. I used EasyBCD to set the boot option for ubuntu. :)

---

### Post by Buntu Bunny on 2012-08-07
> **Kalanac said:**
> Hi there!

Congrats for taking the jump to Linux.  I'm not sure how much PC experience you have in general so if some of this is a bit basic I'm just covering bases :)

I'm getting ready to install Ubuntu 12.04 dual with Windows 7. This will be the 3rd time I've done this over the past several years (different computers, different distros of Ubuntu), but it seems like the first! I've been reading up, doing my "homework" and have to say I appreciate this explanation. Very clear, very helpful.

---

### Post by Buntu Bunny on 2012-08-07
> **ickPers said:**
> Its all working now. I used EasyBCD to set the boot option for ubuntu. :)

Glad it went well for you and doubly glad to know about EasyBCD.

---

### Post by Kalanac on 2012-08-08
> **ickPers said:**
> Linux installed fine and I got my swap partition etc sorted ok. However when the system rebooted it just booted straight into windows without the option to choose to boot to linux.

At a guess you used a USB stick to install from?  Typically this is caused by accidentally installing grub to the Master Boot Record of the USB stick instead of your hard drive.  You want to install grub to the hard drive you boot first in the bios settings :)  EasyBCD is a good way to fix the problem if it's already happened :)

Welcome to the Linux community anyway :)

---

### Post by mastablasta on 2012-08-08
there is also boot repair tool
 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

