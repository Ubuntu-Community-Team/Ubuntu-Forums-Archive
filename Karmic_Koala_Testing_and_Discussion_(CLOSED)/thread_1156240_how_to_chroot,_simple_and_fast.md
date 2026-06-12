---
title: "how to chroot, simple and fast"
date: 2009-05-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-05-11
Pick up a liveCD, version doesn't matter, you could use any distro, as long as it ables you to enter to console.


# means run with root or sudo

1. Create a mountpoint
```
# mkdir /mount/point
```

2. Mount /proc /sys /dev to chroot
```
# mount -o bind /proc /mount/point/proc
# mount -o bind /dev /mount/point/dev
# mount -o bind /dev/pts /mount/point/dev/pts
# mount -o bind /sys /mount/point/sys 
```

3. Copy resolv.conf to networking
```
# cp /etc/resolv.conf /mount/point/etc/resolv.conf
```

4.Open bash in chroot
```
# chroot /mount/point /bin/bash
```

5. Do what you have to do and then exit chroot
```
exit
```

there may be more elegant way of achieving this, but this one has stuck to me.

Hope this helps someone, this is probably posted on multiple sites, but what the heck, now no need to search around ;)

---

### Post by davideotape on 2009-05-11
May I ask what this is used for and what it actually does?

---

### Post by vade on 2009-05-11
It creates a "jailed" copy of the current operating environment within the current operating environment, so you can run stuff without affecting your main environment.

---

### Post by autocrosser on 2009-05-11
I was just talking in the Hal thread & my script looks very similar......I'll post it this evening---at work right now......

---

### Post by Starks on 2009-05-11
Here's my chroot bash script.

```
#!/bin/bash
mount --bind /dev /media/disk/dev
mount --bind /proc /media/disk/proc
mount --bind /sys /media/disk/sys
mount --bind /dev/pts /media/disk/dev/pts
cp /etc/resolv.conf /media/disk/etc/resolv.conf
chroot /media/disk
```The resolv.conf line is essential for using apt or aptitude to update your packages. Without it, you won't be able to use DNS.

---

### Post by davideotape on 2009-05-11
So you could use it to test new packages then

---

### Post by Reiger on 2009-05-11
Or fix a borked OS, because you get full control over the packages installed in the "jail".

---

### Post by autocrosser on 2009-05-11
Hey Starks---looks like you are using the same one I am---I just point to stuff that's in /mnt --- helps to have 4 drives with 5 OS installs.....

```
#!/bin/bash
sudo mount --bind /dev /mnt/Karmic/dev
sudo mount --bind /proc /mnt/Karmic/proc
sudo mount --bind /sys /mnt/Karmic/sys
sudo cp /etc/resolv.conf /mnt/Karmic/etc/resolv.conf
sudo chroot /mnt/Karmic su
```

---

### Post by taavikko on 2009-05-12
> **Starks said:**
> Here's my chroot bash script.
The resolv.conf line is essential for using apt or aptitude to update your packages. Without it, you won't be able to use DNS.

If modem is providing the DNS then there's no need to copy resolv.conf
At least that I'm aware of.

Case may be different if behind proxy or connected directly to ISP

---

### Post by Starks on 2009-05-12
> **taavikko said:**
> If modem is providing the DNS then there's no need to copy resolv.conf
At least that I'm aware of.

Case may be different if behind proxy or connected directly to ISP

As far as I understand, the resolv.conf step is necessary because the chroot'd environment is isolated from the internet under most circumstances.

---

### Post by taavikko on 2009-05-12
> **Starks said:**
> As far as I understand, the resolv.conf step is necessary because the chroot'd environment is isolated from the internet under most circumstances.

whups, so it seems, had to test. Last time I used chroot was during hardy cycle, 
glibc issue then (major b0rkage).

---

### Post by philinux on 2009-05-12
Ok this sounds good but very new to me. I'm running off Jaunty on disk 1 /dev/sda1. Karmic is on /dev/sdb1. Both have separate home partitions. 

How would I chroot from jaunty to karmic.

---

### Post by taavikko on 2009-05-12
> **philinux said:**
> Ok this sounds good but very new to me. I'm running off Jaunty on disk 1 /dev/sda1. Karmic is on /dev/sdb1. Both have separate home partitions. 

How would I chroot from jaunty to karmic.

It's the same when running from already installed enviroment or liveCD.
Create a mountpoint, bind important system folders, copy resolv.conf and enter chroot, that's it.

/home partition isn't necessary to mount.

---

### Post by philinux on 2009-05-12
> **taavikko said:**
> It's the same when running from already installed enviroment or liveCD.
Create a mountpoint, bind important system folders, copy resolv.conf and enter chroot, that's it.

Sorry for being thick but how does the mount point know it's looking at /dev/sdb1

---

### Post by taavikko on 2009-05-12
> **philinux said:**
> Sorry for being thick but how does the mount point know it's looking at /dev/sdb1


this is when running on jaunty
```
sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
```

Now sdb1 is mounted on /mnt/karmic

---

### Post by philinux on 2009-05-12
> **taavikko said:**
> this is when running on jaunty
```
sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
```

Now sdb1 is mounted on /mnt/karmic

Thanks all is crystal clear now.

---

### Post by Lampi on 2009-05-12
@taavikko: technical question:

if you are you mount-binding the existing filesystems (proc,sys,/dev/pts) from the **non-chrooted** environment to the chrooted environment, couldn't this have side effects e.g. you create or use entries in /sys and /proc that are not valid (or only valid) in the chrooted environment?

I usually chroot first and then mount proc,sys,/dev/pts,/dev/shm in the chrooted environment. After I'm finished I unmount the mount points and then I exit. Like this I thought proc and sys are kept separate from the non-chrootet environment...

Does this make a difference or is it pointless / unnecessary?

---

### Post by Gourgi on 2009-05-12
also have in mind that chrooting in different architectures (eg. i386 to amd64) doesn't work .
i tried that once and it just failed :)

---

### Post by taavikko on 2009-05-12
> **Lampi said:**
> @taavikko: technical question:

if you are you mount-binding the existing filesystems (proc,sys,/dev/pts) from the **non-chrooted** environment to the chrooted environment, couldn't this have side effects e.g. you create or use entries in /sys and /proc that are not valid (or only valid) in the chrooted environment?

I usually chroot first and then mount proc,sys,/dev/pts,/dev/shm in the chrooted environment. After I'm finished I unmount the mount points and then I exit. Like this I thought proc and sys are kept separate from the non-chrootet environment...

Does this make a difference or is it pointless / unnecessary?


I'm no expert regarding to use of chroot, but as to my understanding,
when bind from / to chrooted env, you don't have any possible cruft
that may affect ill-wise.

I've used both ways, and both worked.

Maybe someone more experienced in chroot could provide an answer that may be more to your liking :)

---

### Post by nanog on 2009-05-12
> glibc issue then (major b0rkage)

that was fun!


apart from building dev environments for those who are vm impaired, another major use of chroot is to jail http servers. if done right it can make your server near impervious (my dmz servers are on an .edu domain = thousands of hack attempts a day)

---

### Post by Eclipse. on 2009-09-10
> **Gourgi said:**
> also have in mind that chrooting in different architectures (eg. i386 to amd64) doesn't work .
i tried that once and it just failed :)

i386 live cd is working fine chroot'd into a lpia environment right now.Although both are similar architectures still.

---

### Post by slakkie on 2009-09-15
So how would one also include the any other disk in the jail?

Today I wanted to recover from all the karmic failures by using a chroot, but my /var/log dir is on a seperate slice.

Do I need to mount the slice from within the chroot, or do I do this from outside?

---

### Post by Regenweald on 2009-09-15
Thanks a lot for this thread taavikko and Starks for the script. fumbled a bit but managed to update my system after the upstart breakage. Now i can at least boot into 2.6.31-9 as -10 is still not working.

The prospect of windows for a few days was mightily depressing. Again, this info saved the day on my end.

---

### Post by philinux on 2009-09-15
Thanks to this thread I created my two scripts to do the job.

I always have Jaunty or current stable release on sda1 and the development release on sdb1.

I use two scripts, one to get into chroot and the other to unmount everything. Although a reboot will unmount everything too. Open either with a text editor.

---

### Post by dunbrokin on 2009-10-10
> **taavikko said:**
> Pick up a liveCD, version doesn't matter, you could use any distro, as long as it ables you to enter to console.


# means run with root or sudo

1. Create a mountpoint
```
# mkdir /mount/point
```

2. Mount /proc /sys /dev to chroot
```
# mount -o bind /proc /mount/point/proc
# mount -o bind /dev /mount/point/dev
# mount -o bind /dev/pts /mount/point/dev/pts
# mount -o bind /sys /mount/point/sys 
```

3. Copy resolv.conf to networking
```
# cp /etc/resolv.conf /mount/point/etc/resolv.conf
```

4.Open bash in chroot
```
# chroot /mount/point /bin/bash
```

5. Do what you have to do and then exit chroot
```
exit
```

there may be more elegant way of achieving this, but this one has stuck to me.

Hope this helps someone, this is probably posted on multiple sites, but what the heck, now no need to search around ;)

Is /mount/point a variable here or is it a constant?

---

### Post by kansasnoob on 2009-10-10
> **dunbrokin said:**
> Is /mount/point a variable here or is it a constant?

I start by determining what partition I need to mount. I can usually figure it out by running the command "sudo fdisk -l" and/or looking at the Gparted gui. (You can hose things if you mount and alter the wrong partition.)

My script (slightly different) is here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

If you need help determining which partition to mount someone will help you. Probably at least would need to see the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by ronacc on 2009-10-10
/mount/point is where your existing karmic / is , since you are using a different sys to boot ( your live cd or whatever ) you must mount your existing karmic / and transfer functions to it . you could just use places>computer to mount your existing karmic root and use whatever name it assigns as /mount/point .

---

### Post by slakkie on 2009-10-10
> **philinux said:**
> Thanks to this thread I created my two scripts to do the job.

I always have Jaunty or current stable release on sda1 and the development release on sdb1.

I use two scripts, one to get into chroot and the other to unmount everything. Although a reboot will unmount everything too. Open either with a text editor.

Both your script have an fi where there is no if. So it would b0rk if you run it.

BTW, since we are sharing scripts for chroots:

```

#!/bin/bash

mnt=/mnt/karmic-chroot
root_disk=/dev/sdb1
mnt_devices="proc dev dev/pts sys"

start() {
        sudo mkdir "$mnt"
        sudo mount $root_disk "$mnt"

        for i in $mnt_devices ; do
                sudo mount -o bind /$i "$mnt"/$i
        done

        sudo mv "$mnt"/etc/resolv.conf "$mnt"/etc/resolv.conf.orig
        sudo cp /etc/resolv.conf "$mnt"/etc/resolv.conf
        sudo chroot "$mnt" /bin/bash

}

stop() {
        for i in $mnt_devices; do
                sudo umount "$mnt"/$i
        done
        sudo mv "$mnt"/etc/resolv.conf.orig "$mnt"/etc/resolv.conf
        sudo umount "$mnt"
        sudo rmdir "$mnt"
}

$1


```

---

### Post by dunbrokin on 2009-10-10
> **kansasnoob said:**
> 
```
sudo fdisk -l
```

BTW that's a lower case L.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b53557

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   83  Linux
/dev/sda2           29186       30401     9767520   83  Linux
/dev/sda3           28943       29185     1951897+  82  Linux swap / Solaris
/dev/sda4             244       28942   230524717+   5  Extended
/dev/sda5             244        2675    19535008+  83  Linux
/dev/sda6            2676        5107    19535008+  83  Linux
/dev/sda7            5108       28942   191454606   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x0001e525

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1017     3909317    c  W95 FAT32 (LBA)

---

### Post by ranch hand on 2009-10-10
Just lurking and noticed dunbrokens sig.

Thanks for that, it's good.  I don't chuckle very often when I read those things.

---

### Post by kansasnoob on 2009-10-10
> **dunbrokin said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b53557

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   83  Linux
/dev/sda2           29186       30401     9767520   83  Linux
/dev/sda3           28943       29185     1951897+  82  Linux swap / Solaris
/dev/sda4             244       28942   230524717+   5  Extended
/dev/sda5             244        2675    19535008+  83  Linux
/dev/sda6            2676        5107    19535008+  83  Linux
/dev/sda7            5108       28942   191454606   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x0001e525

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1017     3909317    c  W95 FAT32 (LBA)

I shot this back to your other thread hoping that will be more helpful.

---

