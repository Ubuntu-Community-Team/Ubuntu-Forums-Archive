---
title: "anyone know of a program(free preferably) that would clone my hdd so..."
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by juntjoo on 2010-06-08
i can just swap my old one out for a larger one?  thanks in advance.

---

### Post by ssulaco on 2010-06-08
read this
[http://ubuntuforums.org/showthread.php?t=1250553](http://ubuntuforums.org/showthread.php?t=1250553)


[http://remastersys.sourceforge.net/](http://remastersys.sourceforge.net/)
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by PatCasey on 2010-06-08
> **juntjoo said:**
> i can just swap my old one out for a larger one?  thanks in advance.

Funny you should ask.  I just did this this afternoon myself.  I used **rsync**.  It's already in the default desktop installation too so there's nothing to install. Well, I take it back, I did choose to install **gparted** to do the partitioning too.



Here's a summary of what I did:

1. Create the partitions on the new disk as you would want them.
I installed and used gparted to do this.  I originally tried to use the disk utility under the System / Administration menu but ran into some minor trouble creating a logical partition in the extended partition. gparted was very easy to work with though.  For my example, let's assume you are partitioning /dev/sdb and you want partitions for /, /boot, /home, and /usr.  I've read that /boot should be either an ext2 or ext3 filesystem or grub might have trouble booting from it. I like journaled filesystems, so I set my /boot up as /etc3 and that worked fine for me.  Don't forget to create a swap partition too.  So for our examples, let's assume I partitioned things like this:, here's what I made for that:
```

/dev/sdb1:    /boot    ext3   approx 500M
/dev/sdb2:    swap     swap   approx 1G
/dev/sdb3:    Extended
/dev/sdb4:    /home    ext4   approx 3G
/dev/sdb5:    /usr     ext4   approx 6G
/dev/sdb6:    /        ext4   remainder

```
2. Make a directory under /mnt to mount what will become the new
root filesystem.  For example, /mnt/new
```

# mkdir /mnt/new

```

3. Mount the new root partition under /mnt/new
```

# mount /dev/sdb6 /mnt/new

```

4. Make directories under /mnt/new for the other partitions that make up the filesystem (assuming you have more than one partition in your filesystem.)
```

# mkdir /mnt/new/boot
# mkdir /mnt/new/home
# mkdir /mnt/new/usr

```

5. Mount the other partitions under /mnt/new until you have the filesystem under /mnt/new looking like you would expect to find once this is done.  For example, /mnt/new/home and /mnt/new/usr.
```

# mount /dev/sdb1 /mnt/new/boot
# mount /dev/sdb4 /mnt/new/home
# mount /dev/sdb5 /mnt/new/usr

```

6. Copy non-root partitions to their places under /mnt/new using rsync. Note: you will probably get a permission error when it tries to copy .gvfs from your home directory. I'll explain the arguments shortly.
```

# rsync -aAHX /boot/ /mnt/new/boot
# rsync -aAHX /usr/  /mnt/new/usr
# rsync -aAHX /home/ /mnt/new/home

```

NOTE: the / at the end of the source directory names is very important. Without it, /boot would copy to /mnt/new/boot/boot in the command above. Not quite what we want.

Now, about those options:
-a    archive.  Copies recursively, gets the ownership and most of the permissions we want and handles symbolic links as we would want it to. It also copies special and device files in the right way too.  Here are the things in misses though.  It doesn't get ACLs from the files if they are there; It doesn't preserve hard links across the copy; and it doesn't preserve any extended attributes the files might have.
-A    ACLs.  Preserve the ACLs.
-H    Hard Links.  Preserve hard links as they are found.
-X    eXtended attributes.  Preserve extended attributes.

7. Copy / to /mnt/new using rsync.  Exclude /dev, /sys, /proc, /mnt/new, /usr, and /home. (Excluding /usr and /home aren't strictly necessary, but why make it check them again?)
```

# rsync -aAHX --exclude /proc --exclude /sys --exclude /dev \
--exclude /mnt/new --exclude /boot --exclude /home \
--exclude /usr     /    /mnt/new

```

8. Edit /mnt/new/etc/fstab to make it point to the new partitions as if /mnt/new was /.  Until you get it working right, replace the UUID=... with the old-style /dev/sdb1 type entries. (Use the right device names for the given partitions though.)

9. Install grub-pc to the new disk.  I used the chroot method documented [here]("https://help.ubuntu.com/community/Grub2").

After a reboot, you should see the new disk as an additional choice to boot to.  Don't destroy the original boot entry just yet.  Keep it around as a very full-featured recovery disk in case things don't quite work right on the new disk just yet.

Whew.  And I thought I was summarizing. Oh well.

I hope this helps.

---

### Post by juntjoo on 2010-06-09
thanks so much.  that's quite a screen full and i'm a beginner, so we'll see. wish me luck.

---

### Post by phampson on 2010-06-10
Download the clonezilla iso the alternative version based on ubuntu. Burn it to cd/dvd and boot the pc off it.

You can use it store the image of your hard disk over the network or to another directly attached disk, usb disk. Very Very good at the job. Works for linux / windows.

So boot off the cd, backup to your chosen device.
Replace your disk
Boot off cd again, restore the backup to the new disk
Take the cd out
Boot off new disk

[http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php](http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php)

---

### Post by iskatyel on 2010-06-10
This howto is pretty solid.  We use partimage extensively for this type of task.
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

---

### Post by juntjoo on 2010-06-10
awesome ya'llz.  this'll keep me busy for a while.

---

### Post by 67GTA on 2010-06-10
If you have a windows partition to install it and create the live CD, and prefer an easy to use gui, then paragon backup and recovery free edition is hands down the best I've used. It will back up partitions or whole drives in any file system format to any media. Then boot the live cd up once the new drive is in place and recover the image. I use it about once a month to backup my whole drive just for insurance. It has windows and linux on it. There is also a 64bit version. [http://download.cnet.com/Paragon-Backup-Recovery-Free-Edition-32-bit/3000-2242_4-10972187.html?tag=mncol](http://download.cnet.com/Paragon-Backup-Recovery-Free-Edition-32-bit/3000-2242_4-10972187.html?tag=mncol)

---

