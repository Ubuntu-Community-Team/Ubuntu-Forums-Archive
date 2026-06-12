---
title: "Swap partition"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by nicoliani on 2012-04-01
I installed it with no dual boot, it's the only OS on my netbook.
I have tried numerous times, both by letting Ubuntu do the install automatically and me setting the partitions, although I end up with the same outcome and that is when I look in GParted I see the swap file doesn't exist, and I can't even set that partition as swap in GParted.

[CENTER][IMG]http://img801.imageshack.us/img801/1889/skrmbild20120401012451.png[/IMG]
By [nicoliani]("http://profile.imageshack.us/user/nicoliani") at 2012-04-01

[LEFT]The swap file should be **sda5**, and as you can see its file system is unknown.
[/LEFT]
[/CENTER]

---

### Post by sudodus on 2012-04-01
Welcome to the Ubuntu Forums!

Have you tried to boot from the Ubuntu install USB drive, and from there delete the swap partition and use the free space to install a swap partition (re-install)?

After that it will have another UUID, so you have to change the line in fstab to point to the UUID of the new swap partition. Once you have rebooted from your installed system, start a terminal window and run a couple of commands to fix the that!
```
sudo blkid
``` gives you the UUID. Use it without quotes editing fstab
```
sudo nano /etc/fstab
```

*Edit: If this does not work, maybe you should check if you have an msdos (mbr) partition table or something else, or if there are traces from another partition table, that was used before.*

---

### Post by nicoliani on 2012-04-07
Thanks sudodus.

What I did was I rebooted and deleted the partition. Then I made that same partition as a swap file again and exited the install process.
In Gparted I got the same results as before, the partition showing up as unknown, although this time I could set it as swap file in Gparted. So now it's set as swap.
Do I need to run the commands as you pointed, or it's not necessary as I used Gparted?

And yes the hard disk was used for WIN7 before. I formated the disc but can there still be traces left?

---

### Post by coffeecat on 2012-04-07
@nicoliani, do you have an encrypted home? If you have an encrypted home, then the swap partition is encrypted too and that is how it appears in Gparted. I don't know how feasible it is to create a non-encrypted swap partition with an encrypted home but if this is what you have achieved, this is not desirable. It is theoretically possible for some of your personal data to be written unencrypted to the swap partition.

---

### Post by darkod on 2012-04-07
If you deleted the partition and created a new one, it doesn't automatically change the UUID entry in /etc/fstab.

Post the results of:
cat /etc/fstab

and

sudo blkid

Most probably you will need to change the UUID identifier for swap in /etc/fstab.

---

### Post by nicoliani on 2012-04-07
> **coffeecat said:**
> @nicoliani, do you have an encrypted home? If you have an encrypted home, then the swap partition is encrypted too and that is how it appears in Gparted. I don't know how feasible it is to create a non-encrypted swap partition with an encrypted home but if this is what you have achieved, this is not desirable. It is theoretically possible for some of your personal data to be written unencrypted to the swap partition.

Yes my home is encrypted. So are you saying I have a swap and tha Gparted can't show it.

---

### Post by nicoliani on 2012-04-07
> **darkod said:**
> If you deleted the partition and created a new one, it doesn't automatically change the UUID entry in /etc/fstab.

Post the results of:
cat /etc/fstab

and

sudo blkid

Most probably you will need to change the UUID identifier for swap in /etc/fstab.

After the second reboot and login, I open Gparted and the swap partition is again unknown. Wasn't so after one reboot as I checked.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=4d04c514-0f6f-4d8b-a686-908953a9317b /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d8d1467f-7a36-4be6-8b4e-00dec1417319 /boot           ext2    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=0353d124-861b-48c8-8073-7dce9ae54d07 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=dd9ad4d2-1bed-4a40-8525-ed8696fe1a3a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

/dev/sda1: UUID="d8d1467f-7a36-4be6-8b4e-00dec1417319" TYPE="ext2" 
/dev/sda5: UUID="4d04c514-0f6f-4d8b-a686-908953a9317b" TYPE="ext4" 
/dev/sda7: UUID="0353d124-861b-48c8-8073-7dce9ae54d07" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="984ce583-2c37-4ede-aa9f-fb78128d502e" TYPE="swap"

---

### Post by coffeecat on 2012-04-07
> **nicoliani said:**
> Yes my home is encrypted. So are you saying I have a swap and tha Gparted can't show it.

In a way. Don't worry about what Gparted shows. Your outputs in your post #7 show that you have an encrypted swap and a suitable mount line in /etc/fstab. Simply run "top" in the terminal and/or System Monitor -> Resources tab to be sure that your system is seeing the swap space. If it is you can forget about what you see in Gparted.

---

