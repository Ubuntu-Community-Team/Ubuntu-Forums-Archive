---
title: "Upgrade Encrypted Hard Drive HOWTO"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by simguru on 2011-01-11
**SCENARIO:** I had a laptop with a failing hard drive. I use whole disk encryption as illustrated in [http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html]("http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html"). This guide will show one how to move their Ubuntu system from an old disk to a new disk. Even if you don't use encrypted disks like I do, the same principles apply and, in that case, one can just skip the section related to encryption.

**STEP 0: Preliminaries**
I have three slices in my hard disk:
```

/dev/sda1	256 MB	/boot	(unencrypted)
/dev/sda2	158 GB	/	(encrypted as sda2_crypt)
/dev/sda3	2 GB	swap	(encrypted as sda3_crypt)

```

Substitute this map of the partition table with whatever suits your configuration. All examples will assume this map. You can map the partition table on your hard drive by:

```

sudo fdisk -l

```

**STEP 1: Full System Backup**

Insert the Ubuntu Desktop CD and boot it. Select "Try Ubuntu" to start the LiveCD environment. Now mount a backup medium (USB flash drive, external hard drive, etc) on /media/backup. Now we need to mount the root filesystem. For those of us using encryption, double clicking the encrypted volume and letting the LiveCD mount it for us is a **BAD IDEA**. The LiveCD will map the encrypted root filesystem based on its UUID. This is problematic because the encrypted volume must be mapped in the same way as the original system configuration. So, we can use the command line:

```

sudo mkdir /media/olddrive
sudo cryptsetup luksOpen /dev/sda2 sda2_crypt
sudo mount /dev/mapper/sda2_crypt /media/olddrive
sudo mount /dev/sda1 /media/olddrive/boot

```

It is necessary to mount the boot slice under the root slice so the file structure of the system is preserved. Now, we can backup the files themselves:

```

cd /media/olddrive
sudo tar cpvf /media/backup/olddrive.tar .

```

**STEP 2: Setup the New Hard Drive**

I now swapped the old drive for a new, blank hard drive and created a parition table as follows:
```

/dev/sda1	256 MB	/boot	(unencrypted)
/dev/sda2	498 GB	/	(encrypted as sda2_crypt)
/dev/sda3	2 GB	swap	(encrypted as sda3_crypt)

```

Notice the only change is the size of root slice since this is a hard drive upgrade (who would ever downgrade?). You can use fdisk, cfdisk, or gparted to create the partition table. Now, I setup and format the slices:

```

sudo cryptsetup luksFormat /dev/sda2
sudo cryptsetup luksOpen /dev/sda2 sda2_crypt
sudo mkfs.ext4 /dev/sda1
sudo mkfs.ext4 /dev/mapper/sda2_crypt

```

And then I mounted the new hard drive and restored the files:

```

sudo mount /dev/mapper/sda2_crypt /mnt/newdrive
sudo mkdir /mnt/newdrive/boot
sudo mount /dev/sda1 /mnt/newdrive/boot
sudo tar -C /mnt/newdrive -xpvf /mnt/backup/olddrive.tar 

```

Note the careful order of creating the mount point for the /boot slice on the new drive. If these commands are done out of order, you will experience unexpected results.

**STEP 3: Change UUIDs**

The tricky part of this process is changing the UUIDs (now used by default on Ubuntu for all disk related functions). To get the active UUIDs for the (new) disk, use:

```

blkid

```

In /etc/fstab, the entry for the /boot slice needed updating:

```

UUID=VVVVVVVV-WWWW-XXXX-YYYY-ZZZZZZZZZZZZ	/boot	ext4	defaults	0	2

```

Replace VVVVVVVV-WWWW-XXXX-YYYY-ZZZZZZZZZZZZ with the UUID for sda1 from the blkid command. For the encrypted root filesystem, I found it necessary to again change the UUID in /etc/crypttab:

```

sda2_crypt UUID=VVVVVVVV-WWWW-XXXX-YYYY-ZZZZZZZZZZZZ none luks

```

Again, replace VVVVVVVV-WWWW-XXXX-YYYY-ZZZZZZZZZZZZ with the UUID for sda2 from the blkid command. **WARNING:** Do not use the UUID for sda2_crypt. This file is supposed to tell cryptsetup which slice to decrypt, not what the decrypted output will be.

**STEP 4: Reinstall GRUB2**

This is probably the hardest part. The simple way outlined in [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2") doesn't work since the kernel image booted still has the old UUID hard wired in it. Instead, we will be following the chroot method mentioned there. We will mount the virtual filesystems on top of the restored file system and go from there:

```

sudo mount --bind /dev /mnt/newdrive/dev
sudo mount --bind /dev/pts /mnt/newdrive/dev/pts
sudo mount --bind /proc /mnt/newdrive/proc
sudo mount --bind /sys /mnt/newdrive/sys
sudo chroot /mnt/newdrive

```

This should give us a shell inside the chroot environment. Edit /boot/grub/grub.cfg and replace all old UUIDs with the UUID for sda1 found from the blkid command. The grub.cfg contained many lines like this:

```

menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set VVVVVVVV-WWWW-XXXX-YYYY-ZZZZZZZZZZZZ
	linux	/vmlinuz-2.6.32-27-generic root=/dev/mapper/sda2_crypt ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/initrd.img-2.6.32-27-generic
}

```

Again, replace VVVVVVVV-WWWW-XXXX-YYYY-ZZZZZZZZZZZZ with the UUID for sda1 from the blkid command. Now, we are ready to rebuild the kernel images and reinstall grub:

```

sudo dpkg-reconfigure udev
sudo update-initramfs -u
sudo update-grub
sudo grub-install /dev/sda

```

Reboot. The process should now be complete and you should be now booting with a new drive without having to reinstall everything. Please send me any feedback, clarifications, or corrections.

---

