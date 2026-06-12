---
title: "problem after upgrde to 7.10 (fsck MANUALLY)"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by alivip on 2007-11-15
When I upgrade from 7.04 to 7.10 every thing is going fine Until system restart it give my this message
 File system check   UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

any one can help me to  solve this problem please

---

### Post by Herman on 2007-11-15
Certainly, it's very easy now if you have the Gutsy Gibbon Desktop (Live) CD.

Just boot your Ubuntu Live CD and open Gnome Partition Editor, go: 'System'-->'Adminstration'-->'Partition Editor', and start GParted.

When GParted is open, right-click on your Ubuntu partition and click 'Check; from the right-click menu.
The after you click 'Apply' up on the toolbar, you'll get a confirmation window, click 'Apply' on that. 
A new window should open and show a progress bar as the filesystem check is being done for you.
When it is finished you should click on the arrow buttons several times  to expand the window fully and read about what has happened.

When you are finished reading, close the window, close GParted and reboot,

If you don't have the Gutsy Gibbon Live CD, you can do the same thing with [GParted -- LiveCD]("http://gparted.sourceforge.net/").

Or, you can run sudo e2fsck -C0 -p -v -f /dev/hda2.
```
sudo e2fsck -C0 -p -v -f /dev/hda2
```
Where: /dev/hda2 is the partition designation for your Linux partition, (partition number 2), please replace /dev/hda2 with something else as needed to suit your own particular setup.
[                      Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

That's it, it should be fixed! :)

Regards, Herman :)

---

