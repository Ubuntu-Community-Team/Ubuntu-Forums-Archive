---
title: "error 15"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by Xanthous on 2005-06-22
I've been running Hoary for @ 2 months now.  Now I installed a second HD and in the process of trying to make it accessible, I must have messed up the boot sequence or something.
I re-booted and now Ubuntu doesn't load.  I get the following:
Grub loading, please wait:
Error 15

And it hangs there...doesn't go any further.  Re-installing Ubuntu is not something I want to consider, due to the information currently on there.

:cry: Help please!  Thank you so much.

---

### Post by irusun on 2005-06-22
You didn't provide much detail on what you did, but...

Grub Error 15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

Sounds like grub can no longer find the grub menu.lst file.  This would typically happen if you changed the partition order on your existing drive or your existing drive is no longer in the original location (e.g. your new drive is now the master and your existing drive is now the slave).  What happens if you take the new drive out and return it to the original configuration?

If you think you need to reinstall grub:

First, you'll need a grub boot disk - you can't "install" grub while using the hard drive.

This assumes that you want grub as your boot manager:

Boot the grub disk.  At the command line, search for the file name “/boot/grub/stage1”, which shows the devices which contain the file.

grub> find /boot/grub/stage1

Then you can run the root command using the correct partition based on the results.

For example:

grub> root (hd0,1)

Once you've set the root device correctly, run the command "setup". This command will install GRUB on the MBR in the first drive.

grub> setup (hd0)

---

### Post by Xanthous on 2005-06-23
Thank you irusun for taking your time to help out here.

Before you answered, and after browsing through dozens of posts, and trying different things, I managed to get it to boot, and everything is back as normal.

The thing is, I didn't get more then "error 15", that's why I didn't post any more then that.

Now, I am concerned that my grub file is configured properly, and I am leary of re-booting incase it hangs again.  I need help to know if I am configured properly.
Please let me know if more info is needed.
Thank you!!

Hardware:
P4 / 512 ram / 128 radeon / DVD / 2x 80 GB

"sudo fdisk -l" output:
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1991    15992676   83  Linux
/dev/hda2            1992        9729    62155485    f  W95 Ext'd (LBA)
/dev/hda5            2081        5920    30844768+   7  HPFS/NTFS
/dev/hda6            5921        9729    30595761    7  HPFS/NTFS
/dev/hda7            1992        2080      714829+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10011    80413326   83  Linux
```

"/etc/fstab" info:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none        swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/dv       ntfs    umask=0222      0       0
/dev/hda6       /media/ang      ntfs    umask=0222      0       0
/dev/hdb1        /media/drive           ext3        defaults        0       1
```

gub/menu.lst:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by irusun on 2005-06-24
[QUOTE=Xanthous]Now, I am concerned that my grub file is configured properly, and I am leary of re-booting incase it hangs again.  I need help to know if I am configured properly.[/QUOTE]
Nothing looks out of the ordinary... but the key is what you did to get it to boot.  Unless there's faulty hardware, grub either works or it doesn't.  It's not flakey software.  Best I can say is now that you're back and running, backup all your important data and then try rebooting.  Sorry I can't be of more help.  Maybe someone else can take it from here.  Good luck!

---

### Post by fmcdee on 2005-10-20
I've been searching for this post for some time,  I added partitions to my HD using partition Magic. It added them, reported no problems and I continued to use MSXP to check a few items. I did not add or subtract anything to the HD0 start that I know of.  I am getting the message GRUB and then error 15.  Nothing else. I don't  have a Grub disk, where can I get one or is there some other way to access the boot area to correct the problem.  My Thanks. FMCDEE  
P>S> I have used Ubuntu on the HP4805ze for several monthes and had no problems with it to amount to anything.

---

### Post by hayim on 2006-08-08
Xanthous, 
good to hear you solved it, but would love to also hear how?

I just had a similar problem, and NO IDEA why.
I didnt change any partitions on the disk (i did change partitions on an external disk..?) but i got that:

Grub 1.5

Grub Loading, please wait
error 15

then nothing. I follwed advices to reinstall grub, by booting from the LiveCD, then running 'sudo grub', and from the grub prompt 'find /boot/grub/stage1'. This found my grub install at (hd0,5). So i 'root (hd0,5)' and 'setup (hd0)' to reinstall.

Sounds good? Wrong. I got Grub back, but Grub got all the drives wrong! It looked for kernel files two partitions too far up!

Using the 'edit' option at the Grub menu i changed the values to where the kernels actually were. Bingo!

Was that enough? NO! *somehow* my fstab had also been rewritten! All the partitions were wrong. Ubuntu failed trying to mount my /home drive on an NTFS partition... PLUS, my actual root partition was mounted as /swap :s. Boy was i scared important things had just been wiped....

Nano'd /etc/fstab and all seems to be in order...  It loads, there are files...

the ONLY question i have is... WHY? 

any ideas? thx, hayim.
ps. i did try 'update-grub' before i worked out how to grub> setuo (hd0) - not sure what diff that made.

---

### Post by Xanthous on 2006-08-09
Wow, this is a old topic.  

I'm sorry, but I don't remember what happened.  It may have been the jumper settings on the new HD, but I can't confirm that.

For the last year I've switched and stuck with Mepis, so I am out of the loop in the Ubuntu area.  

Hope you can sort it out.  ;)

---

### Post by everlasting.puneet on 2007-09-17
plz help me tooo!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :(

i have installed ubuntu a year ago n now i dont know due to some reasons my grub loder started showing  error 17 
which i have tried to sort out but there are some problems it is showing
it is showing 
grub> find /boot/grub/stage1
 (hd0,8)

grub> root (hd0,8)     

grub> setup (hd0,8)         
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,8)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,8)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,8) /boot/grub/stage2 p /boot/grub/menu
.lst "... failed

Error 22: No such partition

grub> 
 

this has installed the grub but now it is showing error 15 for my linux partitions while detecting the windows one...
god plzzz help meeee...
there is very important data in my linux so dont wanna reinstall

---

