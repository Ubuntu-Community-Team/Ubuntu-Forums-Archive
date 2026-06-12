---
title: "Problem with dual boot"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by Dave Burbank on 2006-07-26
After installing Ubuntu I can no longer boot into Windows XP.
On a new hard drive I did a clean install of XP and set up a / and swap partition for Ubuntu using Partition Magic.  I then installed Ubuntu using a live CD, and the instalation went without issue.  Uppon reboot GRUB loaded and it listed both Ubuntu and XP, once Ubuntu was loaded the Windows patitions appeared on the desktop and I was able to read from them (so I know they're still there).
If I try to load XP through GRUB the black WindowsXP splash screen with the progress bar loads, but after that I get a baby blue screen with the error 'autocheck not found, skipping autocheck' and then a BSOD.  What gives?  Is Windows now looking for files in the wrong place?  Is the MBR messed up?  Any help would be great, thanks.

---

### Post by OpsVentus on 2006-07-26
Have you checked to Windows partition for errors? It looks like the windows install is corrupted somehow.

The MBR should not be causing this, that's just to tell the computer what to start, not how.

Cheers,
Bart.

---

### Post by Dave Burbank on 2006-07-26
I don't think there is a problem with the windows partition as I am able to browse it in Ubuntu, and it loaded fine before Ubuntu was installed.  I will gladly check the partition for errors, but being a n00b with Linux I am unsure how, some advice would greatly be appreciated.

---

### Post by OpsVentus on 2006-07-26
That depends if your Windows partition is NTFS or FAT32.

And how did you setup the other partitions? after installing Windows? Did you have to shrink the windows partition?

Cheers,
Bart.

---

### Post by Dave Burbank on 2006-07-26
The windows partition is NTFS, I also created Data, Media, and Backup partitions all of NTFS.  None of the partitions were resized as I made a seperate / and swap partitions before I installed Ubuntu.  I don't see how the Windows partitin could have been affected as the Ubuntu installation should not have touched it.

---

### Post by OpsVentus on 2006-07-26
No it shouldn't have touched it. But you are moving stuff around on the disk, after installing Windows. This is something it doesn't like.

Cheers,
Bart.

---

### Post by Dave Burbank on 2006-07-26
OK, so if I reinstall windows will I be able to boot Ubuntu, as GRUB might get moved around and the MBR will be re-written?

---

### Post by OpsVentus on 2006-07-26
The MBR will be overwritten, but you can reconfigure GRUB.
To do this you will have to boot from a live cd.

The exact procedure I'm not shure about but it will be something like (after reinstall windows):
Boot from live cd
#chroot *your filesystem*
#grub-configure

Cheers,
Bart.

---

### Post by OpsVentus on 2006-07-26
From the GRUB site:
"The following example assumes you have your root partition on /dev/hda1, and /boot on /dev/hda2. And grub will be installed on the MBR of /dev/hda. 

mount /dev/hda1 /mnt/sysimage
mount /dev/hda2 /mnt/sysimage/boot
chroot /mnt/sysimage
mv /boot/grub /boot/grub.old
mkdir /boot/grub
cp /boot/grub/menu.lst /boot/grub
cp /boot/grub/grub.conf /boot/grub
grub-install /dev/hda"

Should work, maybe you have to add the Windows boot by hand.

If you do not understand these command's tell me how your disk(s) look like, and where's what. Then I can adjust the command's for you.

Cheers,
Bart.

---

### Post by Dave Burbank on 2006-07-26
Thanks for all of you help Bart, I am going to reinstall XP on it old partition and see if I can get a windows boot manager to recognize Linux:rolleyes: 

I'll start a new thread about configuring GRUB, once again thanks for the help

EDIT : oopps I missed your last post, give me a minute and I'll have a list of my partitions and filesystem

---

### Post by Dave Burbank on 2006-07-26
My hard disk looks like this under Gparted:

/dev/sda1   :  Windows install NTFS Primary
/dev/sda2   :  *Extended Primary
/dev/sda5   :  Data NTFS Logical
/dev/sda6   :  Media NTFS Logical
/dev/sda7   :  Backup NTFS Logical
/dev/sda3   :  Ubuntu ext3 Primary
/dev/sda4   :  Linux-swap

---

### Post by OpsVentus on 2006-07-26
After installing Windows try this:
Boot from live cd, no need for gnome, where going into the terminal anyway.

mount /dev/sda3 /mnt/sysimage
chroot /mnt/sysimage
grub-install /dev/sda

Good luck and come back if you fit a problem,
Bart.

---

### Post by Dave Burbank on 2006-07-26
Alright I'm going to install Windows again and then try what you suggested.
Not being too familiar with Linux, does what this do is mount the linux partition and then install grub on the windows boot sector?

---

### Post by OpsVentus on 2006-07-26
**mount /dev/sda3 /mnt/sysimage**
Mounts your filesystem to /mnt/sysimage

**chroot /mnt/sysimage**
Will make / change into /mnt/sysimage.
Bit hard to understand maybe, doesn't matter.

**grub-install /dev/sda**
Will install Grub on /sda3 and tells the computer to start grub when it boots from this disk.

Windows will have it's own boot stuff, grub knows how to handle this. Windows will never know there's another OS on your computer.

Cheers,
Bart.

---

### Post by Dave Burbank on 2006-07-26
So I've installed windows again and have it working.
I booted from the live CD (what I'm using now) and tried what you suggested, here is what happened:

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/sysimage
mount: mount point /mnt/sysimage does not exist

If I try it without the space after sda3:

ubuntu@ubuntu:~$ sudo mount /dev/sda3/mnt/sysimage
mount: can't find /dev/sda3/mnt/sysimage in /etc/fstab or /etc/mtab

Do I need to create a mount point?

---

### Post by OpsVentus on 2006-07-26
Yes sorry, forgot.
go first:
mkdir /mnt/sysimage

If it says your not allow'd go:
sudo mkdir /mnt/sysimage

Then the other commands.

---

### Post by Dave Burbank on 2006-07-26
OK I have gotten the filesystem mounted, I swithched to the root directory, when I type grub-install /dev/sda I get: /dev/sda: Not found or not a block device.

What do you think?

---

### Post by OpsVentus on 2006-07-26
And what about:
grub-install hd0

---

### Post by Dave Burbank on 2006-07-26
root@ubuntu:/# grub-install hd0
/dev/sda3: Not found or not a block device.

---

### Post by OpsVentus on 2006-07-26
I'm sorry that should have work'd.
Do you have an floppy around?
You can try to reboot the live cd, put a floppy in, in the terminal go:
#grub-install '(fd0)'
Then boot from the floppy.
There should a grub on the disk.

When you get to grub go:
grub> root (hd0,0)
grub> setup (hd0)

---

### Post by Dave Burbank on 2006-07-26
Will try... I've just got to install a floppy drive

---

### Post by Dave Burbank on 2006-07-26
When I type **#grub-instal '(fd0)'** ubuntu accepts the command and goes to the next line, but grub is not installed.  The floppy drive LED does not come on and there are no disk noises. I can copy other files to floppy drive, so I am able to use it, but grub does not get installed on the disk.

EDIT : If I try **sudo grub-instal '(fd0)'** I get :
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

---

### Post by OpsVentus on 2006-07-26
# mke2fs /dev/fd0
# mount -t ext2 /dev/fd0 /mnt
# grub-install --root-directory=/mnt fd0
# umount /mnt

And how about this.

ps.
Sorry I can't give you the correct answer right away, I'm getting into stuff here I haven't had to deal with yet.
Maybe a google to the subject could deliver a better answer?

---

### Post by Dave Burbank on 2006-07-26
Ok, it looks like grub was installed to the floppy but there were some write errors, but I'll try to boot anyways. This is what I saw:

ubuntu@ubuntu:~$ mke2fs /dev/fd0
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
184 inodes, 1440 blocks
72 blocks (5.00%) reserved for the super user
First data block=1
1 block group
8192 blocks per group, 8192 fragments per group
184 inodes per group

Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
ubuntu@ubuntu:~$ mount -t ext2 /dev/fd0 /mnt
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/fd0 /mnt
ubuntu@ubuntu:~$ grub-install --root-directory=/mnt fd0
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Unknown partition table signature


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (fd0)
 Filesystem type is ext2fs, using whole disk
grub> setup  --stage2=/mnt/boot/grub/stage2 --prefix=/boot/grub (fd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (fd0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (fd0)"... failed (this is not fatal)
 Running "install --stage2=/mnt/boot/grub/stage2 /boot/grub/stage1 (fd0) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 29: Disk write error
grub> quit
ubuntu@ubuntu:~$ umount /mnt
umount: /mnt is not in the fstab (and you are not root)
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$

EDIT : from the GRUB web page : 29 : Disk write error
    This error is returned if there is a disk write error when trying to           write to a particular disk. This would generally only occur during an install of set active partition command.

---

### Post by confused57 on 2006-07-26
May be something in this thread that could help:

[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)
or
[http://www.ubuntuforums.org/showthread.php?t=219344](http://www.ubuntuforums.org/showthread.php?t=219344)

---

### Post by OpsVentus on 2006-07-27
Found this howto:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
This seems to be the best option.

Cheers,
Bart.

---

### Post by Dave Burbank on 2006-07-27
Success!!!
Thank you very much OpsVentus for your guidance, and for the links confused57.

@OpsVentus, I tried to boot from the floppy, but to no surprise there was an I/O error.  I installed grub onto 5 floppies but got a write error every time, either I've got some horrible floppies or I was doing something wrong.
If I ran grub from the terminal and typed : **root ([tab]** nothing would appear, grub would just go to the next line, it wouldn't tell me wich is the root partition (even though I know it's sda3).
By the time I noteced your last post I was reinstalling both XP and Ubuntu.  It seems the only way I could set up grub without XP messing with it was to, install XP on the first partition of a clean disk.  Then using Partition Magic I made partitions for windows, and then '/' /home and swap partitons for ubuntu.  I then installed Boot Magic and set up a entry for a yet uninstalled ubuntu.  Once all that was taken care of I installed ubuntu, and at the partition window I manually mounted / /home and swap to the partitions I created earlier.  Near the and of installation, grub installed itself as the main boot loader and I can now boot both XP and Ubuntu!
Even though Boot Magic is not used, I had to install it before setting up Ubuntu, otherwise after ubuntu was installed and I booted XP, Windows would  somehow mess up grub, and on the next boot I could boot neither (my original question posted).
Although I could not restore grub with your help, I did learn a lot about Ubuntu and Linux, and that is far more valuble, thank you very much,  Hopefully given some more time and learnig I can ween myself off of Windows and fully experience Ubuntu.
Dave

---

### Post by OpsVentus on 2006-07-28
Glad to help.

Have fun with Ubuntu!

Bart.

---

