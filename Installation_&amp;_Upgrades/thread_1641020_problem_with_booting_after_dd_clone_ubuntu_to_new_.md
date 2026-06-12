---
title: "problem with booting after dd clone ubuntu to new hard drive"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by teddmeister2 on 2010-12-08
[solved]
I recently got a new (much bigger) hard drive.  I used dd to clone the partition with ubuntu on it to the new hard drive.  However, I run into a problem where, even changing grub to look at the new hard drive, it boots to the old hard drive.  When unplugging the old hard drive, it simply doesn't boot.  Can't figure this out.  Please help.

---

### Post by drs305 on 2010-12-08
You may need to change the UUID of one of the two Ubuntu partitions. Since Grub2 now uses UUIDs to find the partitions it may be getting confused.

You can change a partition's UUID with the following command, but make sure you update grub and fstab before you reboot:

```
sudo tune2fs -U random /dev/sd**XY**
sudo update-grub
```

**Added:** With the old drive unplugged, from a LiveCD you can run the following to make sure G2 is on the MBR. Change XY to the correct names (example: sda5)

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If you are on your other/old Ubuntu, you can mount your desired Ubuntu (sdXY) on /mnt and then use the same commands above.



If this doesn't fix things, please post the RESULTS.txt after running the boot info script from this site:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by teddmeister2 on 2010-12-08
Actually, after looking at it, it looks like I'm booting from my new hard drive, it's just that I get the same warning that the hard drive is almost full and the amount of space I have left as the old drive. b/c disk utility says that /dev/OLDDRIVE isn't mounted.  Is this a problem with fstab settings?

---

### Post by drs305 on 2010-12-08
I'm assuming you cloned this to a larger drive?

I'm about to log off and don't have time to research it, but I know that there are some issues about cloned drives and that you sometimes have to use "resize2fs" to allow the larger drives/partitions to be seen. I think I've even posted about it. Do a search of the forum and you will probably find the answer.

---

### Post by teddmeister2 on 2010-12-08
It worked!  Thanks!  You are a life saver.

---

