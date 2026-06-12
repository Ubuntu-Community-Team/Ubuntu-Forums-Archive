---
title: "Grub 18 Error on 9.10 Live CD Instal"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by ksanger on 2010-03-15
Tried to install ubuntu 9.10 live cd Sunday with existing Win XP SP3. Asus A7N8X Deluxe, AMD Athlon XP 2800, 2G Ram, 640 GB HD. Hard drives are two 320G drives striped together using Raid 0. Raid shows up as scsi drive on mobo. XP on the first 200 GB. NTFS on the second 200 GB. 200 GB free. Installed ubuntu to the free using all of the disk. On booting obtained Grub error 18.


 Now what do I do? I've recovered XP using original CDs then overwrote boot sector. XP shows the remaining hard drive has two partitions, one almost 200 G and one about 5 G with the 5G last in line.  Looks like Linux loaded.



 I'm not comfortable trying to reinstall or fix grub2, then having to keep doing so whenever Ubuntu or Windows updates. (I had run fedora core 4 for 10 years without updating, recently my bank stopped working with Firefox 1.0 and I had to update to fedora core 10 to get Firefox to run, but that 16 bit system is still running with no updates). I'ld really like to get away from XP's updates, as today trying to ignore SP3 upgrade killed Avast. I had to delete Avast, update to SP3 anyway, then reinstall Avast. Shouldn't need to update a pc to start it up and go online.


 Anyway ubuntu looked good on the web.  When will it be fixed so I can install it properly?

---

### Post by dstew on 2010-03-16
Ubuntu is not very good at installing to a RAID like yours. It can be done, maybe, but it is difficult. See [this forum thread]("http://ubuntuforums.org/showthread.php?t=1360445"). I am not sure if RAID support for installation is going to be improved or not. Ubuntu will recognize a RAID once it is installed, however. But, it is usually best to install Ubuntu into an un-RAIDed partition.

---

### Post by ksanger on 2010-03-16
dstew;  Thanks, that thread looks like there are multiple things to try.  I have used unix, so I've no excuse not to at least try.  Just hope that its not the 200 GB first and second partitions causing the Error 18 meaning the bios isn't letting grub jump 400 G into the disk to start at the linux partition.  If I'm hitting the limit I'ld have to partition xp for less than the limit to start the linux drive sooner.  I love the sata drives running under raid 0.  Their quite, and I've got plenty of room so I shouldn't run out soon.  I didn't need to update the bios for xp sp2 to use the raid 0 array.  All of this is way too much to have to know to get up and running though.  What's the rest of the world going to do?

---

### Post by dstew on 2010-03-17
The grub 18 error is probably more complicated that the old cylinder-limit-in-BIOS problem. It is more likely that your BIOS is fairly sophisticated, has RAID extensions or other settings that grub is not dealing with well. One example is in [this thread]("http://www.linuxforums.org/forum/debian-linux-help/52256-first-time-trying-linux-grub-error-18-a.html"), where a BIOS setting for IDE translation was causing the behavior. You don't need to update your BIOS. You could try changing some settings to see if it will help. But, if grub is trying to boot from a RAID0, it will fail, because (I think) grub cannot deal with striped RAID. At least, grub legacy (version 0.97) could not. I looked at grub2 threads and the grub2 wiki and could not find any indication that grub2 supports striped RAID. However, legacy grub and grub2 can boot kernels on mirrored RAID, ([see this]("http://grub.enbug.org/MirroringRAID?highlight=%28RAID%29")) but only because it is fooled into thinking that the mirrored partition is un-RAIDed. I did this before. I had a software RAID5 setup, but had to make a small RAID1 for grub to boot the kernel off of.

My only suggestions is to try the installation methods listed in that How-To, or put Ubuntu into an un-RAIDed partition.

Good luck and best wishes.

---

### Post by psusi on 2010-03-17
I also have a fakeraid on my Asus K8N Delux motherboard.  In the past getting Ubuntu working with it was a pain, but 9.10 installed smoothly.  Try booting from the livecd and take a look in that 5G partition and make sure you can see the normal filesystem there.  It sounds like everything but grub got installed correctly.  If that is the case, then you can try reinstalling grub from the livecd.

First run sudo -s to switch to root, and find out the name of the partition.

```

sudo -s
ls /dev/mapper

```

You should see something like nvidia_abcdefg.  That is the raid device.  From now on when I say nvidia_abcdefg, I mean whatever yours said here, not literally "nvidia_abcdefg".  There should also be nvidia_abcdefg1 and 2 for the partitions.  Assuming nvidia_abcdefg2 is that 5G partition, then mount the new filesystem and chroot into it:
```

mount -t ext4 /dev/mapper/nvidia_abcdefg2 /mnt
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/proc
chroot /mnt

```

At this point you will be running a shell that thinks it is running from the hard disk.  Now you need to fix your /boot/grub/device.map file so:

```

nano /boot/grub/device.map

```

You should see at least one line that says (hd0) /dev/sda.  You might have a second line for hd1 pointing to sdb.  You want to change this so that you have only hd0 pointing to /dev/mapper/nvidia_abcdefg instead of sda.  Save and exit, then reinstall grub:

```

grub-install '(hd0)'

```

Now reboot.

---

