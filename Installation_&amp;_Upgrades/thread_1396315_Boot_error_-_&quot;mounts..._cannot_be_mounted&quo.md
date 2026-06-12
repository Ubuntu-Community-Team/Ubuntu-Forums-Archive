---
title: "Boot error - &quot;mounts... cannot be mounted&quot;"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by Starman~ on 2010-02-01
I just reinstalled my windows partition from a backup image. Following that the Grub2 needed repair. That was accomplished and the grub2 menu along with the changes I made (to the grub screen) come up just fine. I can select my Windows 2K installation and it boots okay.

when I select the "Linux 2.6.31-17-generic" the boot process appears to begin normally with the Ubuntu symbol shown, but at some point the screen goes blank and the boot process stalls. recovery mode gives me a jumbled up recovery menu. Alt-Ctrl-Delete gets me out of either.

If I boot from the previous "Linux 2.6.31-14-generic", I´m receiving this error during boot-
> "One or more of the mounts listed in etc/fstab cannot be mounted"

There are subsequent screens that warn I'm running in "low graphics mode", but I can boot to a somewhat functional system. I was able to boot it once, but get the same results with either kernel

There is  a difficult to read message in the jumble of the recovery menu.
> "One or more of the mounts listed in etc/fstab cannot be mounted. Swap: waiting for UUID=35b77xxxxxx"

Any ideas? I'm not sure how to troubleshoot the problem, or what steps to take to resolve it.
Can you please assist. Still learning linux, the hard way.

---

### Post by Starman~ on 2010-02-02
I'm going to call this solved. It may be a first for me.

The problem was that the UUID of the swap partition changed. It happened sometime during the restoring the image or restoring the Grub2.

The solution was to boot the live CD and run ```
# Sudo blkid
```
out put gives you the UUID of each partition. Compare this to fstab in root partition. 

On mine the swap UUID was no longer the same. With the "filesystem" mounted I edited the fstab to match the "blkid" output. 
Booted right up afterwards. Still testing but eerythig seems to be in order.
The question remains, "How can partitions be restored without all the headaches?"

---

