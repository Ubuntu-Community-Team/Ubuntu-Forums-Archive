---
title: "very upset, please help. (mount: must be superuser to use mount)"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by samssf on 2006-09-20
Ok, after having huge problems with 64bit ubuntu on AMD64, I decided to wipe and start over using 32bit ubuntu.

When I was running 64bit, I had the pmount problem upon install but was quickly resolved...

This time forever, I have a new problem, and I am exteremly frustrated. I need to get my system up and running, but my wireless card wont work, I cant read from my partitions, etc... I have read every howto and done everything I can possibly think of, and yet no one out there has any decent answer for any of my problems.

My first major thing with this new install, is that when I would try to access "53 Gig volume" in "Computer", I would recieve the error "Mount: root cannot mount /dev/sdc1 on /media/sdc1" or something like that.

The suggestion was given to chmod 777 /mount/bin so I did. Makes no sense why I would have to do that, but ok.

Now when I try to access the partition from Computer, I receive this error:
"mount: must be superuser to use mount"

Really, this is a bunch of bs. There should be some info somewhere online on how to fix this. Surely, if I just finished my install, then other people would have the same problem upon install.

I have tried tweaking my fstab. Everone tells how to modify the CDROM entry. I need to know how to edit an entry for an ntfs partion.
Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdc1       /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdc5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Someone PLEASE help me or direct me to where I can find my solution.

---

### Post by samssf on 2006-09-20
and yes I've tried setting umask to 000. and to 0444. I've tried putting the word "user" and "users" in the sdc1 entry line, but I dont know exactly where to put it.

*Update* logged into gnome as root and tried to access the drive in Computer. Now I get this error:

"mount: wrong fs type, bad option, bad superblock on /dev/sdc1,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so"

Can someone tell me what this means?

---

### Post by kerry_s on 2006-09-20
I added "user" so i don't have to be root to mount.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               jfs     defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,user,noauto,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     vfat    defaults,user,noauto,utf8,umask=007,gid=46 0       1
/dev/hda3       /media/hda3     reiserfs defaults,user,noauto        0       2
/dev/hdd2       /media/hdd2     reiserfs defaults,user,noauto        0       2
/dev/hdd3       /media/hdd3     xfs     defaults,user,noauto        0       2
/dev/hdd1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Edit: nevermine i see you already tried the user thing. What filesystem is it suppose to be? in your fstab it says it's a ntfs(windows xp type). I hope you didn't try to write to a ntfs partion, if you did it's more than likely corrupt. Linux is not really there yet when it comes to ntfs.

---

### Post by samssf on 2006-09-20
Well, I have an update... although I'm not real sure what's going on.. I will tell what I Know.

Mounting was giving me lots of errors on my sdc1 partition (windows xp ntfs). I tried lots of things (which never worked for anyone on any other forums), and likewise came up with nothing. Then I found a automatic mount script when helped me by giving me an error about block size and unknown filesystem type or some crap like that.

So I decided to try to boot to windows, and grub gives me an error that says "Filesystem type unknown. partition type 0x7"

Turns out a lot of people online got this error, and a lot of them when they dual boot. Unfortunately, I read for hours and never found a post where someone actually had their problem solved. Everything just asks whether or not the grub config is set up right.

Well, my grub config is correct. I know how to use the command line to try to boot to a partition. And I've tried setting my HDD to LBA. None of this helped.

I am not to knowledgable when it comes to partitions and MBR.... but I think ubuntu (for some reason only with my latest install).. Installed grub onto my windows partition. Is that possible? Rather than installing it into the MBR. If I overwrite my MBR with a different tool... and tell it to boot to windows... then alas GRUB comes up. 

Maybe the reason linux cannot recognize my windows partition filesystem is because if f'ed it up with grub?? I'm not sure...

I need to know what tools, if any, will allow me to 

1. fix my mbr
2. get rid of grub from my windows partition
3. fix my windows partition.

I am sure something is f'ed up thats why I cant mount that partition from within ubuntu. OH and if I load gparted... it has an exclamation mark by my windows NTFS partition.

been nothing but hell since i installed ubunutu.... lost like 50 hours of time, and it's crazy because no one has any information about any of my problems. and yet, I've followed all instructions exactly.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7014    56339923+   7  HPFS/NTFS
/dev/sdc2            7015        8959    15623212+  83  Linux
/dev/sdc3            8960        9039      642600    5  Extended
/dev/sdc5            8960        9039      642568+  82  Linux swap / Solaris

---

### Post by samssf on 2006-09-20
**Update**

I have now figured out that grub is installed into the boot sector of my first primary partition. As a result, Booting to that partition just reloads grub. Other ways of trying to boot give errors.

ALSO, grub does not recognize the filesystem properly of my primary NTFS partition, and so it won't mount it once I boot to Ubuntu.

How can I fix this so that I can boot to windows as well as mount that NTFS partition in Ubuntu?

---

### Post by samssf on 2006-09-21
Ok, so I decided to try what was suggested to me and try NTFSTools to see if I could figure anything out. To my dismay, NTFSTools told me that my NTFS partition is unreadable and I should use chkdsk. Damn.

So I boot using the windows xp cd, and ran chkdsk. Chkdsk told me:

"Disk appears to have unrecoverable problems" or something like that.

so I decided to run the Fixboot command. When I did, it said
"Cannot read filesystem on C:".... do you wish to try to fix the boot record? I said yes. Then it says

"Attempting to detect filesystem...filesystem detected as NTFS"
"Attempting to rewrite boot sector to C:.... success"..

So then I run chkdsk again, and it says everything is fine!
I boot to linux, and behold, my NTFS partition mounts immediately. All I had to do was go to "Computer" and double click on the drive.

Thanks for everyone who helped think about a solution.

Lesson: ---> If you accidentally f' up a NTFS partition with grub, or if your NTFS partition wont load, try using Fixboot in the windows xp recovery console (xp cd)

---

