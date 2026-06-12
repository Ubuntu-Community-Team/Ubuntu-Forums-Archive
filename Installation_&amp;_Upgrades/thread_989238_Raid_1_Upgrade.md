---
title: "Raid 1 Upgrade"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by groovey58 on 2008-11-21
Hey all.

I have just built a home server with Ubuntu 8.04.

My system is a Gigabyte GA-7N400 S-L MB with an AMD 2800+ CPU. It runs with a nforce2 chip set.

I have 2 TB seagate hard drives. One is the root and system disk. The other is not mounted.

I would like to RAID 1 the system but everything I have found is how to do this from the setup. As it has taken me 3 weeks to get my server to it's current state I would like to upgrade the system to RAID 1, not start from "scratch" as all of the tutorials seem to state.

Could someone point me to a tutorial that can help me with this task?

Thanks

---

### Post by psusi on 2008-11-21
1)  Create a single disk raid 1 using the spare drive and format it
2)  Copy all files from the exiting drive to the raid array
3)  Update grub to boot from the raid array
4)  Reboot and make sure the system is running off the raid array
5)  Add the original disk to the raid array
6)  Reinstall grub on both disks

Consult man pages as I'm doing this from memory, but step one should look like ( assuming sdb1 is the raid partition you created on the spare disk ):

```

sudo mdadm -C /dev/md0 -n 2 -l raid1 /dev/sdb1 missing
mke2fs -j /dev/md0

```

You will want to boot into recovery mode to make sure files aren't in use while you copy them.  Mount the raid filesystem, then copy:

```

sudo mount -t ext3 /dev/md0 /mnt
sudo cp -ax / /mnt
sudo umount /mnt

```

That should get everything if you only have a single root filesystem.  If you have more, you will need to copy each.  Now to fix grub to boot from the raid.  Edit /boot/grub/menu.lst and change the line that says # kopt=root=UUID=xxxx so that the UUID=xxxx part is replaced with /dev/md0.  Also replace the UUID=xxxx part if the root entry in /etc/fstab with /dev/md0.  Then update grub:

```

sudo update-grub

```

Now when you reboot the system should be using the new filesystem on the raid for the root.  Verify this by checking the output of sudo mount, and make sure the entry for / says /dev/md0.

Now use fdisk to change the partition type of the partition on the first disk to raid autodetect, and add the partition to the raid array:

```

sudo mdadm /dev/md0 --add /dev/sda1

```

That should start the process of synchronizing the two disks.  You can check on the status with sudo mdadm -D /dev/md0.  Wait for it to finish then reinstall grub:

```

sudo grub
root (hd0,0)
setup (hd0)
setup (hd1)

```

---

