---
title: "checkdisk failure after resizing partition"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by Gwaap on 2007-07-08
I have resized my kubuntu partition with gparted. Now when I boot up I get a string of error messages about fsck failing before completing the bootup after pressing control+D.  Now also Kontact asks my pop3 password continually.  var/log file reads asfollows:

Log of fsck -C -R -A -a 
Sun Jul  8 15:26:14 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=07660736-5366-480e-b721-8a4a12437e51'
/: clean, 30836/1270464 files, 155098/2555904 blocks
fsck died with exit status 8

Sun Jul  8 15:26:15 2007

Any suggestions about how to fix this?

Thanks.

---

### Post by confused57 on 2007-07-08
> **Gwaap said:**
> I have resized my kubuntu partition with gparted. Now when I boot up I get a string of error messages about fsck failing before completing the bootup after pressing control+D.  Now also Kontact asks my pop3 password continually.  var/log file reads asfollows:

Log of fsck -C -R -A -a 
Sun Jul  8 15:26:14 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=07660736-5366-480e-b721-8a4a12437e51'
/: clean, 30836/1270464 files, 155098/2555904 blocks
fsck died with exit status 8

Sun Jul  8 15:26:15 2007

Any suggestions about how to fix this?

Thanks.
The UUID changed when you resized your partition...you need to determine the new UUID, by opening a terminal(Konsole?), enter:
```
blkid
```
this will show your current UUID's for your filesystems

You'll then need to open your /etc/fstab & /boot/grub/menu.lst, then copy & paste in the correct UUID's from the "blkid" command:
```
kdesu kwrite /etc/fstab
kdesu kwrite /boot/grub/menu.lst
```

You might want to create a backup before you edit your files:
```
sudo cp /etc/fstab /etc/fstab_backup
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

---

### Post by Gwaap on 2007-07-09
Thank you.  You put me on the right track.  Gparted seems to have corrected the numbers but it did not delete the hda1 partition in fstab that I deleted through Gparted.  Deleting that resolved the issue.  Thank you, I would not have been able to find it without your help.

---

