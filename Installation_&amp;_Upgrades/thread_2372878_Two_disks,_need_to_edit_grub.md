---
title: "Two disks, need to edit grub"
date: 2017-09-29
forum: Installation &amp; Upgrades
---

### Post by James Wilde on 2017-09-29
This is my setup.  I am running Ubuntu Mate from a 160 GB internal disk formatted with three partitions, root (/dev/sda1), swap and home.  Swap and home are in an extended partition.  On a 500 GB usb drive formatted similarly, except that swap and home are not in an extended partition, I have copied the root partition on /dev/sda1 to the root partition on /dev/sdb1.  I followed the instructions in a post entitled MovingLinuxPartition (with no space between the words).

I used gparted run from a start-up disk to copy and paste, and have changed the UUID of the target partition (/dev/sdb1).  Now I've got to the paragraphs about Update grub and fstab, and Update MBR to point to the new grub.  It's here I am stuck, since this article was written for Ubuntu 9.10 and later, which means it was probably written before grub2.

What I would appreciate is if someone could point me to an article which will help me finish what I have started.  I want to be able to a) test the 500 GB disk by starting from it after selecting it via the bios and then b) taking out the internal 160GB disk and inserting the 500 GB disk as my new internal disk.  I presumably need to edit grub and possibly fstab, using the UUID of my new /dev/sdb1 partition.

Much appreciated as I can't even imagine how I would word a search to look for this kind of solution.

---

### Post by TheFu on 2017-09-29
$ sudo update-grub

This won't fix any fstab errors, however. It will just have grub search for all OS partitions and add them to the grub menu for you.  There is a how-to for editing fstab on help.ubuntu.com. Google finds it easily.  Make certain you have all the fields and that no duplicate UUIDs exist.

---

### Post by oldfred on 2017-09-29
I think it was 9.10 where they changed to grub2 as standard over grub, now grub legacy.

If you have not installed grub to MBR of sdb using install in sdb, you need to do that.
How did you copy from sda to sdb. Any image copy will leave you with duplicate UUIDs.  

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by James Wilde on 2017-09-30
Thanks for your reply, The Fu.  I suppose if I test the new disk whilst it is still a usb and thus /dev/sdb I must run sudo update-grub again when I move it to become the internal disk, /dev/sda, so that the new position is noted in the grub menu?

---

### Post by James Wilde on 2017-09-30
Thanks, Old Fred.  I copied the partition from /dev/sda1 to /dev/sdb1 using gparted.  That did leave me with duplicate UUIDs so I used gparted to create a new UUID on /dev/sdb1.  Unfortunately I didn't note the UUID of /dev/sdb1 beforehand, but I can find the UUIDs of all my disks now, and will see any 'false' UUIDs in fstab.  Then I need to know the boot order in grub so I can choose the right version to set as default.

---

### Post by TheFu on 2017-09-30
blkid will show the UUID-to-device mapping.
There are other ways too - those are really just symbolic links under /dev/ somewhere. I always look them up that way - old school methods sometimes are the best methods.  

For example:
```
$ cd /dev/disk/by-{tab}{tab}
by-id/        by-partlabel/ by-path/      
by-label/     by-partuuid/  by-uuid/
``` shows that you can see them by label, by path, by uuid, and by a few others.  Each has a use in different environments.  I use by-label for all my portable devices that I want to control where they are mounted.  If I had 20 disks attached, I'd use by-path since the controller used would matter. You get the idea.

---

### Post by James Wilde on 2017-10-02
Thanks, All.  Fixed this with careful use of boot-repair.  Now I'm back to my 500 GB disk and the 160 Gb disk can be my system backup.

---

