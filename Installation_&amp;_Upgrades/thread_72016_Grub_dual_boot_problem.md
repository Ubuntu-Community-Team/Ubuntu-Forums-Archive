---
title: "Grub dual boot problem"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by weazoe on 2005-10-05
Hope you can help a Linux Noob. I installed the Breezy pre-release about two weeks ago, dual booting with Win XP. I have to say I'm quite impressed, I guy could learn to live with this. However, today after the Linux system upgraded the kernel, for reasons uknown to me Windows just disappeared as a boot option. It's simply no longer there. (Maybe an omen?) The windows partition is still there, I can still browse it, I just cant load it. If anyone can help I would appreciate it. Sadly, there are still applications that need Windows to run and I can't do without them.
Thanks, Chris

---

### Post by Emerzen on 2005-10-05
Weazo,

Open a terminal and type the following:

sudo fdisk -l

then copy the results and post them here.  Don't worry, should be able to get your Windows back in a jiffy and tell you how to prevent this from happening in the future.

---

### Post by weazoe on 2005-10-05
Emerzen, Thanks for the quick reply. I hope this gives you some insight into the problem.
Weaz.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        9588    25816455   83  Linux
/dev/sda3            9589        9729     1132582+   5  Extended
/dev/sda5            9589        9729     1132551   82  Linux swap / Solaris

---

### Post by Emerzen on 2005-10-05
Hey Weazo, try the following at a terminal:

sudo gedit /boot/grub/menu.lst

A window will open up w/ a bunch of text.  Scroll down to the bottom.  You will find a line that looks like this...

### END DEBIAN AUTOMAGIC KERNELS LIST

Below that line copy the following text...

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

Save it and exit.  Reboot and select 'Windows 95/98/NT/2000" from GRUB and let me know how it goes.  I'll let you know what this is all about when we get it working.

---

### Post by weazoe on 2005-10-05
Emerzen, you're a real sweetheart! I'd buy you a beer if I knew where you were, but you'll just have to settle for my thanks.
I'm writing this from Windows, so obviously your instructions worked. If you wouldn't mind giving me the basics of what this was all about, I'd appreciate it. Also, you seem to be preety good with Linux, could you recomend a book that gets into the whole OS in depth? I'm curious and from what I've seen in the last couple of weeks very impressed.I'd like to learn more.
Again, many thanks,
Weaz

---

### Post by Emerzen on 2005-10-05
Hey Weazo...I'm in Syracuse, NY and if you're ever in town, I'll take that beer=).  Basically, GRUB reads that list to determine which partitions have bootable OS's on it.  So, I first had you list all the partitions on your hard drive...looking for the one w/ a Windows NTFS partition (/dev/sda1).  We then added the command that tells GRUB where to look for windows [root hd(0,0)] which is the Grub equivalent of /dev/sda1.  Most importantly, we added it below the line about the 'automagic' stuff, so the next time your linux kernel updates/grades, Grub won't remove the Windows stuff (anything below automagic won't get reconfigured unless you do it manually).   This command is for NTFS partitions, if you ever need to add Linux, look above automagic and you can see how that works.

As for learning Linux, I'm definately no expert, this is a problem I've had before though.  Here are some things that have shown me a thing or two about Linux however.  Go through the Unofficial UbuntuGuide from top to bottom [www.ubuntuguide.org](www.ubuntuguide.org) .  This is actually a lot of fun and you'll get a feel for the system.  On my own I've got a book called "How Linux Works," by Brian Ward ISBN: 1593270356, which is a bit dense but has a lot of good info.  I am not ashamed to admit that Linux for Dummies (both the standalone and 5 volume in 1) books are pulled off the shelf relatively frequently.  And then their is the O'Reilly series which is excellent, but I wouldn't start there.  Finally, just search the forums, people here are great...  [www.linuxquestions.org](www.linuxquestions.org) is also good.  Let me know how it's going...and have a blast.

---

