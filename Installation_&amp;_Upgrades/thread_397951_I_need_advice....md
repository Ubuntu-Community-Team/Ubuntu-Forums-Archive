---
title: "I need advice..."
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by javi0084 on 2007-03-31
I want to dual boot XP and Ubuntu. XP is installed on the 228GB partition and the 5GB under it is the recovery for Windows (see attachment, I hope it uploaded). If I leave the mount points like that for Windows, will I lose any data? I have lots of GBs worth of pictures and music that I haven't had time to backup and I don't want to lose any of that.

For Ubuntu, I want to install it on the 15GB partition and use the 92GB partition to share files between Windows and Ubuntu, What changes do I need to make to that? Thanks!!

---

### Post by cantormath on 2007-03-31
> **javi0084 said:**
> I want to dual boot XP and Ubuntu. XP is installed on the 228GB partition and the 5GB under it is the recovery for Windows (see attachment, I hope it uploaded). If I leave the mount points like that for Windows, will I lose any data? I have lots of GBs worth of pictures and music that I haven't had time to backup and I don't want to lose any of that.

For Ubuntu, I want to install it on the 15GB partition and use the 92GB partition to share files between Windows and Ubuntu, What changes do I need to make to that? Thanks!!

install the windows normally(which is sounds like you have), then install ubuntu, you can use the installation scripted to  adjust the size of the hardrive you want for ubuntu.  Ubuntu install will see the windows install, and add it to the master boot record so that when you reboot the machine, it will ask what you want run.

I recommend, before you do the ubuntu install, you defrag your windows machine.

You will need to resize the windows disk, to whatever size you want it, then when you install ubuntu, dont choose entire disk, you want to install it on next largest section of empty disk.  The unbuntu installer will then partition that section of the empty disk you saved for ubuntu property to run linux.

Here is a tutorial 
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo)

once you get the dual boot working, you are gonna want to use NTFS-3g to access and write to the windows partition.  Make sure you use there repo to update and install, its more upto date , IMO.

Hope this helps.

---

### Post by dreadlord_chris on 2007-03-31
> **javi0084 said:**
> I want to dual boot XP and Ubuntu. XP is installed on the 228GB partition and the 5GB under it is the recovery for Windows (see attachment, I hope it uploaded). If I leave the mount points like that for Windows, will I lose any data? I have lots of GBs worth of pictures and music that I haven't had time to backup and I don't want to lose any of that.

For Ubuntu, I want to install it on the 15GB partition and use the 92GB partition to share files between Windows and Ubuntu, What changes do I need to make to that? Thanks!!

**/** is the Mount Point for your *root* partition, i.e. where Ubuntu gets installed. From that pic your **/** is pointing at your 92GB partition - you need to point it at the 15GB one.

For the 92GB one, under **Mount Point** type something like **/media/share**

---

