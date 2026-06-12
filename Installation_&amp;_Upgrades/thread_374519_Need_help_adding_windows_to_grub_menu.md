---
title: "Need help adding windows to grub menu"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by themoonshake on 2007-03-02
i have a dell desktop with 20GB hd on which i was running edgy. i needed to add windows xp to the machine, so i used gparted live cd to resize the partition and gave 6GB ntfs for my windows install. i succesfully installed xp on it. i then reinstalled grub as described here [http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

i was under the impression that doing this will automatically add windows to the grub menu but it didn't in my case. then i tried adding this to menu.lst manually:

```
title		Windows XP
rootnoverify	(hd0,0)
makeactive	
chainloader	+1
```

but when i choose windows xp, it gives me **[COLOR="Red"]"error 13: invalid or unsupported executable format"[/COLOR]**. ubuntu still boots without a hitch.

my partition looks like this:

```
Disk /dev/hdc: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1436    11534638+  83  Linux
/dev/hdc2            1437        2221     6305512+   7  HPFS/NTFS
/dev/hdc3            2222        2482     2096482+   5  Extended
/dev/hdc5            2222        2482     2096451   82  Linux swap / Solaris
```

what do i do with menu.lst to make windows working?

---

### Post by themoonshake on 2007-03-02
figured it out.. was something very simple. :)

just needed to change (hd0,0) to (hd0,1), since my windows install in the first disk's second partition.

---

### Post by Herman on 2007-03-02
Hello themoonshake,
Yup, I was just about to post you and explain that. Glad you solved it. Grub is easy enough to work with.
> i was under the impression that doing this will automatically add windows to the grub menu but it didn't in my case. When Windows and any other operating systems are installed before Ubuntu, grub does usually detect them and  it automatically configures the boot entries for them. 
You installed Ubuntu first and then you installed Windows, that's why you had to enter yours manually. 

Regards, Herman :)

---

