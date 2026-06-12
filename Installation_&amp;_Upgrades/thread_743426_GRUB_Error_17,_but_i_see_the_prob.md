---
title: "GRUB Error 17, but i see the prob"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Barabbas on 2008-04-02
Hey when I went to install XP on an existing partition it told me it was unknown, so I used the LiveCD to format the foleformatting on the partition to NTFS, i rebooted and grub gave me error 17.

Now I changed everything back to Ext2 for the xp parition and now get an error 15. 

... Can I remove Xp from the grub loader, then add xp back to it once i finished the installation?

---

### Post by mikewhatever on 2008-04-02
Try here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

Can you also post the output of <sudo fdisk -l>.

---

### Post by Barabbas on 2008-04-02
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11744    94333648+  44  Unknown
/dev/sda2           11745       30027   146858197+  83  Linux
/dev/sda3           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Can I remove the xp partition from the bootloader and then add it back once I install it properly?

---

### Post by mikewhatever on 2008-04-02
> **Barabbas said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11744    94333648+  44  Unknown
/dev/sda2           11745       30027   146858197+  83  Linux
/dev/sda3           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Can I remove the xp partition from the bootloader and then add it back once I install it properly?

Sure. Delete it from /boot/grub.menu.lst and /etc/fstab. After you are done reinstalling Windows, you'll have to restore GRUB boot loader.

---

### Post by Barabbas on 2008-04-02
Yeah, so i go into terminal and type" /boot/grub.menu.lst" then /etc/fstab?


When i did that i got a blank page

Wait, where to access this? step-by-step help maybe?

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```
can't find grub file

I'm in the boot folder, but no grub file..

I think my grub has been deleteed? Should i use livecd to reinstall it?

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11744    94333648+  44  Unknown
/dev/sda2           11745       30027   146858197+   7  HPFS/NTFS
/dev/sda3           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

```

---

### Post by Barabbas on 2008-04-02
Can anyone help? I'm thinking about just instllating xp on the ntfs, then it should update the mbr to load it self. But I'm still waiting for someone to help me with GRUB and take it off, or the xp partition from the menu. Please I seriously need this help.

---

### Post by mikewhatever on 2008-04-03
> **Barabbas said:**
> Can anyone help? I'm thinking about just instllating xp on the ntfs, then it should update the mbr to load it self. But I'm still waiting for someone to help me with GRUB and take it off, or the xp partition from the menu. Please I seriously need this help.

If you do not have menu.lst file, then there is nothing to edit. Reinstalling GRUB at this point does not make much sense, because Windows installation will overwrite it from the MBR and you'd have to reinstall again. I'd suggest the following procedure:
1. Install XP.
2. Restore GRUB using a Live CD.

---

