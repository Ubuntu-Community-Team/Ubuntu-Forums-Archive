---
title: "Removal of old kernels after update"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Euphorion on 2008-06-26
Hallo

After a while, as a result of Kernel updates, the system collects a lot of Kernels which are no longer required, these are visible in Grub.

Within this Forum the following solution was posted, "Go into Synaptic and use the remove completely option for the older versions of the kernel. Start with the oldest one at a time. That will also clean up many other files in / and the grub entries."

This method apparently works fine, except for one small flaw, see [http://ubuntuforums.org/showthread.php?t=817852](http://ubuntuforums.org/showthread.php?t=817852).

Synaptic cannot remove the /lib/modules/2.6.22-xx-generic directories, whereby xx refers to the version to be removed. This can be seen by opening the details window in the graphical version of synaptics. Trying to remove these directories by hand fails owing to lack of permission and is owing to the large number of directories a tedious task to say the least. The directories contain predominately links. I do not quite see as to how the creation of an empty directory as suggested in a post attached to the above thread solves the fundemental problem of removing the directories containing the links.

Does anybody have a solution to this or can explain as to why synaptics is not allowed to remove the directory trees and as to whether it is prudent to remove them by hand with administrator rights.

Thanks in advance

---

### Post by Rocket2DMn on 2008-06-26
You should be able to search in Synaptic for "linux-image" then mark each one you want for Complete Removal (right click it).
Alternatively, you can edit your GRUB menu.lst file to only show a specific number of kernels
```
gksudo gedit /boot/grub/menu.lst
```
Find the line that says "# howmany=all" and change it to something like "# howmany=3"
Save and close, then, to clean up your GRUB menu, run
```
sudo update-grub
```

---

