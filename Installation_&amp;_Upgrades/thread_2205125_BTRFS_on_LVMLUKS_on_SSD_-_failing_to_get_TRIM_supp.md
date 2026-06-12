---
title: "BTRFS on LVM/LUKS on SSD - failing to get TRIM support enabled (MOVED)"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by SixedUp on 2014-02-12
[This post moved from the hardware forum, where the only reply it received was from another user experiencing the same problem]

I'm trying to set up 13.10 on a 250GB Samsung 840 EVO SSD in a Thinkpad x201. Because this machine is used for work, I need full disk encryption, so I'm using the traditional approach of a LUKS/LVM container for all partitions apart from /boot. To keep the SSD running well I'm keen to get Trim support working. And so far I'm failing, and need some help!

What I've been doing (because of the limitations of the GUI installer) is a manual partition and post-install tidy up:

So, from the Live USB, I install and run gdisk to create a GPT partition table on the SSD, and then a 1GB /boot partition (sda1, type 8300) aligned to 2048 sectors. Then the rest of the space is allocated to an LVM container (sda2, type 8e00).

I then issue:```

sudo cryptsetup luksFormat /dev/sda2
sudo cryptsetup luksOpen /dev/sda2 Ubuntu
sudo pvcreate /dev/mapper/Ubuntu
sudo vgcreate Ubuntu /dev/mapper/Ubuntu
sudo lvcreate -L 20G -n RootVol Ubuntu
sudo lvcreate -L 4G -n SwapVol Ubuntu
sudo lvcreate -l 100%FREE -n HomeVol Ubuntu
```

At this point I can run the GUI installer, pointing it at my partition layout, getting it to format the various partitions and install 13.10. When that completes, I stay in the Live USB, and:
```

sudo mount -t btrfs -o compress-force=zlib,discard,noatime,subvol=@ /dev/mapper/Ubuntu-RootVol /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
> mount -t proc proc /proc
> mount -t sysfs sys /sys
> mount -t devpts devpts /dev/pts
```

I then create /etc/crypttab:```

# <target name> <source device> <key file> <options>
Ubuntu UUID=41ef7d4b-500c-4c83-a40a-9ef1c456653f none luks,discard
```

I then create /etc/initramfs-tools/conf.d/cryptroot:```

CRYPTROOT=target=Ubuntu,source=/dev/disk/by-uuid/41ef7d4b-500c-4c83-a40a-9ef1c456653f,discard
```

I then alter /etc/lvm/lvm.conf, changing the line that reads
```
issue_discards = 0
```
to 
```
issue_discards = 1
```

Next update my /etc/fstab to reflect the mount options I want:```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/Ubuntu-RootVol /               btrfs   defaults,noatime,compress-force=zlib,discard,subvol=@ 0       1
# /boot was on /dev/sda1 during installation
UUID=d024ca5e-a8ba-45f3-9f46-e5949c84f125 /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-HomeVol /home           btrfs   defaults,noatime,compress-force=zlib,discard,subvol=@home 0       2
/dev/mapper/Ubuntu-SwapVol none            swap    sw              0       0
```

Finally, I update /etc/default/grub so the GRUB_CMDLINE_LINUX statement reads:```

GRUB_CMDLINE_LINUX="cryptopts=target=Ubuntu,source=/dev/disk/by-uuid/1f199eb6-b2ad-4014-9f8d-41954bf1a417,lvm=Ubuntu"
```

I then issue the commands:```

update-initramfs -k all -c
update-grub
```
and reboot.

The system comes up fine, but, when I try to run a trim on the SSD, I get:
```
> fstrim -v /home
fstrim: /home: FITRIM ioctl failed: Operation not supported.
```

If I then examine the discard status of the block level devices, I get:```

> lsblk -D
NAME                        DISC-ALN DISC-GRAN DISC-MAX DISC-ZERO
sda                                0      512B       2G         0
&#9500;&#9472;sda1                             0      512B       2G         0
&#9492;&#9472;sda2                             0      512B       2G         0
  &#9492;&#9472;Ubuntu (dm-0)                  0      512B       2G         0
    &#9500;&#9472;Ubuntu-RootVol (dm-1)        0      512B       2G         0
    &#9500;&#9472;Ubuntu-SwapVol (dm-2)        0      512B       2G         0
    &#9492;&#9472;Ubuntu-HomeVol (dm-3)        0      512B       2G         0
```

Which seems to imply no TRIM support. But if I do:```

> hdparm -I /dev/sda | grep -i trim
    *    Data Set Management TRIM supported (limit 8 blocks)
```
... I can see that the drive does support TRIM.

So if I try to run the fstrim on the /boot partition (/dev/sda1) I get:```

> fstrim -v /boot
/boot: 933625856 bytes were trimmed
```
... which implies that drive support is OK, and so is the kernel support. Of course, /boot is ext3, not btrfs like the / and /home. 

So this might be BTRFS, or it might be the LUKS/LVM containers. And by running:```

> cryptsetup status Ubuntu
/dev/mapper/Ubuntu is active and is in use.
  type:    LUKS1
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda2
  offset:  4096 sectors
  size:    486293839 sectors
  mode:    read/write
```
... I believe I can confirm its a LUKS problem, as the output is missing the expected " flags: discards" at the end, indicating the TRIM passthrough is NOT enabled for some reason. **I think.**

I can further check this with:```

> dmsetup table
Ubuntu-SwapVol: 0 8388608 linear 252:0 41945088
Ubuntu-RootVol: 0 41943040 linear 252:0 2048
Ubuntu-HomeVol: 0 435953664 linear 252:0 50333696
Ubuntu: 0 486293839 crypt aes-cbc-essiv:sha256 0000000000000000000000000000000000000000000000000000000000000000 0 8:2 4096
```

Again, there is a lack of the expected " 1 allow_discards" on the Ubuntu entry.

So, has anyone actually got this working yet? I've tried with both Raring and Saucy 64bit, and both fail in exactly the same way, so its either a long standing shortcoming, or I'm making the same mistake repeatedly :-)  Any help much appreciated!

---

### Post by SixedUp on 2014-02-12
Further information: I just upgraded cryptsetup to the latest version (2:1.6.2-0ubuntu0~ppa1~saucy) via [https://launchpad.net/~rayanayar/+archive/cryptsetup](https://launchpad.net/~rayanayar/+archive/cryptsetup), and it has made no difference to my existing system behaviour. Still can't seem to issue Trim commands to the SSD for anything in the LUKS/LVM containers.

---

### Post by SixedUp on 2014-02-20
Solved. [Solution posted here]("http://ubuntuforums.org/showthread.php?t=2197108").

---

