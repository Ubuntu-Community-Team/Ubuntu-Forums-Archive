---
title: "Windows Linux PArtitions messed up"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by Bobobrien92 on 2008-01-21
I installed a new hard drive on my computer and i installed linux.  I kept windows xp pro on one and linux ubuntu on the other.  WHen installing i said use whole second disk and left my first disk untouched.  For the first two boots i could go into xp and it would say something about chkdisk but it worked so i didn't do anything.  However, now i can't boot into windows.  Whenever i try to boot from it in grub my screen just turns black and stalls.  i really want to keep my data on it because it has a lot of music and videos on it and i want them back.  any help would be great.  thank you.

---

### Post by pollywog on 2008-01-21
Don't worry too much about the data on your windows partition, It's probably Ok. To get access to it you could try the disk mounter utility. Add it by right clicking on you panel over somewhere to the right of applications/places/system. Select "add to panel", find & select disk mounter and click "add".  There's several ways to permanently mount a partition too such as the method shown here:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28partitions%29%7C%28mount%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28partitions%29%7C%28mount%29)

Then you can access your data, and save it as you see fit, just to ease your mind. As far as fixing GRUB, you might try downloading, and burning the free bootable bootloader utility "SuperGRUB":

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

You may be able to boot directly to windows to be sure that all is well there, but beware, if you choose "Fix boot of windows" option, it'll erase Grub, and all you'll have left is windows bootloader. There is a utility on that disk to reinstall grub as well. Worth a shot. You might also check in your BIOs setting to verify that the windows disk is activated.

---

