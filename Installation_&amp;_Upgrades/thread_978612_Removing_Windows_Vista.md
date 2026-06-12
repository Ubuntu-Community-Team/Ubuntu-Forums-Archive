---
title: "Removing Windows Vista"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by Elvish Legion on 2008-11-11
I installed Ubuntu (8.10) from inside windows vista and now I would like to remove windows vista. I was wondering if I just formated that partition if I could do that or would I have to reinstall everything since ubuntu was installed under windows

Thanks

---

### Post by phillik747 on 2008-11-11
> **Elvish Legion said:**
> I installed Ubuntu (8.10) from inside windows vista and now I would like to remove windows vista. I was wondering if I just formated that partition if I could do that or would I have to reinstall everything since ubuntu was installed under windows

Thanks

Is Ubuntu and Vista on the same hard drive? Can you please give a printout of```
sudo fdisk -l
```

---

### Post by Elvish Legion on 2008-11-11
> **phillik747 said:**
> Is Ubuntu and Vista on the same hard drive? Can you please give a printout of```
sudo fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475d475c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28876   231946438+   7  HPFS/NTFS
/dev/sda2           28877       30401    12249562+   7  HPFS/NTFS
jduvall@ubuntu:~$

---

### Post by phillik747 on 2008-11-11
This drive [dev/sda] doesn't have Linux on it from what I see.  If Linux was installed on that drive you would see:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fcf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris

```

If you just installed Ubuntu I would start over from the Ubuntu boot disk and format the entire hard drive if you truly want to get rid of Vista.
**THIS ACTION WILL DELETE ALL OF YOUR DATA** But if your ok with that its the easiest way to go.

---

### Post by kebin071 on 2008-11-11
I'd have to agree, if you want to get rid of Windows, a clean install is the best way to go.

It sounds like you used wubi, the ubuntu windows installer, that uses a virtual HDD on a windows partition.

I would suggest downloading either the 32bit or 64bit Ubuntu 8.04, since I've found 8.10 to be a little buggy. But if the wubi 8.10 has worked fine for you, use it.

I use the 64bit, but that's just me. If you want anti-virus, I'd use 32bit. Avast! [avast.com] has free anti-virus for windows and linux, but it works on 32bit only ATM.

Regardless, anti-virus mainly scans for windows viruses in files in linux, so it's not really a big concern unless you share a lot of files with windows users.

If you use MSIE in windows, you can download a free program to convert your MSIE favorites into an HTML file that you can later import into firefox once your linux is up and running. Can't remember the program name, but i used it back in the day.

Anyway, after you backup your files in windows, and when installing ubuntu, if you use the 'guided' partition arrangement, be sure it's going to use the entire drive, and not just unused space. If you do partition editor manually, I'd suggest using XFS file system; rather than ext3.

Unless you play a lot of different and numerous windows games, there is no advantage to using windows. Have fun!

---

### Post by Mark Phelps on 2008-11-11
Your initial post says it all -- you installed inside Windows (i.e., using WUBI), and thus NO you can not just reformat the partition to get Ubuntu, and YES, you have to completely reinstall.

---

