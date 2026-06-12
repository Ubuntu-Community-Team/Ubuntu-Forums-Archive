---
title: "Problems partitioning hard drive"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by christopherbrown03 on 2013-11-04
Hello,
  I am completely new to linux and am just fed up with windows.  I am trying to install ubuntu 13.10 but I am having some problems with the installation.  When I get to the part where I am to select where to install ubuntu nothing comes up.  I assume this is because I have no unallocated space on my hard drive, but I cant seem to shrink the c drive for some reason.  When I try, windows says that there isn't enough available space on the drive, but there is definitely enough space.  Any help would be appreciated.  I did search the forum for this problem, but I didn't really get what they were talking about, so if someone could tell me step-by-step how to do this, I would really appreciate it.  here is a screen shot of my disk manager:

[ATTACH=CONFIG]247562[/ATTACH]

Thanks again for any help.  Also, I am trying to do a dual boot with windows 8, that is probably important here.

Edit: Also, my hard drive is GPT, so shouldn't I be able to do as many partitions as I want?

---

### Post by ajgreeny on 2013-11-04
Your screenshot from Windows is not very helpful.  Can you run the live ubuntu system and get a screenshot from gparted which you will find available on the DVD/USB already, as it gives much more usable info about partition types which is not showing from your picture.

You seem to have a strange assortment of partitions, though the first 5 listed are not even formatted according to Disk-management, but to answer your query; Yes, you can have as many partitions as you are ever likely to need on a GPT partitioned disk

Baffling to me at present, so let's have more info from a "proper" partition-manager (gparted) please.

---

### Post by christopherbrown03 on 2013-11-04
Thank you the reply!  Sorry it took so long to get this, but here it is:

[ATTACH=CONFIG]247573[/ATTACH]

Note:  When I opened gparted, it asked me to apply a couple of fixes by moving the backup image for (I am assuming) windows, and freeing up some space that it said the disk previouslly couldnt get to.  I applied the fixes, and I am going to pop back over to windows to see it it lets me partition the hard drive there.  I would do it in ubuntu, but I have no idea how to do it.  Thank you again for the reply.

---

### Post by oldfred on 2013-11-05
Do not use Windows to create partitions, it may convert to dynamic or LDM partitions even with gpt. And dynamic does not work with Linux, and some Windows tools.
Do use Windows to shrink the main Windows or c: drive to make unallocated space for Ubuntu to install into. Reboot so Windows can run chkdsk or make whatever repairs it likes to do on a partition size change.

Make sure fast boot is off. Does your Windows boot with secure boot off? Most but not all do.

Lots of links on installing with UEFI in the link in my signature. Be sure to review the first couple.

---

### Post by christopherbrown03 on 2013-11-05
Thank you both for the help, I was able to finally get ubuntu installed and working (I did the partitioning in live boot gparted), with secureboot on.  I am sure I will back on the forums as I begin the process of how to use this monster.  Thanks again.

---

