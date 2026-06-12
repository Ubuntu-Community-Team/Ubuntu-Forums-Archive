---
title: "Dell Inspiron, Ubuntu Install, and Recovery Partitions"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by ginsong on 2011-08-21
[FONT=Georgia][SIZE=3]Apologies if there is already a post out there related to this, but I couldn't find one.

I have a Dell Inspiron B120, an old computer with XP loaded on it.  It does the job (i only really use it for videos and writing), but it is slow and I am sick of windows.

I was set to install Ubuntu 10.04, but I saw there were three partitions:

1) A Dell Utility Partition
2) The Windows Partition
3) and a third partition, about 3 gigs in size, simply called sda3

I'm assuming sda3 is the recovery partition, accessible (from what I hear anyway) by pressing ctrl+F11 at boot, or something similar.

Here's the issue.  I figured I would install Ubuntu over the windows partition and leave the two others intact, just in case--for whatever reason--I choose to reinstall windows.

But, I am worried that if I do this, I won't be able to access that recovery partition.

Should I be worried about this?  And if it *would *ruin my ability to access sda3 or the Dell Utility Partition, is there a way to get around this, or burn the contents of the partition to a CD?

Thanks in advance.
[/SIZE][/FONT]

---

### Post by Megaptera on 2011-08-22
I have a Dell Inspiron so it's a bit newer than yours. However, I received 3 Recovery discs with the machine which I tested and ensured they worked. Did you also receive recovery discs? Or do you have an option to burn your own?

---

### Post by Mark Phelps on 2011-08-22
Sorry, don't have a Dell PC to test this, but if you remove the XP partition, replace it with an Ext4 partition (for Ubuntu), there is the possibility that, when you later boot the PC and try to do a Factory Restore (which is what I'm assuming you want to do), it will fail because the Dell software will become confused by the presence of a partition it can not understand.

IF that happens, you SHOULD then be able to fix it by booting from an Ubuntu CD, choose the Try Ubuntu mode, open up Gnome Partition Editor, remove the Ubuntu partition and replace it with an NTFS partition.

That should allow your factory restore stuff to work again.

You could also use an option to image off the current Windows install by downloading and installing the free version of Macrium Reflect, imaging the XP setup to an external drive, and using the option to create a Linux Boot CD.  That would allow you to restore the current XP setup later -- should you need to do that.

---

### Post by ginsong on 2011-08-22
Mega:
 
Unfortunately, no.
The person I received the laptop from didn't have the discs.  :\
 
Mark:
 
Okay... boy, I'm diving in the deep end here without a lifevest.  But... i think the sda3 is FAT32... would making an NTFS partition still work?  Plus, that seems kinda iffy, since it relies on the installation already being in place.
 
That last part sounds intriguing.
 
When you say "image the XP setup", do you mean the XP setup on sda3, or my current installation?
 
The reason i ask... I am unable to access sda3, except using ctrl+F11 or whatev (haven't tested that), and i am very unfamiliar with doing those sorts of things.
 
Part of me thinks I should just say damn the torpedos and just go for ubuntu.  I've used it before and really enjoyed it, and every time i go back to windows it feels like i have to go through five thousands hoops just for it be secure.
 
Thanks!

---

