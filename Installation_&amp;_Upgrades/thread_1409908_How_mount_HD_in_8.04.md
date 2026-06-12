---
title: "How mount HD in 8.04"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2010-02-18
I moved 4 HHD on an ATA-card to a new Ubuntu 8.04 machine. The are in a NFS network. I have called them 280GB_C, 280GB_D, 280GB_E and 100GB_F from before Dapper and to Hardy. Now when I tried to mount them from Desktop on the disks mounted on the desktop, by right-click -->Properties -->Volume. And fill out a new mountpoint in my homedirectory. (/home/Azyx/280GB_C corrensponding to the disk. Also make folder on that place.

After reboot i get the message "Cannot mount the volume"

-details:
"mounting_point cannot contain the following charter: newline, G_DIR_SEPARATOR (usually /)"

How fix it now? I can't get 'Property' on the disk cos they are not mounted anymore.

I have booth ext3 and reiserfs on the disks.

Edit: I think the problem is the name on the disks. 280GB_X, the underline. But where can i change it? There are nothing in fstab or mtab about the mounting point.

/Cheers

---

### Post by ajgreeny on 2010-02-18
Have you actually made the mountpoint folders in your home to mount them to?  If not they will not mount, and you can not make such a folder by using the Properties->Volume tab, you will have to do it by either right clicking on the parent folder and choosing "Create Folder" or in terminal ```
mkdir /home/Azyx/280GB_C
```
I don't think the underscore should be a problem at all in file or folder names, so forget about that; in fact it is always worth using an underscore rather than a space in a name, as it makes life easier when using pathways in terminal.

---

### Post by Azyx on 2010-02-18
> **ajgreeny said:**
> Have you actually made the mountpoint folders in your home to mount them to?  If not they will not mount, and you can not make such a folder by using the Properties->Volume tab, you will have to do it by either right clicking on the parent folder and choosing "Create Folder" or in terminal ```
mkdir /home/Azyx/280GB_C
```
I don't think the underscore should be a problem at all in file or folder names, so forget about that; in fact it is always worth using an underscore rather than a space in a name, as it makes life easier when using pathways in terminal.

Yes. I know that and have also mkdir for all 4 disks :) If that was the problem the message should be something like ..missing mounting point or so...

I thougt the GUI preferens maybe write the mounting point in fstab or so...but I can't find it there. Maybe I heve type some wrong, but I can't find what I wrote

---

### Post by Azyx on 2010-02-18
I made an mounting thrue fstab and it worked, and change _ to - in disk names...

---

