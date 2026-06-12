---
title: "grub confused with sata hdd?"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by terus on 2007-01-05
Hi all, 
another newbie and I am getting a bit desperate: I installed from the live CD on my WinXP system which has one ATA HDD and two SATA HDDs. Windows boots from sda and I installed Ubuntu on sdb.
However when installing from the desktop the installation stopped with an error message. Then i used the text install to do the following:
hd0: one partition ntfs on IDE
sda has three partitions, all NTFS with the first (primary) partition as boot disc
sdb has four partitions, first one ntfs 100gb for windows data, second is root with 40 gb, swap with 3 GB and boot with 500 MB

Not sure if that is a good setup but the installer did not complain about my choices there.

However Grub insists on installing to HD0 and when I reboot only winxp (which I want to get rid off) appears.

So I read lots of things about install-grub and issues with SATA discs, but I would think this should not be so hard. 

I can't even understand how to access my files on the sda, sdb or hd0 from the live CD - my linux knowledge is not worth mentioning. I know that this way you learn most but I can't get the blasted thing started so a little help would be great.

Please let me know if you need more information.

Cheers,

terus

---

### Post by logos34 on 2007-01-05
Hopefully someone with experience using grub will jump in here at some point to help you, but there are a couple of things you can do in the meantime...

Turn off your pc and disconnect the ide/pata drive.  Reboot and it should go into windows on your first sata (sda).  The best solution is then to wipe grub off 'hd0' (or 'hda1' to linux os) and put grub on the mbr of sda so that on bootup you get the grub menu and can choose windows or linux (on sdb). 

[This]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29") explains how to use the LiveCd to (re)install grub ('Troubleshooting' section onwards.)  Remember you will also need to mount your separate /boot partition in the livecd session.

If you are afraid of screwing something up, just use the livecd to get to the following files and post them here (or if the livecd won't let you online save to a floppy or usb thumb drive):

from a terminal:

sudo -i (for root access)
mkdir /mnt/work
mkdir /mnt/work2
mount /dev/sdb2 /mnt/work (or whatever the # of your / partition)
mount /dev/sdb4 /mnt/work2 (or whatever the # of your boot partition)

then
cat /mnt/work2/boot/grub/menu.lst
cat /mnt/work2/boot/grub/device.map
fdisk -l
cat /mnt/work/etc/fstab

when done 
umount /dev/sdb2 /mnt/work
umount /dev/sdb4 /mnt/work2

exit

---

### Post by terus on 2007-01-06
Thanks for the help,

I went through the troubleshooting manual, but in the end all that resulted in my FAT/MBR being totally stuffed on both of my SATA drives. Fixboot from the win install disk got my main disk (and my computer working) back but the other disk was not accessible by anything I tried. (SuperGrub disk, partition magic, partition logic,...

So this is unfortunately the second time that I am left with a stuffed up hdd after a brief venture into linux. And I really would like to get it working.

Thanks to extensive backups no harm (but lost time) was done.

I will give it another try but before that what can I do to ensure that Grub goes onto the right mbr?

One possible problem could be that my SATA disks order seems to be mixed up. In WinXP diskmanagment disk0 is not the boot disk, so perhaps I should change the cables around?

There is only one OS (winxp) on sdb1,0 but I thought Grub would find that anyway?

So right now no printouts, I have to install new after the weekend, but I haven't given up yet.

---

### Post by logos34 on 2007-01-06
so let me get this right: you restored the mbr on sda (windows) and its working fine but sdb (with ntfs and linux) is inaccessible? And is sdb that the disk you want grub to install to?

One surefire way of assuring grub goes to the target drive is to unplug the power cables to the others...then it has no choice!  Then all you have to do is manually add entries in your fstab file for the other drives/partitions.

You could change sda to the first sata channel...don't know if that will confuse windows or not.

---

### Post by terus on 2007-01-07
Yep - that is right, sda is ok and boots thanks to fixmbr, but sdb is gone. Now it doesn't contain anything, it is freshly formatted and waiting for me to take a deep breath and start this all over again. Would you recommend to use the first partition for Ubuntu? I have the choice now, the disk is 160 GB and I am thinking of giving 30 GB for Ubuntu but need the rest for data.

Unplugging won't work as I am installing Ubuntu on sdb and want GRUB to write to the MBR on sda (the only active/bootable partition).

I will try and swap cables, if that confuses Windows I can always swap back.

So much trouble...

Thanks again!

---

### Post by logos34 on 2007-01-07
sorry for the tardy reply. 

> want GRUB to write to the MBR on sda (the only active/bootable partition)
That was my first suggestion and the most common setup (grub has never caused me a single problem on my dual boot).  But if you want to leave windows bootloader intact you could just as well put grub on sdb and set it as first in BIOS boot priority.  Then you'll boot into grub on sdb which will give you a choice of linux on that disk or windows on sda.  If sdb ever gets messed up you will still have a bootable windows disk on sda1--just change the order in the bios.

> Would you recommend to use the first partition for Ubuntu? I have the choice now, the disk is 160 GB and I am thinking of giving 30 GB for Ubuntu but need the rest for data.
No, put your NTFS data partition first, so that you can more easily shrink it and expand linux at a later date (and chances are you will want to do so). Better yet, consider formatting it as FAT32 instead of NTFS.  That way you can read AND write to it from windows and linux. (Unless you have like huge video files over 4GB--then it would have to be ntfs). If it must be ntfs and you want write access from within linux, check out NTFS-3G (though there is a slight degree of risk involved).  To read your linux files from windows get Explore2fs.     

I'd put /swap and /boot inside an extended partition, killing two birds with one stone--that'll leave you the option of adding another primary partition (say, for another linux distro). If you go with a NTFS partition, you could create a separate ext3 (or fat32) 'home' partition...it makes upgrading to a future Ubuntu release a cinch...you can just reformat/overwrite your root partition without the hassle of having to backup all your documents and settings (though you might want to do so anyway in the unlikely event things go terribly wrong!). 

Check out these links: 						
[Dualboot Two Hard Drives]("http://www.ubuntuforums.org/showthread.php?t=179902")
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")
[Partitioning Windows and Ubuntu]("http://www.psychocats.net/ubuntu/partitioning")


Feel free to post back with your results!

---

### Post by terus on 2007-01-07
Hi again,

so I have installed again, this time following the advice on the many links and articles I read. To achieve less hassle I unplugged everything but the one SATA drive Ubuntu will live on.

This worked well until I added the second SATA drive after the install. 

With only one disk and no edits to the GRUB file all worked well. And it looks pretty, too :)

But then I added the second (really the first) SATA disk with my WinXP on it. Tried to edit GRUB following the guidelines and got it so far that the GRUB menu shows Windows XP but when I select it there is only the message 'starting up'...

Then nothing happens.

When I select Ubuntu I get an error 17 I think - operating system not found.
I suspect this can be solved with changing around the hd0 and hd1 or do I have to add a map (hd0) something to the windows entry?
I thought I don't have to as it is already hd0 anyway...

I feel I am nearly there.

Here is the menu.lst AFTER my edits:

## ## End Default Options ##

title		Microsoft Windows XP Professional
root		(hd0,0)
chainloader	+1

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

And here it is BEFORE (with only one disk and when it worked):

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by logos34 on 2007-01-07
You should put windows at the end after 

'### END DEBIAN AUTOMAGIC KERNELS LIST'

But first, post the output from these commands:

> sudo fdisk -l
> cat /etc/fstab

Since you had the other drive unplugged you need to create a mount point for it and add it to fstab file.

---

### Post by logos34 on 2007-01-07
Here's mine:
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
[B]
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		      Windows XP Professional x64 Edition
root		     (hd0,0)
savedefault
makeactive
chainloader	 +1[/B]

Copy and paste that last part, altering it so it reads thus:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		       Windows XP Professional
root		      (hd1,0)
savedefault
makeactive
chainloader	  +1

---

### Post by logos34 on 2007-01-07
> When I select Ubuntu I get an error 17 I think - operating system not found.
I suspect this can be solved with changing around the hd0 and hd1 or do I have to add a map (hd0) something to the windows entry?
I thought I don't have to as it is already hd0 anyway...

yes, and you have to add  it to your /boot/grub/device.map file so it reads:

> (hd0)   /dev/sda
(hd1)   /dev/sdb

---

### Post by logos34 on 2007-01-07
It might be easier to do the install again (you can't edit the files because you can't boot into linux! -- it's been a long day...)

But leave the menu.lst so it reads 'root (hd0,1)' -- which linux sees as 'sda2' -- because that is how the entry for your root partition should show up in fstab (it's the only sata connected at install).

---

### Post by terus on 2007-01-07
Hi again - that was a very quick reply. I understand the issue about the disc not being mounted and will fix the place of the entry in the menu.lst but here is the output for fdisk -l:

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       19457   146046915    f  W95 Ext'd (LBA)
/dev/sda5            1276        5099    30716248+   7  HPFS/NTFS
/dev/sda6            5100       14024    71690031    7  HPFS/NTFS
/dev/sda7           14025       19457    43640541    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17433   140030541    7  HPFS/NTFS
/dev/sdb2           17434       17497      514080   83  Linux
/dev/sdb3           17498       19457    15743700    5  Extended
/dev/sdb5           17498       18134     5116671   83  Linux
/dev/sdb6           18135       19177     8377866   83  Linux
/dev/sdb7           19178       19457     2249068+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I created boot in sdb2 and then home and root in the extended partition, root is sdb5 and home is sdb6. Windows boots from sda1,

This is cat /etc/fstab

root@ubuntu:/# cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

And I guess that is not right - but no idea what to do here.

Thanks!

---

### Post by logos34 on 2007-01-07
oh, I assumed root was the second partition.  

The fstab's not right.  You're on the livecd?

---

### Post by logos34 on 2007-01-07
You have to mount your root and /boot partitions to get to the fstab and device.map files.  Use my instructions in Post #2 to do so and then post them.

---

### Post by terus on 2007-01-08
Thanks for your help - but I am about to give this whole experience another miss. How hard can it be to get two operating systems booting from two discs??

By now I have a working Ubuntu on one disk but only if the other one is unplugged :(

Also I don't really like to use the BIOS each time when I want to boot into another OS.

When I connect the second disk this is what I get:

[IMG]http://i48.photobucket.com/albums/f219/testoroni/ubuntu.jpg[/IMG]

No idea what that means. I tried to edit the menu.lst and device.map as you suggested but no success, all I get is the above.

And I can only run fdisk -l when no second disk is connected, so that wouldn't be much help, is that correct?

Any other ideas?

Cheers,

Matt

---

### Post by logos34 on 2007-01-08
Shouldn't be this hard...I was dual-booting with two disks until recently (albeit pata master/slave) and didn't have any trouble.  

First step: you need to post ALL your relevant setup info so I can see exactly what's going on, and if I can't help someone else reading this will.  
> 
sudo fdisk -l
cat /etc/fstab
your menu.lst and device.map files (wherever they are)


What sata channel do you have the linux drive on?

---

### Post by terus on 2007-01-08
OK, here we go. 
Thanks heaps, the thing I like most about Ubuntu so far is your support :-D 

I would have given up on my own...

As I wrote before, the below results are only valid for booting with the second disc unplugged as i can't boot with both of them plugged in.
I tried before booting from the live cd and then mounting the installed system, when I do that the linux disk is sdb not sda. I also tried to add the second disk in the device.map, both ways and no success either.

The disk is on SATA channel 2 I think, but I will post this now and boot again to make sure.
I'll post straight away
Just done that - it is channel 3 so my windows disk is on channel 2. Not sure why this is so, I probably could change the plugs on the mainboard to 
if the channels are important.


So here is fdisk -l

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       17433   140030541    7  HPFS/NTFS
/dev/sda2           17434       18070     5116702+  83  Linux
/dev/sda3           18071       19177     8891977+  83  Linux
/dev/sda4           19178       19457     2249100   82  Linux swap / Solaris

cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7d3f73fe-db85-4af0-8693-13aa73cd75c8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=7bfd2b7a-f12f-4c16-80f4-bcd2ed3e1ea0 /home           ext3    defaults        0       2
# /dev/sda1
UUID=4ABCD30BBCD2F105 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=d02d1dd7-fc1f-47fc-8bd3-5a5c018dbc2c none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


device.map

(hd0)	/dev/sda


menu.lst:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
savedefault
makeactive
chainloader +1

---

### Post by logos34 on 2007-01-08
seems you're not alone with this 'busybox' error...take a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=292533&page=3").

---

### Post by logos34 on 2007-01-08
Everything looks correct on your files.
> it is channel 3 so my windows disk is on channel 2. Not sure why this is so, I probably could change the plugs on the mainboard to if the channels are important.

Yeah, switch 'em, see if that works.  Or try putting the linux on sata1 and windows on sata2 (worked for one poster in the thread above).

---

### Post by logos34 on 2007-01-08
And as soon as you can bootup with both drives attached without any error messages, run sudo fdisk -l again and post it.

This has got to be a simple issue of sata channels. (I hope!)

---

### Post by terus on 2007-01-08
Ok - here is my latest:

I followed the link you gave me and read all about the problems other people were having.
So I edited the file as recommended - no change.
Then I changed the order of my disks and voila, Grub booted into ubuntu.

I have been trying to add a mount point for the other disk and have been able to mount sdb1 but not the others (error messages in mount) and also am not sure about how to give permissions.

The device.map needs changing as it is still:

(hd0) /dev/sda

But I wait and here what you advice.

menu.lst is unchanged.


Here is my fdisk -l

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 17433 140030541 7 HPFS/NTFS
/dev/sda2 17434 18070 5116702+ 83 Linux
/dev/sda3 18071 19177 8891977+ 83 Linux
/dev/sda4 19178 19457 2249100 82 Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 1275 10241406 7 HPFS/NTFS
/dev/sdb2 1276 19457 146046915 f W95 Ext'd (LBA)
/dev/sdb5 1276 5099 30716248+ 7 HPFS/NTFS
/dev/sdb6 5100 14024 71690031 7 HPFS/NTFS
/dev/sdb7 14025 19457 43640541 7 HPFS/NTFS


And here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=7d3f73fe-db85-4af0-8693-13aa73cd75c8 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3
UUID=7bfd2b7a-f12f-4c16-80f4-bcd2ed3e1ea0 /home ext3 defaults 0 2
# /dev/sda1
UUID=4ABCD30BBCD2F105 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda4
UUID=d02d1dd7-fc1f-47fc-8bd3-5a5c018dbc2c none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

---

### Post by terus on 2007-01-08
here is the output of ls /dev/disk/by-uuid/ -alh
And I have updated the device.map

We are getting somewhere!


total 0
drwxr-xr-x 2 root root 200 2007-01-09 23:54 .
drwxr-xr-x 6 root root 120 2007-01-09 23:54 ..
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 0224223F24223657 -> ../../sdb7
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 4ABCD30BBCD2F105 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 58E4D6C3E4D6A314 -> ../../sdb6
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 7834BF3C34BEFBE6 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 7bfd2b7a-f12f-4c16-80f4-bcd2ed3e1ea0 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 7d3f73fe-db85-4af0-8693-13aa73cd75c8 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 d02d1dd7-fc1f-47fc-8bd3-5a5c018dbc2c -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-01-09 23:54 FC7C3BE37C3B96FC -> ../../sdb1

---

### Post by terus on 2007-01-09
Just to let everyone with a similar problem know how it worked out in the end:

Installed on the non Windows disk to leave the MBR untouched by unplugging during install
The next problem was the IDE channel order (even though my 2 disks are SATA the BIOS reports them as IDE during POST). Make sure your Ubuntu disk is the first not, like on my system, the second. 
So when I could boot Ubuntu with both disks connected it was just a matter of cleaning up the menu.lst for Grub.

Thanks to a very patient guide (three cheers for Logos34) and some other posts on the same subject we got it all sorted out - the key was the mapping of drives to trick winxp into thinking it is on the first disk.

Now I can go and explore!

Cheers,

Matt

---

