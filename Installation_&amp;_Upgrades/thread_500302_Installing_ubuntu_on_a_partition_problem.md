---
title: "Installing ubuntu on a partition problem"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by ruku on 2007-07-13
I'v installed ubuntu before using an older version and it seememd a lot easier. I'v created a partition of 105gb for the ubuntu installation, popped in the disk that has no errors, ran into live and i continued to install from there using the correct partition etc. i finish the install and restart the machine, but it just boots straight to windows.

Now when i load windows and check to see if the partition is still there its magically dissapeared from my computer, i check in administration tools and its still picking up the partition but now as unknown space. so iv had to reformat the partition and go through the process again, but it did the same thing again.

Does anybody have any suggestions as the what the problem may be?

regards in advance

---

### Post by merlinus on 2007-07-13
I may be mistaken, but windows will not recognize a linux-formatted partition without the ifs drivers, so that is not a good way to find out what is happening.

My guess is that for some reason grub was not installed correctly, and so its menu is not appearing on boot-up.

What version of windows are you using?  How did you partition your ubuntu drive?  How is it formatted?

SuperGrub should allow you to boot into ubuntu, and then reinstall grub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by ruku on 2007-07-13
I'm currently using windows xp pro, sp2 all up to date etc.

i partitioned the hdd in windows on disk manager. This was a straight partition and format in ntfs as a primary partition.

from there i installed ubuntu to this partition but as you said it seems that grub isnt creating a bootmenu as such, it just boots normally to windows as if the ubuntu partition is non existant.

As i say i have installed ubuntu before and didnt have this problem :s

---

### Post by merlinus on 2007-07-13
When you installed ubuntu, did you specify how the partition should be formatted (e.g. ext2, ext3, reiserfs)?

If not, that may be the problem.  ntfs is for windows; the others are for linux.

If ubuntu did install correctly, then SuperGrub will allow you to boot into it to make sure, and allow you to reinstall grub as well.

The url in my last post gives excellent information and instructions, thanks to Herman!

Good luck!

-merlin

---

### Post by Pumalite on 2007-07-13
Defrag you Windows several times, erase all temp files, get rid of anything you don't need, BACKUP all your data. Then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Partition your hardrive, you might want to format ext 3 prior to install even though it's not necessary. Install Guided>Largest space available. Try Merlinus solution first. If your system is not there, then try mine ( Ubuntu cannot install or function on an ntfs formatted partition ).

---

### Post by ruku on 2007-07-13
Yes when i installed ubuntu i specified it to be ext2.

I shall look into supergrub and see whats what :P and try and report back as to why the boot loader isnt showing :S

---

