---
title: "How do I completely uninstall Ubuntu 12.04"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by Ineed2know on 2012-05-29
:confused:  I have Ubuntu 12.04 installed on it's own partition. I set-up Ubuntu 12.04 to run "dual boot" with Windows XP Home (Windows XP Home w/SP3).  For reasons I don't want to get into here, I want to completely remove Ubuntu from my computer all together.  Because the dual boot feature is installed, how do I restore the boot record (MBR) for XP to before Ubuntu was installed?  I see something to the effect that I have to restore the "boot loader".  How do I do that?  As for removing Ubuntu itself, I believe all I have to do is just reformat the partition where Ubuntu is installed.  Please help.  I need exact step-by-step instructions please.  Thanks.

---

### Post by Megaptera on 2012-05-29
Guide with screenshots to fix mbr in xp [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

a method for removing Ubuntu (if you must!)  [http://opensource-sidh.blogspot.co.uk/2012/01/uninstall-remove-ubuntu-from-windows.html](http://opensource-sidh.blogspot.co.uk/2012/01/uninstall-remove-ubuntu-from-windows.html)

---

### Post by ajgreeny on 2012-05-29
If you don't have an XP installation disk you can do the repair of MBR with a live ubuntu cd.

Boot to live CD then ```
sudo apt-get install lilo
```Ignore the warning then ```
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot directly into Windows again if all goes well.

---

### Post by Ineed2know on 2012-05-31
:popcorn:  Thanks to all that responded.  All is well.  I did a wipe of the partition where Ubuntu was installed and was able to "fix" the mbr and boot using the Windows Recovery Console.  :smile:  There should be something in the user guides about uninstalling Ubuntu.  I didn't find anything in the 12.04 guide.  Just a thought.  Thanks.

---

