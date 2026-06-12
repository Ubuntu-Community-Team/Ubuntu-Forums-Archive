---
title: "Uninstalling Ubunto..."
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by rolltoheaven on 2010-01-04
I just installed Ubunto 9.2 from the original Ubunto CD. I installed Ubunto without making any partision that is side by side with boot up option in the beginning. The problem is my Ubunto system doesnot have any free space to use while window 7 has 220 GB free space. I was planning to allocate 100 GB for ubuntu and 100 or 120 for windows. I tried to look at in windows C: drive if I could found where Ubunto is and unistall from there but I have no idea where is ubunto sitting. So I want to either Uninstall Ubunto and reinstall after making partision or is there anyway I can increase some space for Ubundo without uninstalling it. Your help gonna be appreciated...

---

### Post by mkoehler on 2010-01-04
I'm not really following what you said.  You installed Ubuntu - did you do it on windows using the Wubi installer or did you boot into the live CD and install from the menu that was presented to you?  If you did the latter, you would have had to partition your hard drive (even if it was unknown to you).  If you're looking to resize these partitions, you can defrag your windows installation, boot into the live cd, then use gparted to resize the partitions.

---

### Post by prshah on 2010-01-04
> **rolltoheaven said:**
> I installed Ubunto without making any partision 

 is there anyway I can increase some space for Ubundo without uninstalling it. 

You can uninstall Ubuntu from the Add/Remove Software option (or equivalent) in the Windows Control Panel.

Or you can use [LVPM (Loopmounted Virtual Partition Manager)]("http://lubi.sourceforge.net/lvpm.html") to change the size of your wubi ("within windows") install and/or to transfer your existing install to it's own dedicated partition. Exhaustive details (including screenshots) are available at the link, but feel free to post back here if you have doubts or comments.

---

