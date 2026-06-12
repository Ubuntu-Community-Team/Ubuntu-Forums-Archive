---
title: "MBR messed up after ubuntu install"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by Narodigg on 2008-03-26
I installed Ubuntu on a secondary HDD from my XP install. 
However it seems that HDD also hosted my MBR for XP. 

When I boot up now I have the option to load either the XP or Ubuntu OS. 

When I select XP it says... 
<Windows root>\system32\hal.dll missing or corrupt:
Please re-install a copy of the above file.

What options do I have to fix this. 
I tried to install XP over top it self but it tries to make MBR changes to the HDD I install Ubuntu on and one untill it has some free space to do so.

---

### Post by Narodigg on 2008-03-27
Anyone have any ideas?

It seems my boot.ini and maybe the MBR or hal.dll was on the HDD that Ubuntu installed and it wiped them out.

---

### Post by az on 2008-03-27
If you installed Ubuntu to another drive, it would not have messed with those files.  The installer put GRUB onto the MBR of the first drive so that you can boot, but I don't think that error is indicative that the problem was caused by Ubuntu.  Unless you erased those files. 

Changing the MBR would not affect those files.  If windows is complaining that a dll is missing, that means that the bootloader can indeed boot windows.  But I don't know anything at all about Windows.

Are you certain you installed to the correct drive?

---

### Post by lswest on 2008-03-27
you can boot to the recovery console of an XP CD and do ```
copy [path to file*] [drive letter of your drive]
```

***path to the file on the CD, not the drive**

not sure where exactly the file would be on the CD, you'd need to google that, but once you do that it should work.

and, by the way, the error seems to be more windows-related, so you might get more information from a windows forum (i know replies take ages in most of them).  Also, if you google my suggestion it might give you the info you need. 

Hope I helped,
lswest

---

