---
title: "Can't boot after upgrade today, June1,2007"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by Kalimar on 2007-06-01
I started using Ubuntu a month ago and absolutely love it. Today I updated my system after clicking on suggested updates and now the system won't boot. I figured out through the forum how to boot in recovery mode. I get the following messages (there is where I think the problems start)

Failure:failed to assemble all arrays.
Done.
Done.
Begin: Waiting for theroot file system    (the computer then hangs for a couple of minutes)
Done.
               Check root= bootarg cat /proc/cmdline
               or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/294c82a0-3ef7-40c4-917b-6c213ed85916 does not exist. Dropping to a shell!



BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-inshell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)_

Thanks so much for any help on this issue

---

### Post by merlinus on 2007-06-01
Sounds like your UUIDs have changed.

sudo fdisk -l

will give a list of your partitions and their formats.

blkid

will give you the UUIDs.

Check these with entries in /etc/fstab

Boot from the live cd, and enter those commands in a terminal.

-merlin

---

### Post by Kalimar on 2007-06-01
Thanks for the super quick response. Can I boot from an older version, the only cd I have is from 5.10. I upgraded to feisty via on-line upgrades. What are UUIDs? How do I check entries in recovery mode? Sorry, I'm a newbie to Linux too.  Thanks

---

### Post by merlinus on 2007-06-01
You can try booting from an older live cd, as long as you can get to a terminal when it is up-and-running to enter the commands I gave in my previous post.

UUIDs are designators for partitions.

To get to /etc/fstab, enter:

gksudo gedit /etc/fstab

Compare the UUIDs you get from blkid with the ones listed there.

Good luck!

-merlin

---

### Post by confused57 on 2007-06-01
> **Kalimar said:**
> Thanks for the super quick response. Can I boot from an older version, the only cd I have is from 5.10. I upgraded to feisty via on-line upgrades. What are UUIDs? How do I check entries in recovery mode? Sorry, I'm a newbie to Linux too.  Thanks
You'll probably have to mount your root partition, using the live cd, to see your /etc/fstab and /boot/grub/menu.lst...using the command merlinus suggested:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by figgles on 2007-06-01
> **confused57 said:**
> You'll probably have to mount your root partition, using the live cd, to see your /etc/fstab and /boot/grub/menu.lst...using the command merlinus suggested:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Darn it, this problem has hit me after an upgrade I wish I never agreed to. I love ubuntu but it is frustrating how fragile the OS is regards to its upgrade stability. This is certainly not the first time I've been through this. I tried the above and I get disk errors trying to mount the boot volume.

---

### Post by confused57 on 2007-06-01
> **figgles said:**
> Darn it, this problem has hit me after an upgrade I wish I never agreed to. I love ubuntu but it is frustrating how fragile the OS is regards to its upgrade stability. This is certainly not the first time I've been through this. I tried the above and I get disk errors trying to mount the boot volume.
You might want to open a terminal & post the output of:
```
sudo fdisk -lu
```

Are all your linux partitions ext3 & what commands were you using to mount your boot &/or root partition(s)?

---

### Post by figgles on 2007-06-02
Running from the Fiesty Fawn 7.04 Live CD:

[FONT="Courier New"]Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    56098979    28049458+  83  Linux
/dev/sda2        56098980    58605119     1253070    5  Extended
/dev/sda5        56099043    58605119     1253038+  82  Linux swap / Solaris
[/FONT]

and I used:

[FONT="Courier New"]ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/FONT]

dmesg tail says:

[  917.140000] JBD: no valid journal superblock found
[  917.140000] EXT3-fs: error loading journal.

blkid returns nothing

I ran spinrite (freeDOS CD utility) and the disk showed no physical errors

---

### Post by Kalimar on 2007-06-02
Thanks for the help so far. I was able to boot from a live cd. I used:
sudo blkid
to see the UUID.
I compared that to the fstab file. Should I add the information from the blkid to the fstab file. Would it help if you had the output from both of these? Let me know if it helps because I have to hand type all of the output.
To clarify, I don't have a windows partition. I'm running straight Ubuntu. 
Out of curiosity, what causes these problems? Is it the unverified installs? Should I only use the synaptic package manager exclusively for installs? 
THanks again for all your help. Ubuntu FOrums rock!

---

### Post by confused57 on 2007-06-02
> **Kalimar said:**
> Thanks for the help so far. I was able to boot from a live cd. I used:
sudo blkid
to see the UUID.
I compared that to the fstab file. Should I add the information from the blkid to the fstab file. Would it help if you had the output from both of these? Let me know if it helps because I have to hand type all of the output.
To clarify, I don't have a windows partition. I'm running straight Ubuntu. 
Out of curiosity, what causes these problems? Is it the unverified installs? Should I only use the synaptic package manager exclusively for installs? 
THanks again for all your help. Ubuntu FOrums rock!
You shouldn't have to post the output of the commands(you can't just copy & paste?)...boot up the live cd & run the command "blkid"...then mount your root partition, edit your /etc/fstab & /boot/grub/menu.lst by copy & pasting the "new" UUID from "blkid", if it's different from what you have in your fstab & menu.lst.

---

### Post by confused57 on 2007-06-02
> **figgles said:**
> Running from the Fiesty Fawn 7.04 Live CD:

[FONT="Courier New"]Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    56098979    28049458+  83  Linux
/dev/sda2        56098980    58605119     1253070    5  Extended
/dev/sda5        56099043    58605119     1253038+  82  Linux swap / Solaris
[/FONT]

and I used:

[FONT="Courier New"]ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/FONT]

dmesg tail says:

[  917.140000] JBD: no valid journal superblock found
[  917.140000] EXT3-fs: error loading journal.

blkid returns nothing

I ran spinrite (freeDOS CD utility) and the disk showed no physical errors

Is your root partition formatted reiserfs?  If it is just substitute reiserfs instead of ext3 in the mount command.

---

### Post by figgles on 2007-06-03
Re: Changing ext3 to reiserfs. Doing so gave the same error. Since blkid returns nothing, I checked with GParted -- and /dev/sda1 is an ext3 device.

Frustrating.

---

### Post by figgles on 2007-06-03
> **confused57 said:**
> Is your root partition formatted reiserfs?  If it is just substitute reiserfs instead of ext3 in the mount command.

And here I vigorously and confusedly scratch my head. Seeing ext3 in GParted, and getting an error, I reflexively run fsck on the drive and behold, more errors than I can count, including ext3 becoming an ext2 drive, unexpectedly. I am booted and back in. 

From what I saw, I should run fsck more often? Thank goodness, no reloading the OS!

Oh, yea; THANKS!

---

### Post by confused57 on 2007-06-03
> **figgles said:**
> And here I vigorously and confusedly scratch my head. Seeing ext3 in GParted, and getting an error, I reflexively run fsck on the drive and behold, more errors than I can count, including ext3 becoming an ext2 drive, unexpectedly. I am booted and back in. 

From what I saw, I should run fsck more often? Thank goodness, no reloading the OS!

Oh, yea; THANKS!
Glad you were able to get your OS booted...yes, I've seen other posters run fsck, which corrected the filesystem so that they were able to boot...good job.

---

### Post by Kalimar on 2007-06-04
I think I'm starting to understand the problem. Now, as rookies go, I actually copied the blkid output into my fstab file which has now become a problem because I think the output of the bklid shows the important information but it's not formatted for the fstab syntax. I've been trying to make heads or tails out of all the FSTAB tutorials out there but I still can't manage to set it up correctly based on the bklid data I have. Therefore I'm posting the output from blkid and would really appreciate some help formatting it to match the /etc/fstab file.  I think the grub file is ok because it allows me to look at the different kernels on my hard drive. I just can't boot from any of them, I think because of the goofed up FSTABfile.

Here's the content of /media/ubuntu/etc/fstab  (this is my temporary mount so I can access thekernel on my HD) Unfortunately it looks exactly like the output of my blkid :(
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       
/dev/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"
/dev/cloop0: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/mapper/casper-snapshot: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/evms/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"

Thanks again for all your help. By the time this is done maybe I'll even be able to help some folks

---

### Post by confused57 on 2007-06-04
> **Kalimar said:**
> I think I'm starting to understand the problem. Now, as rookies go, I actually copied the blkid output into my fstab file which has now become a problem because I think the output of the bklid shows the important information but it's not formatted for the fstab syntax. I've been trying to make heads or tails out of all the FSTAB tutorials out there but I still can't manage to set it up correctly based on the bklid data I have. Therefore I'm posting the output from blkid and would really appreciate some help formatting it to match the /etc/fstab file.  I think the grub file is ok because it allows me to look at the different kernels on my hard drive. I just can't boot from any of them, I think because of the goofed up FSTABfile.

Here's the content of /media/ubuntu/etc/fstab  (this is my temporary mount so I can access thekernel on my HD) Unfortunately it looks exactly like the output of my blkid :(
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       
/dev/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"
/dev/cloop0: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/mapper/casper-snapshot: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/evms/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"

Thanks again for all your help. By the time this is done maybe I'll even be able to help some folks

You definitely have a "messed up" fstab, here's an example of how your fstab should look:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

Here's basically how your / and swap should look, I'm not sure about your other entries:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 /  ext3  defaults,errors=remount-ro   0       1
# /dev/hda5
UUID=a2bfc36b-766a-46ce-9998-3bcb1400d748 none            swap    sw              0       0
#/dev/cloop0: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
#/dev/mapper/casper-snapshot: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
#/dev/evms/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" #TYPE="ext3"
#/dev/evms/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"
```

What you can do is make a backup of your current fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
```

then edit your fstab:
```
gksudo gedit /etc/fstab
```
just delete what you have, then copy & paste the above into your fstab, quit & save.  Then reboot your pc.
You can add any cd or floppy drives following the example in the link I gave you.  You'll be helping out in the forum before you know it.

You might also want to post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

Added:  Here's how you would mount your /etc/fstab with the live cd in order  to edit:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```
quit & save...

---

### Post by Kalimar on 2007-06-04
I think we're close. I've recreated the fstab file but we're still hanging during the quiet splash. The bar moves about 5% and then hangs. Here's the output of my fdisk -l command and the sudo blkid:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37559938+  83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ sudo blkid
/dev/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"
/dev/cloop0: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/mapper/casper-snapshot: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/evms/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"

Thanks

---

### Post by confused57 on 2007-06-04
You might want to post your /boot/grub/menu.lst, after mounting your root partition:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
maybe this will tell us something

I was hoping you might be able to boot your system without evms...I'm not familiar with the proper syntax for entering evms volumes in fstab.  If nothing works, you might want to start a new thread & include evms and possibly fstab entries in the thread title.

---

### Post by Kalimar on 2007-06-04
Thanks so much for your help. I'm going to start a new post discussing the evms, I think you're on the right track.
Keep your fingers crossed!

---

### Post by confused57 on 2007-06-04
> **Kalimar said:**
> Thanks so much for your help. I'm going to start a new post discussing the evms, I think you're on the right track.
Keep your fingers crossed!

You might want to try taking out the quiet & splash options in your kernel line to see where your boot is stalling...you can do this by highlighting your Ubuntu entry in your initial grub boot menu, press "e", arrow down to your kernel line, press "e" again, then take out the quiet & splash in your kernel line, then press "b" to boot...

It could be that startup scripts are trying to start evms & it's failing at that point...I'm sure there is someone else in the forum who's using evms that can share their fstab file.

Don't try this, but I read in another post you can remove evms from your startup script with this:
```
sudo update-rc.d -f evms remove
```

Hopefully, removing the quiet & splash will shed some light on what's failing...

---

### Post by Kalimar on 2007-06-06
I followed the directions for removing the quiet splash, here's what we got (I didn't include the first half that seems to have gone well):
.
.
.
Success: Loaded module raid10.
Done.
Begin: Assembling all MD arrays ...
mdadm: No devices listed in conf file were found
Failure: failed to assemble all arrays
Done.
Done.
Begin: Waiting for root file system ... ...
Done.
Check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/294c82a0-3ef7-40c4-917b-6c213ed85916 does not exist. Dropping to a shell!


It then goes to BusyBOX v1.1.3
    
Any new ideas? THAAAAAANKS

---

### Post by logos34 on 2007-06-06
> mdadm: No devices listed in conf file were found
Check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/294c82a0-3ef7-40c4-917b-6c213ed85916 does not exist. Dropping to a shell!

UUID changed on root partition?  Maybe the system assigned a new one which doesn't match the fstab entry.

You could boot from the livecd, open a terminal and type:

ls- l /dev/disk/by-uuid/

which will show all the current uuid's assigned to each partition.  Compare it to the one for / in /etc/fstab.

---

### Post by Kalimar on 2007-06-07
I can`t get the ls  -l /dev/disk/by-uuid/ command to work.
It gives me the following:
ls: /dev/disk/by-uuid/: No such file or directory
Any  help is greatly appreciated. Thanks this forum is fantastic

---

### Post by confused57 on 2007-06-07
You might want to edit your fstab & menu.lst to boot without using UUID's:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc           proc             defaults              0       0
/dev/hda1          /               ext3      defaults,errors=remount-ro   0       1
/dev/hda5          none            swap         sw                        0       0
```

Change your kernel root to root=/dev/hda1, instead of using the UUID.

I don't know if using "/dev/evms/hda1"  and  "/dev/evms/hda5"  will work in fstab or not, in order to utilize evms.

---

### Post by confused57 on 2007-06-07
I didn't have much time when I posted my last reply, but I wanted to post my Dapper fstab & menu.lst entries:
```
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

```
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot
```

You may be able to use these as an example of how yours should look without UUID's...

---

### Post by Kalimar on 2007-06-08
well, I finally gave up and reinstalled 7.04 :( It works fine for now. I'm just glad I didn't have too much set-up yet when this happened. I wonder if there might have been something deeper causing problems having installed and uninstalled some apps like automatix and vmware. Thanks for all your help and patience. Like I've said before, this forum ROCKS!!!!!!
UBUNTU ROCKS!

---

