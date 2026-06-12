---
title: "disk space problem"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Nazaroo on 2010-03-16
I had ubuntu 9.01 and system got messed up so I installed 9.10 from a cd.

I left the old OS on the drive to save critical files like data, firefox bookmarks etc.

I recovered most of my stuff.  The old OS took up about 6 gig on the drive, it shows up as a folder (apparently not as a partition).

I deleted most of the directories out of the old system, and seemed to recover about 5 or 6 gig of diskspace.

However, only a few hours into the new install, I am getting disk-low message, and then if I "examine", Disk Usage Analyzer opens up, and says my total filesystem capacity is only 3.2 Gig (used: 3.0 GB available: 210.6 MB).

This can't be right.  When I use /PLACES/COMPUTER from the dropdown menu, the old area is called "6.1 GB Filesystem" and  shows up with a "Drive" icon beside it.  The (active) root just looks like a folder at the top.

The space in this "drive/folder" is nearly empty, so why can't my new system just see the free space and use it?

Can I physically move the thing into one of the new /root/ or / folders? 

What do I have to do to make the OS find and use the space like it does the rest of the drive?

"worried about another crash",
Nazaroo

ps., following a tip in another thread, I opened a terminal and got this:
> root@unknown:~# sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00041ed1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         736     5911888+  83  Linux
/dev/sda2             737        1245     4088542+   5  Extended
/dev/sda5            1188        1245      465853+  82  Linux swap / Solaris
/dev/sda6             737        1160     3405717   83  Linux
/dev/sda7            1161        1187      216846   82  Linux swap / Solaris



I think sda6 is my new OS, and and sda1 or sda2 is the old one (but not sure)...

---

### Post by perham on 2010-03-16
> **Nazaroo said:**
> I had ubuntu 9.01 and system got messed up so I installed 9.10 from a cd.

I left the old OS on the drive to save critical files like data, firefox bookmarks etc.

I recovered most of my stuff.  The old OS took up about 6 gig on the drive, it shows up as a folder (apparently not as a partition).

I deleted most of the directories out of the old system, and seemed to recover about 5 or 6 gig of diskspace.

However, only a few hours into the new install, I am getting disk-low message, and then if I "examine", Disk Usage Analyzer opens up, and says my total filesystem capacity is only 3.2 Gig (used: 3.0 GB available: 210.6 MB).

This can't be right.  When I use /PLACES/COMPUTER from the dropdown menu, the old area is called "6.1 GB Filesystem" and  shows up with a "Drive" icon beside it.  The (active) root just looks like a folder at the top.

The space in this "drive/folder" is nearly empty, so why can't my new system just see the free space and use it?

Can I physically move the thing into one of the new /root/ or / folders? 

What do I have to do to make the OS find and use the space like it does the rest of the drive?

"worried about another crash",
Nazaroo

post the output of these commands:

```
sudo fdisk -l
```
```
cat /etc/fstab
```
```
cat /etc/mtab
```
 
and I'll help you with adding that space to your root partition. in fact, that space is now in another partition, it just mounts it. to know more about linux filesystem structure click [here]("http://www.tuxfiles.org/linuxhelp/dirs.html") and [here]("http://linux.about.com/od/nwb_guide/a/gdenwb01t51.htm")

---

### Post by Nazaroo on 2010-03-16
I was already reading another post, and tried this:
> root@unknown:~# sudo blkid -c /dev/null

/dev/sda1: UUID="3dae119e-1ae1-416c-a770-4eb01de1f729" TYPE="ext3" 
/dev/sda5: UUID="b11f96e3-e5de-409d-a7c5-e07310ffe4f6" TYPE="swap" 
/dev/sda6: UUID="a79da916-2d5e-4f48-8230-a80565ea5eaa" TYPE="ext4" 
/dev/sda7: UUID="28b68bc2-05e6-4fb6-90f8-82831243314b" TYPE="swap" 
/dev/sdb: TYPE="promise_fasttrack_raid_member" 
/dev/mapper/pdc_ghijffhf1: LABEL="LINUX SYSTEM" UUID="e6208b2f-0b61-436f-a005-212a4d061d2c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/pdc_ghijffhf2: UUID="6A98166B981635D3" LABEL="Secured 01" TYPE="ntfs" 
/dev/mapper/pdc_ghijffhf3: UUID="8A5C91395C91214D" LABEL="Secured 02" TYPE="ntfs" 
/dev/mapper/pdc_ghijffhf4: UUID="b9178744-7db1-486d-9734-107a5f61c1db" TYPE="swap" 


Then I tried this:
> root@unknown:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda6 during installation
UUID=a79da916-2d5e-4f48-8230-a80565ea5eaa  /               ext4         errors=remount-ro         0  1  
# swap was on /dev/sda7 during installation
UUID=28b68bc2-05e6-4fb6-90f8-82831243314b  none            swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sda5                                  /media/sda5     swap         sw                        0  0  
/dev/sda1                                  /media/sda1     ext3         errors=remount-ro         0  0  
root@unknown:~# 


Then I tried this:

> root@unknown:~# mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type ext3 (rw,errors=remount-ro)
root@unknown:~#

There is another data drive on system, with some windows partitions.

here is the last command:
> root@unknown:~# cat /etc/mtab
/dev/sda6 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
/dev/sda1 /media/sda1 ext3 rw,errors=remount-ro 0 0
root@unknown:~# 


---

### Post by Nazaroo on 2010-03-16
By the way, what brought this crash on in the first place was some kind of /tmp space being full..

I wish I could set that thing large enough to play videos and not worry about downloading big pics on the net...

Here is the 1st FDISK cmd output, incase we didn't get it in full:

> root@unknown:~# fdisk -l

Disk /dev/sda: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00041ed1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         736     5911888+  83  Linux
/dev/sda2             737        1245     4088542+   5  Extended
/dev/sda5            1188        1245      465853+  82  Linux swap / Solaris
/dev/sda6             737        1160     3405717   83  Linux
/dev/sda7            1161        1187      216846   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84a384a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1114     8948173+  83  Linux
/dev/sdb2            1246        4050    22531162+  17  Hidden HPFS/NTFS
/dev/sdb3            4051        7301    26113657+  17  Hidden HPFS/NTFS
/dev/sdb4            1115        1245     1052257+  82  Linux swap / Solaris

Partition table entries are not in disk order
root@unknown:~#

The second drive is just a data drive, and seems to work fine.

Nazaroo


Nazaroo

---

### Post by perham on 2010-03-16
> **Nazaroo said:**
> I was already reading another post, and tried this:


Then I tried this:


Then I tried this:



There is another data drive on system, with some windows partitions.

here is the last command:

according to the information above, you have your system partition on /dev/sda6 and the current swap at /dev/sda7. your free partitions are on /dev/sda1 and /dev/sda7 (unnecessary swap). if this is the case, here's the guide to how to merge that space. note that we need the livecd for, and since we're changing the partitions, we may need to reconfigure grub. please don't do anything unless you double check that you have a backup of your important data. there's a risk that your data may get deleted.

boot from livecd, then:

1. open gparted from System -> Administration -> GParted
2. choose /dev/sda from top right if it's not already on it.
3. right click on /dev/sda1 and /dev/sda7 and click unmount if they are mounted.
4. right click on /dev/sda1 and /dev/sda7 and choose delete partition.
5. right click on /dev/sda2 (Extended) and choose Resize Partition. make it fill the whole space. 
6. right click on /dev/sda6 and resize it to fill the whole space.
7. check if uuid has changed by sudo blkid and comparing the value to the one you provided here.
8. customize grub as it should. here's the guides for that: [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)


be sure that you know everything about bringing the system up after uuid changes before going into steps.

I hope this helps.

---

### Post by Nazaroo on 2010-03-16
ok now that I've read some of the GRUB stuff, (and spent 24 hrs restoring my OS), I think I need to know how to back up my system (while its still working)...

I will have to do this first I think...

Thanks for you help.  I will be back shortly after backing up files.

---

### Post by Nazaroo on 2010-03-16
> **perham said:**
> according to the information above, you have your system partition on /dev/sda6 and the current swap at /dev/sda7. your free partitions are on /dev/sda1 and /dev/sda7 (unnecessary swap). if this is the case, here's the guide to how to merge that space. note that we need the livecd for, and since we're changing the partitions, we may need to reconfigure grub. please don't do anything unless you double check  .

Just one more problem:

You have listed sda7 twice, once as current swap, and once as an (unnecessary 2nd? swap).:confused:

Which swap is which?  I don't want to mess that up either....

I have deleted some data files and now have 65 MB of space on the system drive/partition.
That isn't very much, and I 'm still concerned about crashing...I don't dare delete anything else. 

But can I delete source files from the system?  Will that free up a significant amount of space temporarily, or alternately, can I back them up on the other drive, and put them back later? Are they needed, or only needed when I run the SYnaptic Package Manager?




thanks in advance, 
Nazaroo

---

### Post by perham on 2010-03-16
> **Nazaroo said:**
> Just one more problem:

You have listed sda7 twice, once as current swap, and once as an (unnecessary 2nd? swap).:confused:

Which swap is which?  I don't want to mess that up either....

I have deleted some data files and now have 65 MB of space on the system drive/partition.
That isn't very much, and I 'm still concerned about crashing...I don't dare delete anything else. 

But can I delete source files from the system?  Will that free up a significant amount of space temporarily, or alternately, can I back them up on the other drive, and put them back later? Are they needed, or only needed when I run the SYnaptic Package Manager?




thanks in advance, 
Nazaroo

well, you have sda7 as current swap, but you have two more swap partitions, sdb4 and sda5. they will cover the swap problem. in fact, if sdb4 is on a internal HDD, you can also safely remove sda5, since sda5+sda7 ~ 400MB but sdb4 is 1GB+, so, really, there shouldn't be any problem.

you can free up some space by running "sudo apt-get clean" which clears your downloaded .deb cache.

---

### Post by Nazaroo on 2010-03-16
I think sudo apt-get clean did something, because now I have 221 Mb of freespace.

Still, not enough I fear.   I like the idea of having the swapdisk on the other drive (and its larger size).   If deleting the others frees up space, can it be recovered for the OS?

What am I missing here?

Can I just assign these spaces to virtual folders, or assign system folders to these spaces?


Nazaroo

---

### Post by Nazaroo on 2010-03-16
I am going to try this...are these steps actually exact?

> 
boot from livecd, then:

1. open gparted from System -> Administration -> GParted
2. choose /dev/sda from top right if it's not already on it.
3. right click on /dev/sda1 and /dev/sda7 and click unmount if they are mounted.
4. right click on /dev/sda1 and /dev/sda7 and choose delete partition.
5. right click on /dev/sda2 (Extended) and choose Resize Partition. make it fill the whole space. 
6. right click on /dev/sda6 and resize it to fill the whole space.
7. check if uuid has changed by sudo blkid and comparing the value to the one you provided here.


8. customize grub as it should. here's the guides for that: [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)


be sure that you know everything about bringing the system up after uuid changes before going into steps.

I hope this helps.                                                                                                                   I'm still confused about step 8.  ....



What exactly will that involve?

actually, step 7.  completely escapes me.  What am I doing there?




Nazaroo

---

### Post by perham on 2010-03-16
> **Nazaroo said:**
> I think sudo apt-get clean did something, because now I have 221 Mb of freespace.

Still, not enough I fear.   I like the idea of having the swapdisk on the other drive (and its larger size).   If deleting the others frees up space, can it be recovered for the OS?

What am I missing here?

Can I just assign these spaces to virtual folders, or assign system folders to these spaces?


Nazaroo

we're gonna resize your root partition, so that it actually occupies the whole disk (10GB). so. we're gonna remove both swaps, and /dev/sda1 which was your old ubuntu installation. that will recover lots of space for your OS. so no virtual assignment (mounting) is needed.

---

### Post by perham on 2010-03-16
> **Nazaroo said:**
> I am going to try this...are these steps actually exact?



I tried to be as exact as I can be, but double check yourself. it's actually easy. consider it like this: you'll open gparted in the live CD. there's an ext3 partition on /dev/sda6, that's your root partition. there's an extended partition which your sda5 sda6 and sda7 partitions are below it. first we need to remove sda1, sda5 and sda7, then resize the extended partition to the whole disk, and then resize your root partition (sda6) to fill the whole extended partition.

btw, which version of grub are you using? when you boot, what version does it mention in the title of the menu?


> 
I'm still confused about step 8.  ....



What exactly will that involve?

actually, step 7.  completely escapes me.  What am I doing there?

Nazaroo

please first check your grub version, then I'll tell you exactly what we'll do. ;)

---

### Post by Nazaroo on 2010-03-16
The Grub window says at the top:  GRUB 1.97~beta 4

there is a window with about a dozen choices, but I always take the first one, which is the new OS...

one more quick question: is the "live CD" the same thing as the Ubuntu 9.10 install CD?  It does seem to boot into a GUI and OS if I boot off it...


thanks! 
nazaroo

---

### Post by perham on 2010-03-16
> **Nazaroo said:**
> The Grub window says at the top:  GRUB 1.97~beta 4

there is a window with about a dozen choices, but I always take the first one, which is the new OS...

one more quick question: is the "live CD" the same thing as the Ubuntu 9.10 install CD?  It does seem to boot into a GUI and OS if I boot off it...


thanks! 
nazaroo

yes, it's the same. it's called live cd because you can boot into the OS without installing it. 


about the steps 7 and 8, we need to reconfigure grub boot menu. we only need to run "update-grub" and voila! so, after you did everything and resized your root partition, run "sudo blkid". you should see a partition starting with /dev/sda. for example, /dev/sda6. write down the name somewhere. 

now open a terminal, and do these steps (swap /dev/sdXX with the name you got up there):


```
sudo mkdir /recdir

```
Mount your normal system partition:
   
```
sudo mount /dev/sdXX /recdir

```

Create CHROOT environment
```

sudo mount --bind /dev/ /recdir/dev
sudo mount --bind /usr/ /recdir/usr
sudo mount --bind /proc/ /recdir/proc
sudo chroot /recdir


```
and finally, run update-grub
```


update-grub

```

now reboot. you should have your system up and working. ;)

---

### Post by Nazaroo on 2010-03-17
Good thing I waited till this morning to do this!

I see you edited your last instructions an hour ago.

I have noted the changes, (/mnt -> /recdir)

Are the first set of instructions still accurate?  

I am hoping you'll double-check those too:

Particularly, no. 7 is rather opaque....  What is a "uuid" and a "blkid"?

thank you for your help so far, 
Nazaroo

---

### Post by perham on 2010-03-17
> **Nazaroo said:**
> Good thing I waited till this morning to do this!

I see you edited your last instructions an hour ago.

I have noted the changes, (/mnt -> /recdir)

Are the first set of instructions still accurate?  

I am hoping you'll double-check those too:

Particularly, no. 7 is rather opaque....  What is a "uuid" and a "blkid"?

thank you for your help so far, 
Nazaroo

this should be the whole set of instructions, act based on these two paragraphs:

>  it's actually easy. consider it like this: you'll open gparted in the live CD. there's an ext3 partition on /dev/sda6, that's your root partition. there's an extended partition which your sda5 sda6 and sda7 partitions are below it. first we need to remove sda1, sda5 and sda7, then resize the extended partition to the whole disk, and then resize your root partition (sda6) to fill the whole extended partition.

> about the steps 7 and 8, we need to reconfigure grub boot menu. we only need to run "update-grub" and voila! so, after you did everything and resized your root partition, run "sudo blkid". you should see a partition starting with /dev/sda. for example, /dev/sda6. write down the name somewhere. 

now open a terminal, and do these steps (swap /dev/sdXX with the name you got up there):


```
sudo mkdir /recdir

```
Mount your normal system partition:
   
```
sudo mount /dev/sdXX /recdir

```

Create CHROOT environment
```

sudo mount --bind /dev/ /recdir/dev
sudo mount --bind /usr/ /recdir/usr
sudo mount --bind /proc/ /recdir/proc
sudo chroot /recdir


```
and finally, run update-grub
```


update-grub

```

now reboot. you should have your system up and working. ;)

---

### Post by Nazaroo on 2010-03-17
here is what happened.

I figured out that the GParted program had to write changes and got it to start.

It got to 7 out of 10 steps and stalled.

But after repartitioning (resizing the partition to whole space) it seemed to work fine.

Then I followed your instructions above.

GRUB gave an error message too.
> 
Found linux image: /boot/vlnlunx....
Found initrd image: /boot/...
Found memtest image: /boot/...
CANNOT FIND LIST OF Partitions!
DONE.

Booting gave the following messages:
> 
booting from local disk...
GRUB loading.
Error: no such partition.
grub rescue>

At this screen I tried a few commands, nothing worked, but ls gave me this:
> 
(hd0) (hd0,5)

I rebooted off the Live CD/install to get here.

Now how can I make my system (which is all set up for monitors etc. so I don't want to waste another day reconfiguring it again) bootable?

sincerely,
Nazaroo

:confused:

---

### Post by perham on 2010-03-18
> **Nazaroo said:**
> here is what happened.

I figured out that the GParted program had to write changes and got it to start.

It got to 7 out of 10 steps and stalled.

But after repartitioning (resizing the partition to whole space) it seemed to work fine.

Then I followed your instructions above.

GRUB gave an error message too.


Booting gave the following messages:


At this screen I tried a few commands, nothing worked, but ls gave me this:

I rebooted off the Live CD/install to get here.

Now how can I make my system (which is all set up for monitors etc. so I don't want to waste another day reconfiguring it again) bootable?

sincerely,
Nazaroo

:confused:
ok, now at grub rescue prompt, run these commands one by one to get into your system:

press tab when you see [TAB]. you may see multiple entries,just go for the most recent. something like vmlinuz-2.6.31-20-generic and initrd.img-2.6.31-20-generic. just keep in mind that vmlinuz's and initrd's version should match.

```
set root=(hd0,5)
linux  /boot/vmlinuz-[TAB] root=/dev/sda5 quiet splash  
initrd   /boot/initrd-[TAB]
boot

```

after booting into your system, open a terminal, and run "sudo update-grub" and it's done.

---

