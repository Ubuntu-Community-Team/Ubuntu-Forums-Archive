---
title: "Dual boot problem--where's my options?"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by tarahmarie on 2010-05-07
Hi!

Ok, so I decided to get brave and install Mandriva on the 10GB partition I'd been saving up for a rainy day.  Mandriva uses KDE by default, so while I mounted the /home, I created a new username so that I wouldn't nuke my current Lucid Kubuntu settings.  It's all good; my data from my other username is in /home and I do like Mandriva. Here's the issue. 

My Mandriva install is at / in the extra partition I created when I partitioned this drive.  Kubuntu is my default OS, and when I installed it, I mounted this extra partition at /altos so I could look at it (I presume when I boot back into Kubuntu that all the Mandriva goodness will be there for me to poke about in as well).  

Where is my boot option?  I am not good with the Grub--why don't I have an option to boot into Kubuntu or Mandriva? Mandriva is playing like it's my default OS; I never see an option to boot into Kubuntu.  Do I need to edit my Grub?

I'm going to cross post this at the Mandriva forum too--maybe they know what up.

Thanks!

---

### Post by oldfred on 2010-05-07
Usually the last install takes over control of the MBR unless you specify as part of the install. What boot loader does Mandriva use?

Ubuntu with grub2 finds other installs very easily, but you would have to reinstall grub to the MBR. You may be able to add Ubuntu entries to Mandriva's boot but if you used EXT4 not all grub legacy (0.97) versions support it.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by tarahmarie on 2010-05-11
I have found and successfully configured grub from within Kubuntu.  Now, I have multiple boot entries in the grub menu. Kubuntu boots just fine (it lives on partition sda6), but Mandriva will not boot (it lives on sda7).  

Mandriva will not boot from grub, though. I have Mandriva set to boot in verbose mode, and here's what happens.  When I try to boot from grub (the entry is after the memtest entries, and just reads linux/sda7), the verbose boot mode for Mandriva begins, and it tells me that it cannot find the root partition.  I can't get a screenshot, but to the best of my memory, it says something like:

VFS: no root partition found, cannot mount UUID=[sda uuid here]. Please specify root=
kernel panic blah blah blah...

When I installed Kubuntu, I set up these partition mount points: sda1 = /home, sda2 = swap, sda6 = /, sda7 = /altos.

When I installed Mandriva, I set up these partition mount points: sda1 = /home, sda2 = swap, sda7 = /

First, I installed Mandriva to sda7, and then Kubuntu wouldn't boot.  Then, I reinstalled Kubuntu to sda6, and Mandriva wouldn't boot. WTH? Both distros are using grub2.  At least now I have a grub menu coming up so I can select my OS, but only Kubuntu will boot.  

Have I done something wrong by making both sda6 and sda7 mounted at / for each OS?

---

### Post by oldfred on 2010-05-11
So we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

