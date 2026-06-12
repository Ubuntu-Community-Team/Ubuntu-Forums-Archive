---
title: "Upgrade from 8.04 to 10.04 resulted in &quot;no such partion&quot; by grub"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by highcc on 2010-05-12
Hi,

I've upgraded my Desktop 8.04LTS to 10.04. I've forgot to follow the instruction to update grub ([http://www.ubuntu.com/getubuntu/releasenotes/1004#Switching%20to%20ext4%20requires%20manually%20updating%20grub](http://www.ubuntu.com/getubuntu/releasenotes/1004#Switching%20to%20ext4%20requires%20manually%20updating%20grub)) before rebooting the system, so now grub won't boot my ubuntu partition ("no such partition"), only Windows.

I've 3 SATA Harddrives:
1-80GB with Ubuntu and grub
2-80GB with Windows XP and it's own MBR
3-250GB with one FAT32 and one NTFS partions, both for bkp purposes.

I've booted a 10.04 system with a usb drive and I can't see Windows or Ubuntu through the disk utility! Only the 250GB disk. I can't mount the partitions through terminal too.

Now how can I update grub if I can't chroot to my system?

Thanks in advance

---

### Post by sedawk on 2010-05-12
What is confusing me is that is saying "RAID" in the
screenshot. I wonder if that is related to a software
raid or if the system thinks your two 80 GB disks
are configured as a raid on system level (e.g. via BIOS).

Have you played around with RAID settings features somewhere?

---

### Post by darkod on 2010-05-12
If the disk was used in RAID earlier it would have metadata remains. This was not a problem until 9.10 when it started detecting them and considers the drive as part of raid.

If you are NOT using raid, remove metadata settings with (you can do it from live mode too if you can't boot the ubuntu):

sudo dmraid -r -E /dev/sda

See if that solves it. Not sure if you would need to chroot and update-grub after, we'll see.

---

### Post by highcc on 2010-05-14
Man, I didn't remember of that, but now that you said I remember. Yes, I've used those disks as a software RAID0 with Debian when I bought'em. That's pretty much around 2007. Since 2008 I've been with ubuntu on the first disk and WinXP on the second. First I've formatted both, installed XP and Ubuntu 7.10 and then upgraded to 8.04. Nothing has changed since then.

I've removed the metadata as Darkod suggested. Then the partitions were recognized.

I've mounted and chrooted the HD system. I was noobing with GRUB and so decided to go with GRUB2. I've installed GRUB2 from the live system itself
```
sudo grub-install --root-directory=/mnt /dev/sda
```
as mentioned in ([http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)) chapter 13. It installed with no errors, but without my configs :mad:. From the same guide, chapter 15 I've booted from the rescue mode and now it worked... frustration... the update has only did a partial installation and now it's all lost. Don't boot anymore:(.
I'm not too worried because I've backups of the two 80GB disks.

Someday I'll do a fresh install of Win7 and Ubuntu 10.04, for now I'll stand with my notebook.

Well, thanks for the help guys. It didn't work but it's not your fault. 

See you.

---

### Post by darkod on 2010-05-14
If you previously had grub1, grub2 has no config files to use. It doesn't necessarily mean the insllation is messed up.

Since you know how to chroot, try creating the new config files with (do the necessary steps before that):

chroot /mnt grub-mkconfig

You should have waited and see if it will boot with grub1. Now we don't know if the upgrade was really messed up, or just grub2 doesn't have the config files to boot it.

---

