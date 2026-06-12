---
title: "filesystem / converted to @ after upgrade on btrfs partitions"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by rterbush on 2011-05-02
I performed a fresh install of Natty on my laptop last night and was reasonably happy with the outcome. Things seemed to be working properly and was getting used to the UI changes.

Today I updated some packages which included a kernel package update to 2.6.38-9.

I'm running a 3 partition layout on an SSD drive. /boot is small ext2, with / and /home being btrfs.

When rebooting after the kernel update, the system would not boot and dropped into an (initramfs) prompt. After a bit more debugging, I figured out that /sbin/init was missing so I booted from live cd and ran fsck on all partitions and then mounted them to have a look at what was on the drives.

It appears that the / of both of the btrfs partitions has been converted to an '@' symbol. When mounting the / partition, you only see the '@'. It appears that all files are intact below the '@' but this obviously has made it impossible to find /sbin/init since it is now /@/sbin/init.

I'm going to give it a try to move all files up a level and see what happens but I am curious to know what is going on here.

Thanks

---

### Post by obaudys on 2011-05-04
What's actually going on is that there are a number of subvolumes (one in your case) placed in the btrfs filesystems true root, and the one called '@' is your original root.

You need to mount the btrfs filesystem not from it's true root, but at the subvolume '@'. ie.

```

mount -o subvol=@ /dev/<whatever> /

```

Now your root fs will be the contents of the subvolume '@'.  I thought this is an ubuntu specific filesystem layout as far as I know... which tool did you convert with?

You will need to put the subvoll option in /etc/fstab

If you want to see the true root of the btrfs filesystem at anytime, just ```
mount /dev/<whatever> /mnt
``` and you can see all the subvolumes (just 1 on your case, lol) under /mnt.

I was also scratching my head regarding this oddity, in my case it was when trying to figure out how apt-btrfs-snapshot works. :P  Couldn't figure out where the "@apt-snapshot-xxx" subvolumes where kept;  I had to dig into the python code itself, which is a masterpiece of terse python.

No need for you to have a seperate /home btfs partition now. You can 
```

mount /dev/<whatever> /mnt
cd /mnt
btrfs subvolume create @home
# copy home partition to this btrfs volume
cp -a /home/ /mnt/@home

```
Then edit /etc/fstab to point your home to your root filesystem with subvol=@home.

The you can add the partition that was formerly a seperate /home with "btrfs dev add"

---

### Post by rterbush on 2011-05-10
Sorry for delayed response...

So this is a repeatable problem. 

1. Install Ubuntu 11.04
2. Upgrade to 2.6.38-9 kernel release

Reboot will fail to mount the filesystems and drop to (initramfs) prompt.

Looking around at the existing /etc/fstab, the mount options are there for the subvol=@ and subvol=@home for mounting my / and /home btrfs filessystems. (/boot is on ext2)

So I am puzzled as to why this is not booting properly.

---

### Post by obaudys on 2011-05-11
> **rterbush said:**
> Sorry for delayed response...

So this is a repeatable problem. 

1. Install Ubuntu 11.04
2. Upgrade to 2.6.38-9 kernel release

Reboot will fail to mount the filesystems and drop to (initramfs) prompt.

So I am puzzled as to why this is not booting properly.



Hmmm.. it could be that your initrd does not do a "btrfs device scan" or does not have the btrfs modules installed.  Maybe you did not have "btrfs-tools" installed before you converted?  Once you install that package it will rebuild the initrd.

Easy way to fix it:  

[LIST=1]
[*]boot into rescue cd
[*]open a root terminal
[*]mount the btrfs filesystem with -o subvol=@ on /mnt
[*]mount /boot on /mnt/boot
[*]chroot to /mnt/
[*]run dpkg -l btrfs-tools, and if not installed, use apt-get to install it.
[/LIST]

---

### Post by rterbush on 2011-05-11
This is not a filesystem conversion. This is a clean install of 11.04 and btrfs filesystems were working before the kernel update to -9.

I've checked and both the btrfs.ko module is present under /lib/modules/2.6.38-9-generic and the btrfs-tools indicate they are installed.

This info needs to make it to the dev/test team somehow... it is easily repeatable.

---

### Post by obaudys on 2011-05-12
> **rterbush said:**
> This is not a filesystem conversion. This is a clean install of 11.04 and btrfs filesystems were working before the kernel update to -9.

I've checked and both the btrfs.ko module is present under /lib/modules/2.6.38-9-generic and the btrfs-tools indicate they are installed.

This info needs to make it to the dev/test team somehow... it is easily repeatable.

Okay I have installed linux-image-2.6.38-9-generic (it is not in the repos, I downloaded the deb from launchpad) and it all seems to work fine after a reboot.

My exact Ubuntu package version is 2.6.38-9.43 (arch is amd64), if that helps.

The contents of my initrd after grepping for "btrfs" in the filenames by running:
```

zcat /boot/initrd.img-2.6.38-9-generic | cpio -i -t 2>/dev/null | grep btrfs
```

show the following files:
```

lib/modules/2.6.38-9-generic/kernel/fs/btrfs
lib/modules/2.6.38-9-generic/kernel/fs/btrfs/btrfs.ko
sbin/btrfsctl
scripts/local-premount/btrfs
```

If your initrd looks like this, it should work, otherwise, something went wrong, and you may need to reinstall btrfs-tools or something.

---

### Post by rterbush on 2011-05-12
The driver and associated files are all there. Not sure what package version I ended up with.

To add a few more details about how I got to this point.

1. Installed clean 11.04 from CD
2. In Synaptic, chose under "Updates" tab, maverick-security, maverick-updates, maverick-proposed and maverick-backports
3. Reloaded repositories
4. Marked Upgrades
5. Applied
6. Rebooted

Pretty basic test case. I would think someone either knows there is a problem, or should know.

I'll pull back to maverick-updates only for the time being. 

FWIW, I am installing on SSD.

---

