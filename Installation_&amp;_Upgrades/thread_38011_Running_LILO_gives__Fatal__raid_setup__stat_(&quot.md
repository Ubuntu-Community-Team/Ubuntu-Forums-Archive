---
title: "Running LILO gives  Fatal : raid_setup : stat (&quot;dev/hdi1&quot;)"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by Robban59 on 2005-05-29
Hi everybody,

a few days ago I screwed my fine Hoary installation, please help a newbie boot up his beloved Ubuntu again  \\:D/ 

I was updating the images of the 686 kernels then I misanswered something related to the boot block during the image installs ( YES instead of NO..maybe.), a LILO script was running after the image downloads, so apparently all was well.
But trying to reboot after i get Uncompressing Linux....it stops with  CRC ERROR.

So off I go with W2K and UBUNTUFORUMS and GOOGLE, but here I am because I can' t fix it myself. 

So my box has 2 HD in RAID-0 with 2 NTFS partitions for W2K, then I have a third HD stand-alone for Ubuntu ( hdi ) but here comes my FSTAB: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdi1       /               ext3    defaults         0       1
/dev/hdi3       /home           ext3    defaults        0       2
/dev/hdi2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 rw,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdi4	/media/Win-D	ntfs   ro,umask=0222	0	0
 
and here comes my lilo.conf ( I deleted all # lines to save space here ) : 
as you can see LILO is installed in the root partition's boot sector, not in the MBR; I boot from W2K by the WIN Utility "bootpart". 
_______________________________________________________________

boot=/dev/hdi1
root=/dev/hdi1
map=/boot/map
delay=20
vga=normal

default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1
    append="expert"
	initrd=/initrd.img

image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
#	restricted
#	alias=2
    append="expert"
	initrd=/initrd.img.old

________________________________________________________________

First thing I saw were the missing soft links in / of the vmlinuz and initrd images in /boot, so I recreated them; then I tried to recover by re-running LILO with the lilo.conf appended above and still present in /etc/ by first booting with Hoary LIVE mounting my real /  in /media and then chroot etc.  and also with Hoary Install running in rescue mode, but everytime I run LILO I get : 

Fatal : raid_setup : stat ("dev/hdi1") 

Why is this ? hdi is NOT in the raid-0, it is the stand alone HD, and has always been recognised as such ( hdi) by Hoary as long as it booted fine.

Another question : is the line _append = "expert"_ correct ??   

I haven't still tried : lilo -r /mnt  , somewhere I read that LILO shouldn' t be run with chroot, because I'm afraid to break the box even more.

I can get any file on my Ubuntu installation through W2K by utilizing "explore2fs", so if some logs or conf files are needed just ask.

You know, it is not nice having a nice Hoary installation unable to boot, and being forced to use W2K all the time.. :cry:  :cry: ...

---

### Post by Robban59 on 2005-05-30
Ok..after a couple of hours fiddling with my system, I have some more info :

I booted with Hoary LIVE CD, then mounted the original Hoary root on my HD to /mnt/ubuntu by 

ubuntu@ubuntu: /  mount -O suid,dev,rw /dev/hdi1 mnt/ubuntu

then I checked the /proc directory of the original Hoary install and the one of Hoary LIVE and I found that the original one is empty, and the LIVE one has the files relevant for the system, among others also "partitions".

So instead of running lilo straight which gives me the error in the subject of this post, I instead run lilo on the LIVE root but using the lilo.conf of the  original installation, also because in the LIVE /etc directory there was no lilo.conf !

So I ran 

1) sudo su
2) /sbin/lilo -C /mnt/ubuntu/etc/lilo.conf

and the response was :

Warning : 'proc/partitions' does not match '/dev' directory structure
                  name change: '/dev dm-0' -> 'dev/dm'
Warning : /dev/hdi1 is not on the first disk   [I]= that's OK I want it this way [U]!
[/I][/U]
Fatal : device mapper : only linear boot device supported

Here we go again with the RAID disks getting in the way, I specify hdi1 which is a SATA stand-alone disk, why does LILO always go after the other two RAID disks ?

I saw in the LIVE /proc/partitions a number of dm-x devices, they must be related to the RAID controller, I don't need them just now to restore lilo, maybe I should try do delete their lines in the /proc/partitions files and try again ? 

Thanks for any suggestions.

---

### Post by Robban59 on 2005-06-08
Please anybody can give me some suggestions ? 

Stilll fighting with my Ubuntu, willing to try antthing before reinstalling... ](*,) 

thanks in advance for any help..

---

### Post by nocturn on 2005-06-10
[QUOTE=Robban59]Please anybody can give me some suggestions ? 

Stilll fighting with my Ubuntu, willing to try antthing before reinstalling... ](*,) 

thanks in advance for any help..[/QUOTE]


I haven't run into this problem, but maybe this helps.

Boot the liveCD
mount your root partition on the HD (e.g. /mnt/hdi)
Chroot to it
chroot /mnt/hdi
Now rerun lilo.

I hope this helps

---

### Post by Joeb on 2005-06-10
[QUOTE=Robban59]Ok..after a couple of hours fiddling with my system, I have some more info :

I booted with Hoary LIVE CD, then mounted the original Hoary root on my HD to /mnt/ubuntu by 

ubuntu@ubuntu: /  mount -O suid,dev,rw /dev/hdi1 mnt/ubuntu

then I checked the /proc directory of the original Hoary install and the one of Hoary LIVE and I found that the original one is empty, and the LIVE one has the files relevant for the system, among others also "partitions".

So instead of running lilo straight which gives me the error in the subject of this post, I instead run lilo on the LIVE root but using the lilo.conf of the  original installation, also because in the LIVE /etc directory there was no lilo.conf !

So I ran 

1) sudo su
2) /sbin/lilo -C /mnt/ubuntu/etc/lilo.conf

and the response was :

Warning : 'proc/partitions' does not match '/dev' directory structure
                  name change: '/dev dm-0' -> 'dev/dm'
Warning : /dev/hdi1 is not on the first disk   [I]= that's OK I want it this way [U]!
[/I][/U]
Fatal : device mapper : only linear boot device supported

Here we go again with the RAID disks getting in the way, I specify hdi1 which is a SATA stand-alone disk, why does LILO always go after the other two RAID disks ?

I saw in the LIVE /proc/partitions a number of dm-x devices, they must be related to the RAID controller, I don't need them just now to restore lilo, maybe I should try do delete their lines in the /proc/partitions files and try again ? 

Thanks for any suggestions.[/QUOTE]



I believe that your /proc on your harddrive should be empty as the contents are created at runtime and when you checked you were using the /proc created in ram from the LiveCD.

As for Lilo, it's been a long time since I used it, but I'm not sure you can just run it against the mounted drive like you did, because I believe it looks for all of those symlinks (like vmlinuz, etc.) that won't exist.  Are you also able to pass Lilo a parameter telling where the boot images are kept (and then point it towards the /boot directory on your hard drive)?

---

### Post by Magneto on 2005-06-13
chroot should be what he needs before addressing installing lilo

why not install grub? its so much nicer to humanity - honestly  :)

---

### Post by alastair on 2005-06-13
Not sure I can help but ....

You say : "my box has 2 HD in RAID-0" and "a third HD stand-alone for Ubuntu ( hdi )"

But you fstab file seems to show "hdi" for Linux and XP. I'm not following your disk layout - what RAID for XP?

---

### Post by Robban59 on 2005-06-14
Hi Magneto,

actually the included FSTAB is incomplete : the 2 RAID-0 HDs are named under Ubuntu HD something like HDE and HDG, not to sure, and HDI is the SATA stand-alone drive, which is partitoned like this : 

1) hdi1 = /
2) hdi2 = swap
3) hdi3 = /home
4) hdi4 = WIN2K drive D mounted in Ubuntu (NTFS)

In the RAID-0 drives there are 2 partitions : C and E; in C lives WIN2K and E is for data; since I have not completed the configuration to mount them at bot time in Ubuntu, they are effectively not seen when booting Ubuntu, they are in that case off-line.

So when I boot the LIVE or Install CDs, and rerun LILO, I get an error as LILO is not able to adress the hdi drive correctly.

I'm a little confused on how to proceed....

_Nocturn_ : what you suggest is what ( I think ..  :)  )  I tried and reported on my second post, isn't it right ? 


Regards/ Robban

---

