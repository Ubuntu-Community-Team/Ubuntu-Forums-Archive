---
title: "Repaired Vista Loader/No GRUB"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by RandomUsr on 2007-09-03
Had to repair the Vista Loader after re-installing XP, now I can boot Vista and XP, but not Ubuntu and OpenSuse which are also present.

Would someone be so Kind as to help me install GRUB from the Alternate CD so I can boot all OS's again?

---

### Post by merlinus on 2007-09-03
Try this:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).

-merlin

---

### Post by logos34 on 2007-09-03
['Using the Ubuntu Alternate/Install CD']("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-ec3e41291c7a5a7b61d7827299415204067765de")

(except use '$ grub-install /dev/hda' if you want to overwrite the vista bootloader on the mbr)

---

### Post by merlinus on 2007-09-04
Hi logos34.  So the "usual" way to restore grub will not work if the vista bootloader occupies the mbr?

-merlin

---

### Post by logos34 on 2007-09-04
> **merlinus said:**
> Hi logos34.  So the "usual" way to restore grub will not work if the vista bootloader occupies the mbr?

-merlin

Hi merlinus,

Looks like we posted our replies seconds apart.  

I thought he wanted to use the Alternate CD.  The usual way (from live cd) works too.

---

### Post by RandomUsr on 2007-09-04
OK so, just want to make clear. When I install the Grub to the MBR (superblock) then Vista Loader either gets moved foward of the Grub on that same Disk, or does the Vista Loader get moved to the MBR (non-superblock) of the Vista disk/partition?

---

### Post by logos34 on 2007-09-04
> **RandomUsr said:**
> OK so, just want to make clear. When I install the Grub to the MBR (superblock) then Vista Loader either gets moved foward of the Grub on that same Disk, or does the Vista Loader get moved to the MBR (non-superblock) of the Vista disk/partition?

The vista boot loader on the MBR doesn't get moved anywhere--Grub overwrites it.  Grub then chainloads Vista Boot Manager on the windows system partition (C: ).

---

### Post by RandomUsr on 2007-09-04
That makes perfect sense thank you. any method above preffered pver the other?

---

### Post by logos34 on 2007-09-04
> **RandomUsr said:**
> That makes perfect sense thank you. any method above preffered pver the other?

Either way works fine.  More people use the method in merlinus' post #2 above simply because more people use the live cd.  You specified the alternate cd so I posted that method.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

