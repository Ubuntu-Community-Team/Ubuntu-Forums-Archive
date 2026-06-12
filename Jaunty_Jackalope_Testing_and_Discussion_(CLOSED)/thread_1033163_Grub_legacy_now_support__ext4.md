---
title: "Grub legacy now support  ext4"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by int on 2009-01-07
Grub legacy now support  ext4, so is very probably that grub2 will not be jaunty default.

> grub (0.97-29ubuntu47) jaunty; urgency=low

 [ Colin King ]

 * New patch, ext4_support now allows grub to boot from ext4 partitions.
   This patch orginated from Quentin Godfroy <godfroy@clipper.ens.fr>

Date: Tue, 06 Jan 2009 17:24:26 +0000
Changed-By: Tim Gardner <tim.gardner@canonical.com>
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
[https://launchpad.net/ubuntu/jaunty/+source/grub/0.97-29ubuntu47](https://launchpad.net/ubuntu/jaunty/+source/grub/0.97-29ubuntu47)

----------------------------------------------------------------------

I'm using **ext4** in the full hard drive '**/**' and work well.

The steps I made:

1º
```

sudo apt-get update
sudo apt-get dist-upgrade

```

2º
Download the ISO of the last svn partition manager that support ext4
[http://beefdrapes.partedmagic.com/](http://beefdrapes.partedmagic.com/)

Burn intro cd/usb-> run It and select: Console

([COLOR="Red"]**note:**[/COLOR] is needed this two comands)
```
tune2fs -O extents,uninit_bg,dir_index /dev/yourfilesystem
fsck -pf /dev/yourfilesystem

```
Done, now your file system is in ext4, but to boot it's need some changes:

3º
```
mkdir drive
mount -t ext4 /dev/yourfilesystem drive/
cd drive
vi etc/fstab
```
change in fstab from ext3 to **ext4** (in yourfilesystem)

4º
```
vi boot/grub/menu.list
```
And add this rootfstype=ext4
```
# kopt=root=UUID=24c707be-c824-4781-89bd-25ed9dba54f8 ro **rootfstype=ext4**
...
...
kernel	/boot/vmlinuz-2.6.28-4-generic UUID=24c707be-c824-4781-89bd-25ed9dba54f8 ro **rootfstype=ext4** quiet splash
```

```
reboot
```
done

There's another thing that must be mentioned. All your existing files will continue using the old indirect mapping to map all the blocks of data. The online defrag tool **will be able to migrate** each one of those files to a extent format (using a ioctl that tells the filesystem to rewrite the file with the extent format; you can use it safely while you're using the filesystem normally)

---

### Post by ShirishAg75 on 2009-01-07
I had seen that one, just somehow forgot to mention it :(

Good observation int

---

### Post by jfernyhough on 2009-01-07
So who will be first to go all ext4 ? :D

---

### Post by Cloud79 on 2009-01-07
Are there any up to date guide on how to do this when running jaunty? Convert existing FS (ext3) to ext4?

---

### Post by plun on 2009-01-07
> **jfernyhough said:**
> So who will be first to go all ext4 ? :D

Well... I wait..:D  

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

I got strange errors from my EXT4 test partition and an "automagic" fsck run....:confused: (35 times boot)

---

### Post by pressureman on 2009-01-07
> **Cloud79 said:**
> Are there any up to date guide on how to do this when running jaunty? Convert existing FS (ext3) to ext4?

Unless your existing ext3 partition has 256-byte inodes, I wouldn't recommend an in-place upgrade.

I think starting with Intrepid, the installer defaulted to creating ext3 with 256-byte inodes (except for small partitions like /boot). A recent Intrepid server install I did has 256-byte inodes, even though I did nothing special to select it.

PS: I've been running ext4 on my laptop for about a week now (separate ext3 /boot partition), and not noticed any errors. It's certainly faster at creating large numbers of small files, deleting large files, and just writing to disk in general. The partition has been mounted 16 times so far (automatic fsck at 37)... will cross my fingers. In any case, with "uninit_bg" enabled, fsck runs waaaay faster (proportional to % of partition used).

---

### Post by pressureman on 2009-01-07
> **Cloud79 said:**
> Are there any up to date guide on how to do this when running jaunty? Convert existing FS (ext3) to ext4?

Maybe start here: [http://kernelnewbies.org/Ext4#head-634429ff2676cfc0e86fe9acd7bfa1d2237f2910](http://kernelnewbies.org/Ext4#head-634429ff2676cfc0e86fe9acd7bfa1d2237f2910)

I enabled a few more feature flags than the article describes (see /etc/mke2fs.conf for the default flags used when creating an ext4 filesystem)

---

### Post by plun on 2009-01-07
New util-linux is coming....

> util-linux (2.14-1ubuntu3) jaunty; urgency=low

  * debian/rules: Install rules into /lib/udev/rules.d instead
  * debian/util-linux.dirs: Create new location, don't create old.
  * debian/util-linux.preinst: Remove the old rules if unmodified.


Also other packages as it looks because of this change....


Downgrade Grub2....:confused::P

---

### Post by jfernyhough on 2009-01-07
This bit looks interesting:

> Mount an existing Ext3 filesystem with Ext4 without changing the format

You can mount an existing Ext3 filesystem with Ext4 but without using features that change the disk format. This means you will be able to mount your filesystem with Ext3 again. You can mount an existing Ext3 filesystem with "mount -t ext4 /dev/yourpartition /mnt". Doing this without having done the conversion process described in the previous point will force Ext4 to not use the features that change the disk format, such as extents, it will use only the features that don't change the file format, such as mballoc or delayed allocation. You'll be able to mount your filesystem as Ext3 again. But obviously you'll be losing the advantages of the Ext4 features that don't get used... 

Annoyingly my Jaunty laptop is on the blink (my nice new one... hard drive is not spinning up...). I wonder if this will work in Intrepid (which is installed on my work laptop) - does Intrepid have ext4 support?

Hmm...
```
j@worklaptop:~$ locate ext4
/lib/modules/2.6.27-11-generic/kernel/fs/ext4
/lib/modules/2.6.27-11-generic/kernel/fs/ext4/ext4dev.ko
--snip--
```
Let's see what happens. :D Editing my fstab and changing from ext3 to ext4...

---

### Post by ShirishAg75 on 2009-01-07
Don't know really, it is certainly becoming easier with jaunty with 2.6.28 giving us all the bits really needed, not to say now grub as well. Only things left are e2fsprogs and ubiquity (from end-users point of view)

Although dunno what happens to this bug then [lpbug]197311[/lpbug]

---

### Post by jfernyhough on 2009-01-07
Hmm..

Apparently (of two partitions) my / mounted as ext4, but when it tried to mount /home it complained that ext4 is an unknown filesystem type (so I had to specify ext3 to get it to mount).

I don't understand. :D

```
/dev/sda1 on / type ext4 (rw,noatime,nodiratime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda2 on /home type ext3 (rw,noatime,nodiratime)

```

---

### Post by plun on 2009-01-07
> **jfernyhough said:**
> Let's see what happens. :D Editing my fstab and changing from ext3 to ext4...

Have you run the tunefs command... ?


This is my fstab  (also includes a dynamic swap)

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=431b36fe-46dd-4ee6-94ce-ab65eabdc770 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda4 :
UUID=ea60a35d-3a50-4b02-8eda-60da18ad08fd /home ext3 relatime 0 2
[B]# Entry for /dev/sda3 :
UUID=1bd53d0e-a190-4358-a24f-cdea59941581 /media/Min ext4 relatime 0 2[/B]


/dev/sda1 /media/NTFS ntfs-3g defaults,locale=en_US.UTF-8 0 0


# a swapfile is not a swap partition, so no using swapon|off from here on, use  dphys-swapfile swap[on|off]  for that


> plun@plun:~$ sudo blkid
/dev/sda1: UUID="9E7864E67864BEA1" TYPE="ntfs" 
/dev/sda2: UUID="431b36fe-46dd-4ee6-94ce-ab65eabdc770" TYPE="ext3" 
**/dev/sda3: UUID="1bd53d0e-a190-4358-a24f-cdea59941581" TYPE="ext4"** 
/dev/sda4: UUID="ea60a35d-3a50-4b02-8eda-60da18ad08fd" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="BABA-9F89" TYPE="vfat" 


---

### Post by jfernyhough on 2009-01-07
> **plun said:**
> Have you run the tunefs command... ?Nope:

> You can **mount an existing Ext3 filesystem with Ext4 **but without using features that change the disk format. This means you will be able to mount your filesystem with Ext3 again. **You can mount an existing Ext3 filesystem with "mount -t ext4 /dev/yourpartition /mnt"**. Doing this without having done the conversion process described in the previous point will force Ext4 to not use the features that change the disk format, such as extents, **it will use only the features that don't change the file format**, such as mballoc or delayed allocation. You'll be able to mount your filesystem as Ext3 again. But obviously you'll be losing the advantages of the Ext4 features that don't get used...In theory it should work. But then I'm trying this on Intrepid. :D

---

### Post by plun on 2009-01-07
> **jfernyhough said:**
> Nope:

In theory it should work. But then I'm trying this on Intrepid. :D

For a existing EXT3 partition it must be done, I did it a month ago...

```
tune2fs -O extents -E test_fs /dev/DEV

```


**In my case**

```
plun@plun:~/$ sudo tune2fs -O extents -E test_fs /dev/sda3
tune2fs 1.41.3 (12-Oct-2008)
**Setting test filesystem flag**


```


**test_fs**  :confused:




[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)


I have not tested with a new partition directly created to Ext4...
(also about that within the wiki)

:)

---

### Post by jfernyhough on 2009-01-07
But that's converting from ext3 to ext4 isn't it? I thought it was possible to mount ext3 as ext4 but just lose certain features - plus if my ext3 root can be mounted as ext4 why can't my /home?

Unless it's lying, detecting the / as ext3 but mount reporting ext4, though in reality it's actually mounted as ext3...

---

### Post by plun on 2009-01-07
> **jfernyhough said:**
> But that's converting from ext3 to ext4 isn't it? I thought it was possible to mount ext3 as ext4 but just lose certain features - plus if my ext3 root can be mounted as ext4 why can't my /home?

Unless it's lying, detecting the / as ext3 but mount reporting ext4, though in reality it's actually mounted as ext3...

No it must be converted or created as a EXT4 as I understands it...:confused:

If you converts it, its forever EXT4.

When you then reboots fsck comes in and sets EXT4, takes a couple of minutes during a boot first time.

BUT...

> NOTE: by doing so, new files will be created in extents format, but this will not convert existing files. However, they can be transparently read from and written to in the old ext3 format.

WARNING: Once the extent feature has been turned on, the filesystem will no longer be mountable using the ext3 filesystem! 

Its room for more facts....:D

---

### Post by jfernyhough on 2009-01-07
I rebooted to without quiet and splash to check stuff - and it's as I suspected my / was being detected and mounted as ext3 but mount was telling lies about it being mounted as ext4. Obviously I need to get my other laptop fixed so I can test in Jaunty. :D

---

### Post by Slug71 on 2009-01-07
I think i mentioned it a while back maybe at launchpad or in the Ext4 thread that Ext4 could now be booted by Grub Legacy. Apparently it was just a bug. I'm already using Grub2 anyway and works well for me. 
Just waiting for Ext4 to make its way to the installer now. Dont want to convert my Ext3 to Ext4.

---

### Post by Slug71 on 2009-01-07
> **ShirishAg75 said:**
> Don't know really, it is certainly becoming easier with jaunty with 2.6.28 giving us all the bits really needed, not to say now grub as well. Only things left are e2fsprogs and ubiquity (from end-users point of view)

Although dunno what happens to this bug then [lpbug]197311[/lpbug]

As far as i know e2fsprogs in Jaunty is fine.

---

### Post by gnomeuser on 2009-01-07
The ubuntu mailing list reveals that Tim Gardner has been using ext4 on his machines for a little while now with very positive results. Maybe that means we will at least get it as an option if not the default in Jaunty.

---

### Post by ShirishAg75 on 2009-01-07
link to that mailing post would have been nice.

---

### Post by gnomeuser on 2009-01-07
> **ShirishAg75 said:**
> link to that mailing post would have been nice.

As the posting contains guides on how to migrate to ext4 I considered it wisest to let the people who know how to seek information do so. Additionally it's one developer reporting back on a test, we have seen that before, hell Fedora has allowed installation onto ext4 since Fedora 9. Ext4 is stable, it's just a matter of time before the switch gets thrown. 

Regardless, let the foot shooting begin - please do not follow the guide within unless you are absolutely, positively sure what you are doing.

[https://lists.ubuntu.com/archives/kernel-team/2008-December/003986.html](https://lists.ubuntu.com/archives/kernel-team/2008-December/003986.html)

---

### Post by castrojo on 2009-01-07
I put my /home in ext4 shortly after Ted's talk at UDS.

Asking around the common answer seems to be "in jaunty, not by default", but that will depend on what gets done between now and feature freeze.

---

### Post by int on 2009-01-07
I'm using **ext4** in the full hard drive '**/**' and work well.

The steps I made:

1º
```

sudo apt-get update
sudo apt-get dist-upgrade

```

2º
Download the ISO of the last svn partition manager that support ext4
[http://beefdrapes.partedmagic.com/](http://beefdrapes.partedmagic.com/)

Burn intro cd/usb-> run It and select: Console

([COLOR="Red"]**note:**[/COLOR] is needed this two comands)
```
tune2fs -O extents,uninit_bg,dir_index /dev/yourfilesystem
fsck -pf /dev/yourfilesystem

```
Done, now your file system is in ext4, but to boot it's need some changes:

3º
```
mkdir drive
mount -t ext4 /dev/yourfilesystem drive/
cd drive
vi etc/fstab
```
change in fstab from ext3 to **ext4** (in yourfilesystem)

4º
```
vi boot/grub/menu.list
```
And add this rootfstype=ext4
```
# kopt=root=UUID=24c707be-c824-4781-89bd-25ed9dba54f8 ro **rootfstype=ext4**
...
...
kernel	/boot/vmlinuz-2.6.28-4-generic UUID=24c707be-c824-4781-89bd-25ed9dba54f8 ro **rootfstype=ext4** quiet splash
```

```
reboot
```
done

There's another thing that must be mentioned. All your existing files will continue using the old indirect mapping to map all the blocks of data. The online defrag tool **will be able to migrate** each one of those files to a extent format (using a ioctl that tells the filesystem to rewrite the file with the extent format; you can use it safely while you're using the filesystem normally)

---

### Post by MacUntu on 2009-01-07
Any experience with the online-defragmentation feature yet?

---

### Post by jfernyhough on 2009-01-07
I think I read that the online defragmenter doesn't exist yet.

Yes, indeed I did: [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)
> Online defragmentation

(This feature is not available in 2.6.28, but will be probably available in the next release)

---

### Post by MacUntu on 2009-01-07
My bad, thanks for the link!

---

### Post by Gina on 2009-01-08
Thanks ***int*** - I'll have a go as soon as I get the time :)

---

### Post by Archmage on 2009-01-08
> **Slug71 said:**
> Just waiting for Ext4 to make its way to the installer now. Dont want to convert my Ext3 to Ext4.

Any idea when this will happen?

---

### Post by FarJumper on 2009-01-08
Is there ability to convert ext3 to ext4 without using liveCD distibutives? I believe it is possible to use runlevel 1 and unmount root partition (I have got only one partition for everything: boot, root and home).

---

### Post by int on 2009-01-08
> **FarJumper said:**
> Is there ability to convert ext3 to ext4 without using liveCD distibutives? I believe it is possible to use runlevel 1 and unmount root partition (I have got only one partition for everything: boot, root and home).

If you have this **tune2fs, fsck** at runlevel 1.

---

### Post by FarJumper on 2009-01-08
> **int said:**
> If you have this **tune2fs, fsck** at runlevel 1.

When I trying to umount root partition it doesn't produce any errors but the root is still visible in `mount` and `df`. It's necessary to unmount root partition before applying tune2fs and fsck?

---

### Post by int on 2009-01-08
> **FarJumper said:**
> When I trying to umount root partition it doesn't produce any errors but the root is still visible in `mount` and `df`. It's necessary to unmount root partition before applying tune2fs and fsck?
Yes, it's. You need to have the filesystem unmounted.

---

### Post by MacUntu on 2009-01-08
You could kill your partition if you fsck it while mounted!

---

### Post by Gina on 2009-01-08
To do anything like fsck or change format or such you need to have the filesystem unmounted which means you need to be running a different (separate) system) - either a LiveCD etc. or another system on your hard drive.  A system has to be mounted to "run" it.

(Sorry I don't think that reads quite right but I hope the meaning is clear).

---

### Post by FarJumper on 2009-01-08
> **MacUntu said:**
> You could kill your partition if you fsck it while mounted!

Even if it's RO?

I still have no idea how to unmount root partition beeing runlevel 1. `umount /dev/sdx` doesn't work. Partition is still here after invoking this command.

---

### Post by plun on 2009-01-08
Yup... and you also cannot convert existing files on a partition, just new files will have "full" EXT4. 

I cannot see "the easy way" for this yet....:confused::D

---

### Post by antiram on 2009-01-08
copy this tune2fs and fsck in initrd and reboot without kernel parameter root=..

then you come in the buildin kernel shell to make the transition

---

### Post by ShirishAg75 on 2009-01-08
On the road to ext4 

> 
initramfs-tools (0.92bubuntu18) jaunty; urgency=low

  * Add ext4 to the initramfs, in case it stops being built into the kernel.
[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002726.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002726.html)

Another update, this time to e2fsprogs 

> 
e2fsprogs (1.41.3-1ubuntu2) jaunty; urgency=low

  * Install mkfs.ext4 symlink in e2fsprogs-udeb.


[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002731.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002731.html)

---

### Post by plun on 2009-01-08
And parted supporting EXT 4...

> parted (1.8.8.git.2008.03.24-11.1ubuntu2) jaunty; urgency=low

  * ext4.dpatch: Add skeletal ext4 support.
  * dm-null-target.dpatch: Fix segfault in case DM_DEVICE_TABLE returns no
    targets.

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002734.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002734.html)



gparted must also be around somewhere...

---

### Post by ShirishAg75 on 2009-01-08
dang, you got before me, yes gparted remains, what else i wonder before ubiquity can function.

---

### Post by ShirishAg75 on 2009-01-08
Dang, you got first there, I wonder what else is remaining (apart from ubiquity) for jaunty to have ext4 as an option.

---

### Post by int on 2009-01-08
error (deleted)

---

### Post by int on 2009-01-08
error (deleted)

---

### Post by int on 2009-01-08
error (deleted)

---

### Post by int on 2009-01-08
error (deleted)

---

### Post by int on 2009-01-08
error (deleted)

---

### Post by int on 2009-01-08
error (deleted)

---

### Post by int on 2009-01-08
> **plun said:**
> gparted must also be around somewhere...
the author not release yet the ext4 version..
[http://svn.gnome.org/viewvc/gparted/trunk/ChangeLog?view=markup](http://svn.gnome.org/viewvc/gparted/trunk/ChangeLog?view=markup)
when gparted-0.4.2 goes out.

Will be one e4defrag soon..

```
partman-partitioning (64ubuntu2) jaunty; urgency=low

 * Add ext4 support (LP: #293465).

Date: Thu, 08 Jan 2009 16:55:00 +0000
Changed-By: Colin Watson <cjwatson@ubuntu.com>
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Signed-By: Colin Watson <cjwatson@canonical.com>
https://launchpad.net/ubuntu/jaunty/+source/partman-partitioning/64ubuntu2
```

---

### Post by Slug71 on 2009-01-08
Woohoo! Ext4 in the Daily build tomorrow. :D

---

### Post by gnomeuser on 2009-01-08
According to Colin Watson a Jaunty Daily from Jan 9th should allow you to install optionally directly on ext4. Welcome to the dawn of a new age and to my regret for installing Jaunty yesterday instead of waiting.

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-January/006641.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-January/006641.html)

---

### Post by autocrosser on 2009-01-08
I've started converting--have both storage drives as EXT4 now & will convert the rest as soon as it looks "all clear"

---

### Post by Artemis3 on 2009-01-14
I wonder if its worth dealing with ext4 when btrfs seems around the corner?

---

### Post by Slug71 on 2009-01-14
> **Artemis3 said:**
> I wonder if its worth dealing with ext4 when btrfs seems around the corner?

I think btrfs will still be at least a year before its ready for use.

---

