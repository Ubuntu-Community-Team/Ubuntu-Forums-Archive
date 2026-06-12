---
title: "Changing drive mount point confuses Nautilus"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pertti on 2010-04-14
I'm running an up to date version of Lucid and I have noticed a problem I didn't have before regarding setting mount points of internal drives.

First of all, before Lucid I was able to set the mount point through the properties dialog of the drive in Nautilus. With the deprecation of HAL this feature is gone (or at least I don't see a replacement), so I have to resort to the old trusted /etc/fstab file.

So I edited fstab and added the following line:

```
UUID=170727c3-46e3-48d2-a522-1ad7af6fbfaa       /media/data ext3    user,nosuid,nodev 0 0
```

Now I can mount my drive from the command line, and it also shows up in the Places menu and Nautilus sidebar.

However, if the drive is not mounted and if I click on "data" in Nautilus or in Places the operation times out and nothing happens. Nothing? No! The drive gets mounted on /media/datos. If I click on "data" when it's already mounted, a pop up dialog tells me that it wasn't possible to mount that drive and that it was already mounted on /media/datos (fine! then just open the window!). Meanwhile, I can enter /media/datos from the command line and see its contents.

But it gets weirder. In addition to "data", I still have the old "80 GB filesystem" entry in Places and in the Nautilus sidebar. Clicking on it opens /media/datos, as can be seen on the location bar if a press Ctrl+L.

So it seems that Nautilus gets confused by this new mount point, but is able to access the drive using the old name. A bit annoying. Does anybody else have this problem? Any ideas on fixing this? Should I just change the drive's label and hope that Nautilus picks it up?

Thanks in advance

---

### Post by Quikee on 2010-04-14
gnome-disk-utility is the replacement (in administration/disk utility if you have it installed). Change the filesystem label of the volume an it will mount accordingly (I have tested it now and it works). 

fstab is only good for mounting drives that need to be mounted on system start and is not intended to mount drives into /media.

---

