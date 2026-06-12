---
title: "changing software install directories"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by slifin on 2010-01-06
hello there I wanted to know if it was possible to move the software install directory from the main drive to a secondary drive 

I am using a ubuntu fork (mint linux) with a eee pc the primary drive is very small at around 3GB I've added my second drive to the fstab file in etc so it mounts on start up is there anyway I can make programs install to that second drive or to move my current applications to that drive?

regards :)

---

### Post by sanderd17 on 2010-01-06
I think this is quite dangerous with a completed installation. I would rather recommand to move your files in your home directory to another disk.

you can find a tutorial for it right [here]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/"). If you want to try installing programs on an other hard disk, you can adapt this tutorial to your needs but as said: it can be quite dangerous.

hope I helped

---

### Post by mocoloco on 2010-01-06
You could have your new drive mount as /usr.  You would need to copy over the contents of your existing /usr folder exactly for it to work.  That's the beauty of Linux, the filesystem doesn't care what drive things are on, just where they show up in the file hierarchy.

---

### Post by slakkie on 2010-01-06
> **mocoloco said:**
> You could have your new drive mount as /usr.  You would need to copy over the contents of your existing /usr folder exactly for it to work.  That's the beauty of Linux, the filesystem doesn't care what drive things are on, just where they show up in the file hierarchy.

What he is saying:

1) create a new partition: 
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

2) Mount the disk

sudo mount /dev/sdbX /mnt/

3) copy the contents over
sudo cp -rp /usr/* /mnt/

3) Then get the UUID of the new disk: sudo blkid
Write that down, 

4) Then add it to your /etc/fstab:

```

UUID=2713699d-231d-4e8b-9484-5450cededef3 /usr               ext3    defaults 0       1

```

The UUID is of course the output you got from blkid.

Then reboot and everthing should be there

The only issue you might have is that the files are still present on your old / partition. I prefer to use a livecd, mount the root disk of your OS, and remove /usr from there.

Others mount the root disk to some other mountpoint and then remove the old /usr.

The choice is yours.

---

