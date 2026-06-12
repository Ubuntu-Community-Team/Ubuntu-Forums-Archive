---
title: "Problems with double booting laptop"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by Rockman36 on 2010-02-09
Hi all!!  I have a dual boot laptop, with Windows Vista and Ubuntu 9.10, I had issues with Vista and had to reinstall it, in the process I lost GRUB (because of this I am not even sure that the Ubuntu install is still there), does anyone know what can I do to get GRUB to work again? Thanks!!!  Best Regards

---

### Post by raymondh on 2010-02-09
> **Rockman36 said:**
> Hi all!!  I have a dual boot laptop, with Windows Vista and Ubuntu 9.10, I had issues with Vista and had to reinstall it, in the process I lost GRUB (because of this I am not even sure that the Ubuntu install is still there), does anyone know what can I do to get GRUB to work again? Thanks!!!  Best Regards


Hello and welcome to the forums.

When you re-installed Vista, it (windows) overwrote the MBR with its' own bootloader.  Now, did you re-install Vista to the WHOLE hd or, did you re-install over the existing Vista?

Let's check:

-  boot into the liveCD and go live session (try ubuntu....)
-  access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

small L, not one (1).

Paste the results in your next post.

If you re-installed Vista OVER the existing windows partition, then all you have to do is re-install GRUB2.  [Instructions here]("http://ubuntuforums.org/showpost.php?p=7505203&postcount=1"), number 13.  Remember, after re-installing GRUB2, to do an update (just to be sure).  From terminal 

```
sudo update-grub2
```

Regards,

raymond

---

### Post by Rockman36 on 2010-02-10
Hi Raymond!!, thanks for your help!, followed your instructions sudo fdisk -land got this message:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa47a1f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18403   147819488+   7  HPFS/NTFS
/dev/sda2           18403       19457     8466432    7  HPFS/NTFS

Regards
Rodrigo

---

### Post by oldfred on 2010-02-10
Did you have a wubi install that was inside the windows partition. If so you seem to have overwritten it as you only have 2 windows partitions. wubi could be inside your second partition and then you may just need to update the widnows boot file to see it. Do you have root.disk somewhere?

Since it is wubi do not follow any directions for installing grub to the MBR. You still need windows boot loader in the MBR and then you choose windows or wubi.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by raymondh on 2010-02-10
> **oldfred said:**
> 

Since it is wubi do not follow any directions for installing grub to the MBR. You still need windows boot loader in the MBR and then you choose windows or wubi.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

@ OP,

as OldFred says, IF YOU HAD  A WUBI-INSTALLED ubuntu, do not follow the instructions to re-install grub as that will overwrite the windows bootloader.  Sorry to have linked it.  'wish I had know you may have had a wubi install.

Raymond

---

### Post by Rockman36 on 2010-02-10
It seems that will need to reinstall Ubuntu, oh well!!, thank you both for your help!!!

---

