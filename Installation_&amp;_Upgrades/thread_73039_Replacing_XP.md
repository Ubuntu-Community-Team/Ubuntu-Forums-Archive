---
title: "Replacing XP"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by Aeternvs_Lamia on 2005-10-08
Ok, so as a pre...thing...I know very little about computers, but anyways.
I'm currently using Windows XP with a Compaq Presario SR1210NX, and have the 5.04 CDs, but at the moment my CD drive isn't being recognized, and in place of my D drive I have a partition of some sort, so does anybody have any tips on how I can either A)Simply install Ubuntu without bothering fixing the windows problems, or B)fix the windows problems...
Any help is greatly appreciated
Thanks

---

### Post by Leif on 2005-10-08
see if one of the methods listed here do the trick : [https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

---

### Post by kondor on 2005-10-08
1. Have you made any Windows Restore CDs yet? That is what the D Windows drive is for, it contains your HP/Compaq Restore software that will reinstall windows if you need it. I would recommend making the Restore CDs before you play much more. If you format that partition, you'll have to buy the Restoration Discs.

2. If you want to get rid of XP, you can format the C Drive, which will show up as a NTFS partition. The D drive will show as a FAT32 partition and you can simply leave it as it is if you like. The D drive is likely somewhere around 8MB

Or, if you never want Windows again, you can simply let Ubuntu have both partitions, that is the entire drive. Once the drive is formated, windows is gone.

You may have already wiped something out, can't tell from you post.

If your computer is still in warranty, you might want to think twice about dumping Windows entirely. Not that an HP warranty is worth all that much (I've been through that). You can easily boot WinXP and Ubuntu on the same drive. There are many discussion on this forum about the procedure.

But, again, the D drive (that FAT32 partition that shows up on the Unbuntu install) is where your Restoration software resides.

---

