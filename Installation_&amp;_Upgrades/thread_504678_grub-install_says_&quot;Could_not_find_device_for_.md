---
title: "grub-install says &quot;Could not find device for /boot: Not found or not a block device.&quot;"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by svensandberg on 2007-07-19
I am installing ubuntu-7.04-desktop-i386 and have trouble with grub-install.

The background is as follows. My cd reader is broken and I have used the instructions on [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) to install from a disk partition. After rebooting, I've re-partitioned the disk, so I am currently running a system with two empty partitions (to become / and /home), and one partition containing the contents of the live cd. When I re-partitioned the disk, I removed the root partition of my previous Linux installation. Hence, there is currently no way to boot my system. This is obviously very risky - e.g., if I start an installation and it fails for whatever reason, my system will be unbootable forever.

Therefore, I now ran grub-install, in order to get a bootable system before I start installation. However, I get the following error:

$ grub-install /dev/sda1
Could not find device for /boot: Not found or not a block device.

I've googled for this error message, but could not find any useful help (one advice was to run `grub-install --recheck /dev/sda1'. However, this gives the same error message.)

Any help would be very appreciated!
Sven Sandberg

---

### Post by rbmorse on 2007-07-19
THis is the short version, but may do what you want.

Boot from the liveCD and open a terminal window. Do:
```
sudo grub
```

That should change the prompt to "grub". Then the following:

```
 find /boot/grub/stage1                     <  the "1" is the number one
```

That will return a value that looks like

(hdX,Y)

where X and Y are numbers. Remember the values. Then:

```
root (hdX,Y)
```

where X and Y are the values returned by the find command. This tells GRUB where the boot partition of your linux installation is now located. Then:
```
setup (hd0)                 < the "0" is the number zero.
```

This writes the updated GRUB stub loader (now with the correct boot partition location) to the MBR (first 512 bytes) of the current boot drive.

```
quit
```
to exit the grub terminal,
```
exit
```

to close the terminal window, and reboot.

---

### Post by svensandberg on 2007-07-20
Thanks. My problem seems to be that I don't have a /boot/grub directory. The /boot/grub directory was removed when I re-partitioned the disk. Hence, the `find' command in the grub shell gives the error `file not found'. I have now read the grub documentation, which hints that I should copy image files to the partition I want to boot from, before running grub. Hence, I did this and then I did as you suggested:

```
mount /dev/sda1 /media/disk-1
mkdir /media/disk-1/boot
mkdir /media/disk-1/boot/grub
cp /usr/lib/grub/i386-pc/* /media/disk-1/boot/grub
grub
grub> root (hd0,0)
grub> setup (hd0)
```

This gave no error messages.

Now, my concern is whether everything is done and whether I can be sure that my system is bootable again. (I do not want to take any risks, since my computer has no removable media. In other words, if there is any problem booting, I have to buy new hardware.)

Please, can someone confirm that the commands above, at least in theory, should be enough to install grub from scratch on an empty partition?

Many thanks
Sven Sandberg

---

### Post by Herman on 2007-07-20
That looks like it should have been okay. 

Here's what I would have used,
```
mount /dev/sda1 /media/disk-1
mkdir /media/disk-1/boot
cp -r /boot/grub /media/disk-1/boot
grub
grub> root (hd0,0)
grub> setup (hd0)
```I see there's a difference, I think /boot/grub contains a few more files, will you need any of those? 
```
herman@badboy:~$ ls /usr/lib/grub/i386-pc/
e2fs_stage1_5  fat_stage1_5  jfs_stage1_5  minix_stage1_5  reiserfs_stage1_5  stage1  stage2  stage2_eltorito  xfs_stage1_5

herman@badboy:~$ ls /boot/grub
device.map     fat_stage1_5       jfs_stage1_5  menu.lst~       reiserfs_stage1_5  stage2               xfs_stage1_5
default                e2fs_stage1_5  installed-version  menu.lst      minix_stage1_5  stage1             Ubuntusplash.xpm.gz
```> Now, my concern is whether everything is done and whether I can be sure that my system is bootable again. (I do not want to take any risks, since my computer has no removable media. In other words, if there is any problem booting, I have to buy new hardware.)[Super Grub Disk]("http://geocities.com/supergrubdisk/") is available for floppy disk and USB, as well as CD-ROM, I know you can't use CD-ROM, but would one of the others help you in an emergency?

---

### Post by svensandberg on 2007-07-20
Thanks a lot.

> I see there's a difference, I think /boot/grub contains a few more files, will you need any of those? 

My /boot/grub (provided by the ubuntu installation disk) only contains the files `default' and `device.map', and no disk images. Should I copy default and device.map to /media/disk-1/boot/grub ?

Also, I have no menu.lst (neither in /boot/grub nor in /usr/lib/grub/i386-pc): should I create one manually?

> Super Grub Disk is available for floppy disk and USB, as well as CD-ROM, I know you can't use CD-ROM, but would one of the others help you in an emergency?

It's a laptop without floppy, but it does have a USB port and I have a USB disk. How big is the chance that my BIOS (from early 2004) knows how to boot from a USB disk?

---

### Post by Herman on 2007-07-20
Thanks for your patience, sorry for keeping you waiting.

You don't *need* a menu.lst file if you know how to boot from  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), but It could be easier if you do make a menu.lst file, the links's instructions do say how to edit the menu.lst file to boot the .iso partition,> Step 3. Edit your grub configuration file (typically /etc/grub.conf or /boot/grub/menu.lst) 
to boot from the new partition by adding the lines,  
```
  title installer
        root (hd0,0)
        kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
        initrd /casper/initrd.gz
```
The first line after the title tells grub which partition contains the installer. hd0 stands 
for "first hard disk," and the 0 following it standards for first partition. You will need to 
change this if your installer partition is different from /dev/sda1. sdaN becomes 
(hd0, N-1), sdbN becomes (hd1,N-1) and so on. 
As you can see, grub starts counting from 0, which can be confusing.
 
 Step 4. Reboot, and choose "installer" from the grub boot menu, and continue as if you were installing from CD. All you would probably need would be a plain text file with that on it, named menu.lst. However, I would like to try that out myself first for you to make sure I'm right about that.
 I don't think you will need the other two files actually, just the menu.lst would be enough.

If you give me some more time I'll test that for you in one of my computers and check if that works okay for me and let you know how I get along. :)

Regards, Herman :)

---

### Post by Herman on 2007-07-20
Well, I have done everything up to installing GRUB to MBR from the installer partition.

I have tried my own way first, I made a directory named grub in the /boot directory and tried grub-install /dev/hda, I got  the same error message as you did in your first post.

Then I tried what you did in the third post in this thread, but that didn't work in my laptop, it says: Error 15: File not found, referring to /boot/grub/stage1. I do have a /boot/grub/stage1 and also a /media/disk-1/boot/grub/stage1 file as well now.
Have I missed something here?

Anyway, now I'm now working at making a dedicated GRUB partition, I think that will work and I think that will be the recommended safety measure for you.
The problem for me is I'm running these experiments in a laptop that already has some other partitons in it, so I have my installer in /dev/hda6, which is in an extended partition. I already have all the primary partitions I'm allowed and I can't unmount the extended partition to resize it to make room for the new dedicated GRUB partition with Gnome Partition Editor. If you can do so I think you should. Then copy the /boot/grub files to that and install GRUB to MBR from there.
I'll have to cheat by rebooting and using GParted Live CD to make my new partition.
Then I'll reboot into the installer partition and try installing GRUB to MBR from the new dedicated GRUB partition and check that our abbreviated menu.lst will work okay.

I'll be back again shortly....

---

### Post by Herman on 2007-07-20
Okay, I created a dedicated GRUB partition and have installed GRUB to MBR form it and added our abbreviated menu.lst file.
I have rebooted with it to test it and it works fine.

I recommend you should definitely make a dedicated GRUB partition, about 100 mb of hard disk space would be more than enough. 
Mount it. Make a /boot directory in it and then make a /grub directory inside that. 
Then copy your GRUB files from /usr/lib/grub/i386 and then install GRUB to MBR from there.

This will be important for you. While I was doing this testing I found that the installer, when rebooted, lost all it's files that I made in it before, as a Live CD would be expected to do.
That means even if you were successful in copying the GRUB files within the installer partition and installing GRUB to MBR, when you reboot you will lose all your changes.
You really need a dedicated GRUB partition if you want to be safe.

I'll be back in a while in case you need more details. Just ask if you want extra help.
I have updated my GRUB Page with improvements to this topic, [         How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") in case that's any help.

Regards, Herman :)

---

### Post by svensandberg on 2007-07-21
Thanks a lot for your efforts! It makes me happy to see there are people like you out there to give a helping hand. I have now managed to reboot and install Ubuntu and everything works. What I finally did was to copy both /usr/lib/grub/i386-pc/* and /boot/grub/{default,device.map} to /media/disk-1/boot/grub, and then I ran grub as explained earlier in the thread. I created my own menu.lst using the grub documentation and [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) . Upon rebooting, everything worked as expected.

---

### Post by Herman on 2007-07-21
Hey! Congratulations and welcome, svensandberg!  :guitar:

I'm happy you got Ubuntu installed alright! :)

Thank you as well for your part in this thread, I actually learned quite a few tricks from you that I wouldn't have learned otherwise, so it was worth it, and I enjoyed it. :)

Regards, Herman :)

---

### Post by chylld on 2007-12-18
> **rbmorse said:**
> THis is the short version, but may do what you want.

Boot from the liveCD and open a terminal window. Do:
```
sudo grub
```

That should change the prompt to "grub". Then the following:

```
 find /boot/grub/stage1                     <  the "1" is the number one
```

That will return a value that looks like

(hdX,Y)

where X and Y are numbers. Remember the values. Then:

```
root (hdX,Y)
```

where X and Y are the values returned by the find command. This tells GRUB where the boot partition of your linux installation is now located. Then:
```
setup (hd0)                 < the "0" is the number zero.
```

This writes the updated GRUB stub loader (now with the correct boot partition location) to the MBR (first 512 bytes) of the current boot drive.

```
quit
```
to exit the grub terminal,
```
exit
```

to close the terminal window, and reboot.

just had to register to say a big THANK YOU for the above post!

i recently had a similar problem resulting from trying to repartition my hard disk (2 partitions ntfs vista, 2 partitions ubuntu) and was almost at the point of launching the vista recovery wizard. thankfully the above instructions were enough.

thanks again!

---

