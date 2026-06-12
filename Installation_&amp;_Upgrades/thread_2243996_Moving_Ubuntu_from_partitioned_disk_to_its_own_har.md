---
title: "Moving Ubuntu from partitioned disk to its own hard drive"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by Riothamus on 2014-09-12
I have my hard drive partitioned with Windows 7 on /dev/sda2 and Ubuntu 12.04 LTS installed on /dev/sda6. The remaining partitions are used for recovery modes, the linux swap space, and so on. This is my df configuration:

```

/dev/sda6      217784244  11638932 195082428   6% /
udev             1853904        12   1853892   1% /dev
tmpfs             379136       896    378240   1% /run
none                5120         0      5120   0% /run/lock
none             1895680        76   1895604   1% /run/shm
/dev/sda2      484550384 184728364 299822020  39% /media/WIN7

```

I recently installed a new hard drive and I've been trying to migrate my Ubuntu installation there without having to reinstall the OS and software from scratch. I booted from the Ubuntu 12.04 Live CD and started GParted, then created a new partition on /dev/sdb (which is my new hard drive) and created a 3.75 Gig linux swap space partition at the end of the drive because that's the size of the swap space on my current setup (the partitioned one). Then I copied and pasted my Ubuntu partition to its own, new partition on /dev/sdb. GParted copied the partition, checked for errors, and then resized it. Because I had previously tried this using a different approach, the linux swap space was already called /dev/sdb2, so the main partition became /dev/sdb1.

Then I generated a new UUID and changed the UUID of /dev/sdb1 using:
```

sudo tune2fs /dev/sdb1 1bcc0198-3a90-11e4-9736-00e04c68091f

```

Next, I installed grub on this partition by doing the following:

```

sudo mount /dev/sdb1 /media/tmp
sudo grub-install --root-directory=/media/tmp /dev/sdb  //Putting /dev/sdb1 gave errors, so I just put /dev/sdb

```

Finally, I modified /media/tmp/etc/fstab. All I did was change the UUIDs to the UUID of the new Linux partition that was copied, and the UUID of the linux swap space on the new drive, respectfully:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
/dev/sda2    /media/WIN7    ntfs
UUID=1bcc0198-3a90-11e4-9736-00e04c68091f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=451a0a74-36a1-474d-87e4-983298d60ad0 none            swap    sw              0       0

```

When I rebooted, I went into the BIOS and set the new hard drive as the primary boot drive, because I understand that if the Windows drive is the primary boot drive, it will not recognize the Linux drive, and will not give the option of which OS to boot into. My intention is to delete the Linux partition from the first hard drive once I'm sure the migration was successful, but for the time being, it's still there.

When I boot, everything starts up okay, and I've even disabled booting from the first hard drive with the BIOS to ensure that it is able to boot correctly from the new hard disk. But the only problem is that when I do this, even though it's booting from the second hard drive, it's still mounting /dev/sda6 as / and /dev/sdb1 isn't being mounted at all. Was there anything else I was supposed to change besides /etc/fstab to make this boot correctly?

---

### Post by oldfred on 2014-09-12
It sounds like you made all the changes that should be required.
But because of your type of issues is why I suggest a clean install and copy /home over.
Not sure if your grub menu still has old UUID. A full choot uninstall & reinstall would make sure that grub's menu has new UUID.
While we are never supposed to edit grub.cfg, your case is an exception. You should only have to manually edit first entry with new UUID. Then once booted into it run the sudo update-grub and all entries will be updated.

Post link to BootInfo report, it that does not work.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Riothamus on 2014-09-12
Thanks, that seems to have fixed everything!

---

