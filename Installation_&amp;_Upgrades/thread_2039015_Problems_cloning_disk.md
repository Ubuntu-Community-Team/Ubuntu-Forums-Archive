---
title: "Problems cloning disk"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by Iker Höek on 2012-08-07
Hello there.

I've got a problem: i took quite a bit (6 months) to set up a server to work exactly as required and then some.

Now i need to be able to clone it to other hard disk to deploy it.

The thing is that it's virtualized in Virtualbox from the beginning and was set up with a dynamic 2TB hard disc (don't ask me why, i'm still wondering the same) so deploying it with dd would require a 2TB hdd which are kinda hard to come by with those prices lately.

So i decided to clone the virtual machine to a smaller drive (160GB or less).

I've used Gparted, Clonezilla, rsync, dd and the bunch and each time someting was not quite rigth (Plymouth issues after clone, dd wanting to clone more than the hdd size after shrink, system broken after exporting to appliance, etc), so i kept restoring snapsots time after time.

After so much trying i've come to a point where Virtualbox won't allow me to revert nor delete snapshots so i can't do too much to the server without breaking it (and it's still working perfectly in that broken 2TB virtual hdd).

Now i need a way to clone it to a 160GB virtual disk so i can deploy the latter to target systems (need to have it still virtual because hdd's die).

I've depleted my google-fu trying and there's always a detail which doesn't work with my setup.

Do any of you know a windows-guy-proof way to achieve this?

Now, specs:
OS: Ubuntu server 12.04
Arch: 32 bits
hardware: default Virtualbox hardware
hdd:
```
Disk /dev/sda: 2199.0 GB, 2199022206976 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294965248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007a538

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  4292870143  2146434048   83  Linux
/dev/sda2      4292872190  4294963199     1045505    5  Extended
/dev/sda5      4292872192  4294963199     1045504   82  Linux swap / Solaris
rodrigo@Svr-Mon:~$
```
Space used: 1.9G

Any help will be incredible appreciated =)

**TL;DR**: halp! Need to clone virtual disk, can't try too much w/o breaking it.

---

### Post by darkod on 2012-08-08
One program that copies only the data and can restore to a smaller partition/disk as long as the data fits, is FS Archiver. You can run it from the System Rescue CD or install it in Ubuntu (it might be even included in latest releases, not sure).

It's supposed to work right away after restore, maybe you will need to change the UUIDs with the new ones in /etc/fstab and reinstall grub/grub2 to the MBR so it can connect to the config files, but apart from that, it should work out-of-the-box.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

Of course, this being a VBox machine, you will need to for example save the backup file inside your ubuntu VM, and then using shared folders or such take it outside of the VM. After that you can do what you want with it.

---

### Post by Iker Höek on 2012-08-08
> **darkod said:**
> One program that copies only the data and can restore to a smaller partition/disk as long as the data fits, is FS Archiver. You can run it from the System Rescue CD or install it in Ubuntu (it might be even included in latest releases, not sure).

It's supposed to work right away after restore, maybe you will need to change the UUIDs with the new ones in /etc/fstab and reinstall grub/grub2 to the MBR so it can connect to the config files, but apart from that, it should work out-of-the-box.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

Of course, this being a VBox machine, you will need to for example save the backup file inside your ubuntu VM, and then using shared folders or such take it outside of the VM. After that you can do what you want with it.

Would that be like using rsync for the copy? Since rsync doesn't copy the boot info.

So process would be like:
1. Create another virtual hdd
2. Partition it like the original
3. Copy/clone each partition
4. Make it bootable?

Any solution that copies the boot info also or it is safe/easy to reinstall grub?

---

