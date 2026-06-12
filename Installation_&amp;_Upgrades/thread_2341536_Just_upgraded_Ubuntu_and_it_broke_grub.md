---
title: "Just upgraded Ubuntu and it broke grub"
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by Brian_Hill on 2016-10-29
I just upgraded from Ubuntu 12.04 to 14.04 or what ever it is.
Restarted and was greated with grub rescue. This isn't the 1st time this has happened. I've been having problems with Ubuntu off and on. I've tried everything short of a clean install and I kept running onto problems.

I'm about to give up on Ubuntu. I don't know what else to do.

---

### Post by egeezer on 2016-10-29
From an older post, which I copied for my own use (I'd credit the author, but I lost the link):
  	 	 	 	   Try the following 
```
   	 	 	 	   
[INDENT]grub rescue > ls
(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)
grub rescue > ls (hd0,msdos1) # try to recognize which partition is this
grub rescue > ls (hd0,msdos2) # let's assume this is the linux partition *
grub rescue > set root=(hd0,msdos2)
grub rescue > set prefix=(hd0,msdos2)/boot/grub # or wherever grub is installed
grub rescue > insmod normal # if this produced an error, reset root and prefix to something else ..
grub rescue > normal[/INDENT]  
```
  	 	 	 	   
This should fix it ..
 *Correct partition will usually be formatted as ext2

---

### Post by oldfred on 2016-10-29
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Also post this, if you originally install grub into wrong place it remembers that and will reinstall to that wrong place:

 sudo debconf-show grub-pc

---

### Post by kevdog on 2016-10-29
Can you give me more information?  I think I've done this before.  I had to reconfigure grub to generate a new grub.cfg.  Although the process wasn't that difficult, I actually had to mount the /boot partition within a chroot, and then regenerate the file.

---

### Post by Brian_Hill on 2016-10-30
> **egeezer said:**
> From an older post, which I copied for my own use (I'd credit the author, but I lost the link):
  	 	 	 	   Try the following 
```
   	 	 	 	   
[INDENT]grub rescue > ls
(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)
grub rescue > ls (hd0,msdos1) # try to recognize which partition is this
grub rescue > ls (hd0,msdos2) # let's assume this is the linux partition *
grub rescue > set root=(hd0,msdos2)
grub rescue > set prefix=(hd0,msdos2)/boot/grub # or wherever grub is installed
grub rescue > insmod normal # if this produced an error, reset root and prefix to something else ..
grub rescue > normal[/INDENT]  
```
  	 	 	 	   
This should fix it ..
 *Correct partition will usually be formatted as ext2

Ya, doesn't work. Tried to do ls (hd0, msdos1), which is my boot partition, and got error: bad filename . I've also tried fixing it with a live cd and got some message about blocks not supported.

Oh, and setimg prefix and root, I've all ready tried that with all my partition. It doesn't work.

@kevdog, I've tried that it doesn't work.

@oldfred, I have know idea what that is.

This sucks, 'cause this build cost me over $700, and now it's almost a brick.

If I have to install the os all over, I'm going with a different distro.

---

### Post by kevdog on 2016-10-30
Is your /boot on a separate partition?  If you choose to go with a different distribution or stay with ubuntu, I'd just recommend you always but /boot on its separate partition.  I've hosed my boot partition before and had to reinstall it from scratch and the process was very easy.

---

### Post by Brian_Hill on 2016-10-31
Ya, i have a separate partition for boot.

---

### Post by oldfred on 2016-10-31
If you have a separate /boot then you have to also mount it when manually booting.
And you have to keep straight which files are in /boot and where / (root) is.

Example with Separate /boot on sda1, / on sda5:
 grub> set prefix=(hd0,1)/grub
grub> insmod linux
grub> set root=(hd0,5)
grub> linux (hd0,1)/vmlinuz-3.13.0-43-generic root=/dev/sda5 ro
grub> initrd (hd0,1)/initrd.img-3.13.0-43-generic
grub> boot

---

### Post by Brian_Hill on 2016-11-11
No good. I substituted my partitions, and that wasn't the problem.

I have a screen shot, but I don't know how to post it.

I'm going with a different distro. I'm tired of ubuntu screwing up my system. If my my home partition it messed up, I have no Idea what to do. All I know is I don't like ubuntu any more. &#55357;&#56851;

---

### Post by oldfred on 2016-11-12
Better to just run Ubuntu live installer in live mode and post the link to the Boot-Repair Summary report.

Often issues are related to what hardware, and how you have it configured. I found just using another 25GB for / (root) for new version rather than upgrading works a lot better. If you have issues before upgrading, you almost always have more issues after upgrade. System need to be working, fully updated, and all ppas & proprietary drivers removed, before upgrade to new version.

Even if you want to try another install, put it into another 25GB / partition.

---

### Post by Brian_Hill on 2016-11-18
Ya, the problem was that ubuntu broke grub, so I installed manjaro. It works fine, there's just a bit to learn. Even though ubuntu is still on my system. I can't boot into it.

---

