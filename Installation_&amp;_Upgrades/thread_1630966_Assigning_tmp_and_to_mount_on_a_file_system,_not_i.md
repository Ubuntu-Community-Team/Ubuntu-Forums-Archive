---
title: "Assigning /tmp and to mount on a file system, not in root"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-11-26
Greetings again.

I am pondering a reinstall of a freshly installed Ubuntu; I may or may not take that drastic step.  However, I have partitioned my drive to include a 16-GB partition labelled "Ubuntu-tmp", in my case /dev/sda7, with the intent of mounting that file system as /tmp.  Depending on how I decide to go about the reinstall I need an answer to these questions:
[LIST]
[*]If I reinstall: Is it possible to designate /dev/sda7 to mount as /tmp during the installation process?
[*]If I cannot designate the mounts at install time, or if I opt not to reinstall: I can't really empty the /tmp directory in the root in order to properly use it as a mount point for [the file system on] /dev/sda7; many files in there are still in use by running processes.  So how can I clear the /-mounted /tmp directory and assign it to /dev/sda7?
[/LIST]

I have attached a screen shot of gparted to illustrate my layout scheme.  The gparted manual suggests I select the partition, click [Partition]->[Mount].  Of course, my gparted drops a menu with [Mount] is absent and an [Unmount] option is greyed out.  :(  This raises a question of how I am going to mount /users and /var in their intended file systems (/dev/sda8 and /dev/sda9, respectively), because the [partition] menu looks the same for these partitions as well.

Thanks mucho for advice here.

---

### Post by jocko on 2010-11-26
During an install it is possible to assign mount points to any partition. Just pick the advanced option during the install program's partition setup.

But you don't need to reinstall just to move /tmp (or any other directory) to a separate partition, just boot a live cd, mount your installed system's root partition (/) and edit /etc/fstab. Then delete any files in the old /tmp directory and reboot.

I have never seen much usage of /tmp (usually a few hundred kb up to a few Mb), so I think it's a waste of space to make a 16 Gb /tmp. I keep my /tmp in ram...

For the other partitions, once you edited fstab, just copy all the data to the root of the new partitions, make sure you didn't change the permissions on the files, delete the files from the old directories and reboot.

Your root (/) is incredibly small with only 4 Gb. Why not increase the size of the extended partition to fill up the unallocated space at the end of the disk, move the other partitions to make some free space between sda5 and sda6, and then increase the size of the root partition? This will take quite some tiime if you have data on the sda7, 8 and 9 partitions, and you don't want to turn the computer off or loose power during the process, but if the partitions are new and don't have any data you can simply delete them, increase the size of the root partition and then create the partitions again.

Or, when you say you want to move the "/users" directory you really mean you want to move the /usr directory? In that case, I guess the size of the rest of the / file system will probably be sufficient when you also move /var...

But let me suggest one more thing to move to it's own partition: /home. That way if you ever need to reinstall you can keep the data in /home and keep all of your user defined settings for different applications.

---

### Post by rpaskudniak on 2010-11-30
Greetings, Jocko.

I bring you greetings from Rufo and Oscar. :D  (I am, of course, making literary assumptions about your moniker.)

I have taken your advice and changed some sizes; see the attached screen shot. I'll worry about /home later.

I just need a bit of guidance about the format of the fstab entry, seeing how useless the existing entries are as role models.
```
UUID=831b4fa3-b7eb-4daf-83f4-5edcb625795c / ext3 defaults 0 1
UUID=b131bed3-9334-4baa-9573-bf15c9465e83 swap swap sw 0 0
UUID=9AF08259F0823B8F /media/OS ntfs-3g defaults 0 0
```Duh?  Where would I find this UUID value to plug into the fstab line?

For the more delicate-natured sysadmin, like me (yeah, right :rolleyes: ), the man page on fstab seems to suggest the following line for what I have in mind:```
/dev/sda7 /tmp ext2 defaults 0 0
``` That is:
[LIST]
[*][Sub-]Partition /dev/sda7 mounts on directory /tmp.
[*]It is of type ext2 (See the screenshot)
[*]It is subject to default mount options, which are good enough for the root.
[*]0 in position 5 says "Don't dump me"
[*]2 in position 6 says "fsck should check me second".  According to the man entry, if I were to mount that sw partition, it would also have a 2 in this column.
[/LIST]
Pending the nod of correctness from a guru, that's what I will stick into the fstab next time I boot from the live CD.

But I'd still like to know where that UUID value came from.  (Yes, I could also use the disk labels but that tends to change at this early stage.)  xfs_admin and e2label, suggested my the fstab man page, don't yield these numbers. :-(

But mainly, I just want my hand help a moment while I cross this street into directly editing fstab. (BTW, I have already done a bit of this after using NTFS-Manager to mount my Windows partition and got an extra mount I didn't want.)

Thanks for your critique.

---

### Post by jocko on 2010-11-30
> **rpaskudniak said:**
> For the more delicate-natured sysadmin, like me (yeah, right :rolleyes: ), the man page on fstab seems to suggest the following line for what I have in mind:```
/dev/sda7 /tmp ext2 defaults 0 0
```
That would probably work fine, but if you have more than one hard drive or sometimes boot with a non-bootable usb disk the /dev/sdX designation may change randomly between boots, so it's always better to use uuids instead...
> **rpaskudniak said:**
> But I'd still like to know where that UUID value came from.
You'll get it from either of these commands:
```
sudo blkid
ls -l /dev/disk/by-uuid/
```

---

### Post by rpaskudniak on 2010-12-31
Jocko and family,

I had other issues for a while but I'm back in the swing now.  To pick up where we left off: Jocko suggested these two options for getting the UUID of each device file: ```
sudo blkid
ls -l /dev/disk/by-uuid/
```The blkid command works as advertised.  Thank you much.  On the other hand, the ls option quoted above looks like it must be a typo; the ls command interprets the last path component, [FONT="Courier New"][COLOR="Navy"]_/by-uuid_[/COLOR][/FONT], as a file or directory under /dev/disk (in my case, /dev/sda7) and (reasonably enough) complains "no such file or directory".

Now once I have learned the blkid command, I don't really need another method to obtain this UUID.  But in the the spirit of the Perl programmer, I'd very much enjoy knowing another way to do this, if it really exists.    Jocko, would you please demonstrate a screen shot of the ls command you have used to obtain the UUID?

Thanks much.

Oh, there is one little snag in my scheme.  You see, it's not just /tmp I want to turn into a mounted file system.  I wish to do the same with /var and /usr - Use the Ubuntu Live CD to move the contents of the directories into these locations and then overwrite the /etc/fstab with another that I have prepared.  (Don't worry, I have already created a backup of fstab.)  I will post another thread about the mv command and when I have the answer to that, I will post my completed scheme back on this thread.

Thanks much for the answers so far.

---

### Post by jocko on 2010-12-31
by-uuid/ is a folder under /dev/disk/, so the command is correct.
```
jocko@jocko-desktop:~$ ls -l /dev/disk/by-uuid/
totalt 0
lrwxrwxrwx 1 root root 10 2010-12-30 04:15 0d76854e-ae85-42be-8840-07ee9fb1b56c -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-12-30 04:15 23b478fb-2569-4057-a4d8-b7dd2dead1bc -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-12-30 04:15 66427a5c-acf9-45a4-b431-8ca62c42de2a -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-12-30 04:15 714a23c1-0607-4579-9170-2e3b45c156a1 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2010-12-30 04:15 9073e907-befc-44eb-9129-2fd5331479dd -> ../../sdc1
jocko@jocko-desktop:~$ 

```

---

