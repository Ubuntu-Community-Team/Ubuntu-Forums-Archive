---
title: "Re-installing 10.04 over bad upgrade without losing stuff."
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2010-08-03
Please can the team help?
I recently upgraded to 10.04 from 9.10 and have some questions:
1. Will a clean install of 10.04 perform better than my upgrade?
2. Will it get rid of the message I get at boot time about IRQ #18 being disabled.
3. The boot splash image does not appear after the upgrade. Will it appear after a clean install? (It does when booting from 10.04 live CD).
4. And finally: I can see that there are some 20 or so folders including home when I do ls / 
```

mike@mike-laptop:~$ ls /
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
mike@mike-laptop:~$ 

```
How may I preserve stuff I have on my upgraded system such as:
- VirtualBox running a Windows XP guest, its application and data.
- Wireless LAN implemented using ndisuio? wrapper
- Canon PIXMA IP2600 driver

---

### Post by mikewhatever on 2010-08-03
I don't know if a clean install will fix the problems you mentioned. Need to try.
Before doing that, backup your home folder. Ndiswrapper and the Canon driver will need reinstalling.

---

### Post by welshmike on 2010-08-03
> **mikewhatever said:**
> I don't know if a clean install will fix the problems you mentioned. Need to try.
Before doing that, backup your home folder. Ndiswrapper and the Canon driver will need reinstalling.

Thank you for your prompt reply.
I'm OK with Ndiswrapper and the Canon driver, if a bit tedious to do.
I can see a .VirtualBox folder in my home folder so will it and its Windows XP guest and applications installed there be restored when I restore my backed-up home folder?

---

### Post by ahbart on 2010-08-03
Make a copy of you complete home folder. Including the hidden files starting with '.' and place it on a external disk, dvd or usb stick.
Do a fresh install of ubuntu. It would be a good idea to create at least a separated partition for /home
And a much smaller root '/' partition. All depends on your disk size and space available for linux.

Login to the new system and restore (copy back) the files and folders. Including .Virtualbox. It is not a smart idea to copy everything back, because that won't give you a clean install then. ;-)

---

### Post by welshmike on 2010-08-03
Thank you ahbart.

I originally had just a single partition Windows XP system and when I first installed Ubuntu some years ago I think I resized that partition and either left free unformatted or maybe ext3 space for an Ubuntu installation.
I then let Ubuntu install set up its default partitions. One included /home and /root , the other swap. My current Ubuntu system occupies 30GiB.
Please will you advise what partition sizes you suggest out of that 30GiB for /home , /root and swap?
Do I need to create the partitions before install, or does the install help me create them?

Many thanks
Mike

---

### Post by ahbart on 2010-08-03
There are, always have been en will be a lot of discussion about partition size and the size of swap. Root and Home depend of what you are using this system for and how many data (documents, music, video, virtualbox images) you have. 

With 'just' 30Gb (My first hard disk was 10**M**b ;-)). I would do:
10 for root, 19 for home and 1 for swap. But swap depends on how many internal memory your computer has.

---

