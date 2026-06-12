---
title: "Ready to Drop Windows!"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by MSchenker on 2007-11-04
Hello,
OK, I have been running a dual-boot system, but now I'm ready to let Kubuntu be my full-time operation system.

How do I get rid of the Windows partition and let Kubuntu use my whole hard drive?  Is there some kind of Linux application that does this?

I could reinstall the whole thing, but I have spent a lot of time getting all the settings correct and don't want to redo it now.

Thanks,
Matt

---

### Post by American_Outcast on 2007-11-04
Use a livecd, the Kubuntu/Ubuntu one or Gparted, etc. You can delete the windows partition and then resize the Ubuntu partition. There is always a chance that you could loose data or something can get messed up. So make sure you back up all of your important info just in case.

---

### Post by aysiu on 2007-11-04
If, when you set up the dual boot, you went with the default installation options, then Kubuntu's Grub boot loader will be installed to the Master Boot Record, which is a good thing. If you did some complicated workaround to keep Windows' boot loader on the MBR, then it'll be a little more complicated. We'll assume you went with the default, though.

First, change your settings so that partitions and drives are not automatically mounted.

Second, install (using Adept or *apt-get*) QTParted.

Run QTParted and delete the Windows partition. Then format it as Ext3.

Follow [this tutorial](http://www.psychocats.net/ubuntu/mountlinux) to make the freed-up space easily available.

Then change the settings again so that partitions and drives are automatically mounted.

---

### Post by MSchenker on 2007-11-04
American_Outcast and aysiu,
Thanks for your help.  But these instructions are confusing to me.  I deleted the Windows partition in QTparted, and I created a new partition with that space.  That worked fine.

But QTparted will not let me format the new partition as EXT3.  Also, I don't see any way to resize the existing Kubuntu partition so it takes the space of the new partition (the one that used to be Windows).

I installed Kubuntu using the "guided, largest continuous free space" option.

Correct me if I'm wrong, but it seems that it might be easier for me to just re-install Kubuntu from scratch.

Thanks,
Matt

---

### Post by American_Outcast on 2007-11-04
> **MSchenker said:**
> American_Outcast and aysiu,
Thanks for your help.  But these instructions are confusing to me.  I deleted the Windows partition in QTparted, and I created a new partition with that space.  That worked fine.

But QTparted will not let me format the new partition as EXT3.  Also, I don't see any way to resize the existing Kubuntu partition so it takes the space of the new partition (the one that used to be Windows).

I installed Kubuntu using the "guided, largest continuous free space" option.

Correct me if I'm wrong, but it seems that it might be easier for me to just re-install Kubuntu from scratch.

Thanks,
Matt


If you don't mind doing that, it may be the best way to go until you get use to it some more. It does take some time just to get comfortable with Linux when you are use to Windows only.

---

### Post by MSchenker on 2007-11-04
American_Outcast,
I'm comfortable in Kubuntu -- so comfortable that I'm ready to drop WIndows.

My real question is, what's the easiest way to get rid of a dual-boot system and just let Kubuntu be the only operating system?

Thanks,
Matt

---

### Post by MSchenker on 2007-11-05
Just wanted to finish out this discussion...
This morning, I just reinstalled Kubuntu again, from the Live CD. I just told it to install using the whole drive, and now everything is fine.  I had to go through all my settings again, but it was less time that playing with existing partitions.
Matt

---

