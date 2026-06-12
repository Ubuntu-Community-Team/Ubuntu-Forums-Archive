---
title: "Grub Error 18"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by spacecowboy706 on 2006-10-14
I just got a new computer (actually used but it's new for me) and i put in 2 hard drives.... one Hardrive is a 80GB and i did a fresh install of Windows XP pro and it workes fine.... the second hard drive is a 140GB and i did a fresh install of Ubuntu 6.06 from the live cd and it doesnt work at all. The 80GB windows drive is set as the master and the 140GB Ubuntu drive is set as the slave. 

If i change the bios to have the 80GB Windows drive selected as the boot device i get the "error loading grub, error 18" message.

If i change the bios to have the 140GB Ubuntu drive selected as the boot device i get the error message "Error loading operating system".

I know that the live cd is good cause i used to install ubuntu on my old system last week and it worked fine.

I have read through other similar posts about this problem and none of those fixes worked, for my problem.

Working from the live cd as i cant get either the Ubuntu or windows os's to boot now....

Here are the output commands requested from nearly all the other grub error related threads:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10336    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19269   154778211   83  Linux
/dev/hdb2           19270       19457     1510110    5  Extended
/dev/hdb5           19270       19457     1510078+  82  Linux swap / Solaris

gksudo gedit /boot/grub/menu.lst .....just open a file with nothing on it.

ubuntu@ubuntu:~$ sudo grub

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd0,0)
 Filesystem type unknown, partition type 0x7

grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,0) [COLOR="Red"]<---- i have alkso tried "setup (hd1,0)" SAME RESULTS[/COLOR]
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd0,0) /boot/grub/stage2 p /boot/grub/me
nu.lst "... succeeded
Done.

grub> quit

AND STILL I GET THE SAME ERROR MESSAGES AFTER RESTARTING.... PLEASE HELP

---

### Post by Kateikyoushi on 2006-10-14
This is what I found about grub error 18.
An empty grub menu.lst doesn't sound good either. What is in your /boot folder ?

> Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

---

### Post by louieb on 2006-10-14
Here is a simple menu.lst that you can try. windows on master ubuntu on slave. Check the file names of kernel and initrd. Those files or something close to those names should be in your /boot directory.  You might have a diffrent kernel and initrd version. Just make sure the file name in this example match what is in your /boot directory.  
Not sure if Ubuntu will work but windows should.
```
default 0
timeout 10

title		Ubuntu, kernel 2.6.15-27-386
root            (hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-27-386 (Recovery mode)
root            (hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro  
initrd		/boot/initrd.img-2.6.15-27-386
boot
title Win XP 
                rootnoverify (hd0,0)
                chainloader +1
                makeactive
                boot

```

---

### Post by confused57 on 2006-10-14
You might want to restore your Windows mbr, using the Windows install cd:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Once you're able to boot Windows, you may want to consider setting your system up this way:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you continue to get the grub error 18, there's an outside possiblity you need to update your bios...that's just a wild guess, probably not the problem.  I'm definitely not a bios expert, but there may be an option to enable LBA if it isn't already.

When you tried to reinstall grub, you probably should have used setup (hd0), which installs to the mbr. Using setup (hd0,0) installs on the Windows partition and I'm not sure what effect this will have on booting Windows...**fixboot** &/or **fixmbr** may repair it.

---

### Post by spacecowboy706 on 2006-10-14
**[COLOR="Red"]Kateikyoushi[/COLOR]**, Im not sure what your trying to tell me with that post but it didn't contain any instructions on how to possibly correct my problem?

**[COLOR="Red"]louieb[/COLOR]**, I redid the command sudo gedit /boot/grub/menu.lst from a terminal which opened a document titled menu.lst. The document was empty and i pasted over the information you gave me and when i clicked the save button i got "Could not save the file, File not found /boot/grub/menu.lst." all i could do was cancel it at that point.

**[COLOR="Red"]confused57[/COLOR]**, I followed the link, you provided, to restore the windows mbr and now when i select the small 80GB windows device in the Bios as the selected boot device all i get is the same menu as if i were typing "sudo grub" in a terminal? Not sure what else im supposed to do there so i just exit out of it.


I appreciate all of your attempts to help, but i am still in the same predicament... "not able to boot into either OS and having to work off of the live CD." More help to resolve this problem would be greatly appreciated?

PS... when making suggustions please give "[COLOR="Red"]How to Step's[/COLOR]" i know a little about linux, but im still in the noob category :-D

---

### Post by Sef on 2006-10-14
> Kateikyoushi, Im not sure what your trying to tell me with that post but it didn't contain any instructions on how to possibly correct my problem?

Actually it did contain an answer to your problem:

> This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

I would download [GParted]("http://sourceforge.net/projects/gparted") and use that to create a boot partition. This is the download page.

---

### Post by spacecowboy706 on 2006-10-14
From my last post...

> PS... when making suggustions please give "How to Step's" i know a little about linux, but im still in the noob category

Again I am a "NOOB" i dont know how to creat partitions using g parted... but it doesnt matter anyways since i just [COLOR="Red"]reformatted both drives[/COLOR] and reinstalled windows to the small drive and it is working fine...

What i dont understand is that i didn't have these problems last time i installed ubuntu on the older computer.... Why am i having problems this time around?

---

### Post by confused57 on 2006-10-14
Sorry you had to reinstall everything, it takes time to learn Linux...a little at a time for me.
You might want to checkout Herman's replies near the end of this thread concerning bootloaders:
[http://www.ubuntuforums.org/showthread.php?t=277241](http://www.ubuntuforums.org/showthread.php?t=277241)

---

### Post by spacecowboy706 on 2006-10-14
I am starting to get angry at this pc... I have removed the windows hard drive and am just using the 160GB Ubuntu drive now. I just got done reformatting it to erase everything on it. Now I just installed Ubuntu and upon completion of the installation it said i had to restart the pc to complete it. Up to now that is normal...

When i restarted the pc i am now getting the same dang "Grub error 18 message". How is this even possible there is only 1 hd in the pc and it was raw, with no OS on it when i istalled ubuntu.

Again im using the live cd... What do i have to do to make ubuntu work on this PC? ](*,) 

here are the outputs from sudo fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19269   154778211   83  Linux
/dev/hdb2           19270       19457     1510110    5  Extended
/dev/hdb5           19270       19457     1510078+  82  Linux swap / Solaris

ubuntu@ubuntu:~$gksudo gedit /boot/grub/menu.lst
<<<<<<<<< It still has nothing in it, just like before >>>>>>>>>>>
<<<<< and this is what i get, before the blank page loads >>>>>>>>

(gedit:6759): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


and from the grub configuration this is what i get:

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit

ubuntu@ubuntu:~$ exit

and then i restart the pc, making sure to remove the live cd before it quits... and im right back to the "Grub error 18" message.

Someone please help me get this dang thing working?

---

### Post by Herman on 2006-10-14
Well, I'm sorry I didn't get time to participate in this thread too, but Kateikyoushi, confused57 and sef were already saying what I would have said anyway. Here's the link to my info about Grub error 18 on my Super Grub Disk Page, 
Grub error 18.............................................................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")
So I think I agree with you fellows, it probably has something to so with the way the BIOS reads the larger hard disk. I'm glad it's fixed now, but I think any of those possible solutions would have likely worked.  You guys were already doing a good job. I was going to suggest making the Ubuntu partition smaller with GParted maybe.

This error message collection I'm starting is beginning with the error messages out of the Grub manual, but I'm adding extra info to them as I can gather it, from wherever I can.   It's still in its early stages so far though.

Regards, Herman :D

EDIT: Whoops! The error is back! Oh no! Okay , try going into your BIOS and taking a look around at how it's set up and see if there's anything there that you can see (settings) that can be improved. (Refer to the link I gave above)
If that doesn't work, try shrinking your Ubuntu partition on that big hard disk maybe, too, so your BIOS can see it all. 
Like sef suggested, you can use a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), that's the best tool for the job. Gparted in the Ubuntu Live CD should work okay though. :-D
Maybe you will be able to get it working by making an extended partition and installing Ubuntu in a logical partition inside that, as has solved the problem for some other people with the same error message.

---

### Post by spacecowboy706 on 2006-10-14
ok i will try to shrink down the partition.... but that was kinda why i was wanting to move ubunto to this hard drive.. for the size... i need the full 160GB for video editing.. the 80GB drive that works on the old pc is nearly full? after repartitioning can i use the extra partitions for storage space from Ubuntu?

---

### Post by Herman on 2006-10-15
Yes, probably, but I'm not sure. We'll have to Just try it and see.

 In the olden times when they had the 8.0 GB limit, so I have read, they used to leave Windows in the first 7 1/2 GB or so, and have their /boot partition just inside the limit.  Either that or have the /boot partition first, then Windows, then Linux after the 8.0 GB limit, because Linux could handle being outside the limit, but Windows couldn't. As long as the Linux kernel was insdie the limit, it used to work, so people could use a much larger hard disk when they used Linux in those days. Well, that's what I've read.

Here's what the PC Guide has to say about the 137 GB hard disk size barrier, [http://www.pcguide.com/ref/hdd/bios/sizeGB128-c.html](http://www.pcguide.com/ref/hdd/bios/sizeGB128-c.html), do you think it could be this that's your problem, or something else?
 
Even some of the newest computers are getting such large and modern hard disks, sata in particular, that the hardware still tends to be a little ahead of the software. That's just progress I guess. Would it be a Sata disk, or IDE?

---

### Post by spacecowboy706 on 2006-10-15
Im here for the next 8 hours if need be.... i resized like you said and now i am getting a different grub error message. I also went through the bios and made the changes you suggested on your web page as well:

Bios changes...LBA is already enabled and set to auto... there is no option to switch it to normal? HD detection was already set to Auto.

the new grub error message is "Grub error 17"

---

### Post by Herman on 2006-10-15
Bah! Another Grub error! 
Well, we appear to be making progress, at least we got away from error 18!
Those BIOS changes are from answers I collected by googling as well as searches of this web forum, they are good for clues as to how others have solved the same or similar problem, but might or might not be exact for another problem, but they should generally point us in the right direction.  Don't worry if you can't see a certian option in your  BIOS, there are lots of different BIOSes made.  It could be like looking for a radiator in one of those famous old volkswagons. :D

 Okay, I'll stick with you for as long as it takes. I still have to go  to work Monday morning though. :D (Unfortunatley).

Grub error 17.........................................................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17")

---

### Post by Herman on 2006-10-15
>              If you get this error when trying to boot Linux, check your grub conf. or menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct.
           
            You will need Super Grub Disk to boot Linux for you so that you can easily check and repair your operating system's entry in menu.lst. 
            Super Grub can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...Well, there are two or three other ways of dealing with this problem, depending on what you have available.
If you have a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), that makes it a lot easier.

If you have the Ubuntu Dapper Drake Live/Install CD, that will do fine too.
Here's how to access your menu.lst file in your installed OS from the LiveCD, I'm not sure how you were doing it when you were getting the blank gedit page, but try this way,             

Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD...........[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

If you need any help, just post a copy of your menu.lst here, and I'll take a look at it for you. I think we already have your fdisk details in an earlier post.

---

### Post by spacecowboy706 on 2006-10-15
here is the menu.lst (THAT IS NOT BLANK ANYMORE).... What do I do with it... i wasn't sure if i needed to use:

sudo mount -t reiserfs /dev/hda7 /media/hda7

or

 sudo mount -o loop -t iso9660 /home/username/name_of_file.iso /media/mountpoint

or if i just needed to change somethinf in here?????

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Herman on 2006-10-15
> here is the menu.lst (THAT IS NOT BLANK ANYMORE)....  Yup, excellent! :D

> What do I do with it... i wasn't sure if i needed to use:
sudo mount -t reiserfs /dev/hda7 /media/hda7 or sudo mount -o loop -t iso9660 /home/username/name_of_file.iso /media/mountpoint
 No-no, those have nothing to do with menu.lst, those are for /etc/fstab, that's okay, just ignore those for now. :D
>  or if i just needed to change somethinf in here????? Yeah, I'll get back to you in a minute with some changes. ...

---

### Post by Herman on 2006-10-15
```
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##


title Ubuntu, kernel 2.6.15-26-386 
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot


title Ubuntu, kernel 2.6.15-26-386 (recovery mode) 
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot


title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP 
rootnoverify        (hd0,0)
savedefault
makeactive
chainloader    +1

```Try replacing it with this one instead, just 'Edit'-->'Select All'-->'Delete' the text off the one you have, it was no good anyway, and copy the above and paste it on there instead and save it.
That should be right according to the fdisk info you posted earlier.

If not, I'm still here to help, but that should fix it. 

Regards, Herman :D

---

### Post by spacecowboy706 on 2006-10-15
Replaced it just like you instructed... and rebooted.... and "Grub Error Message 17"... what next?

---

### Post by spacecowboy706 on 2006-10-15
is it normal for a single hard drive system that is wanting to use just ubuntu and no other os's to have problems like this... or am i just special... My older pc runs ubuntu like a champ.. but it has a 80GB windows drive and an 80gb ubuntu drive...and the install for it was as easy as 1...2....3 your done?

---

### Post by spacecowboy706 on 2006-10-15
I have also noticed that while using this live cd i get a tiny white line that runs horizontally across the screen when i am at the very first menu where you select either start/install, memory test, safe graphics mode, ect...... i have also noticed that it runs really slow and locks up if i try to open and run more than two programs at a time...

maybee this cd has a scratch on it, or the cd drive is messed up... not sure but im going to shutdown and pull this cd drive out and put the cd drive in from my older pc as it is a much more expensive one, and then log on to windows and download a new iso and burn it to cd, thenm try a new install again on the ubuntu drive. 

this whole process could take about 3 or 4 hours, and may or may not work, so i will be back in about that time... if you have to go for now that is fine, but if you would check back tomorrow that would be great.

---

### Post by confused57 on 2006-10-15
You still might want to consider this setup as an option:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

This would involve installing Ubuntu onto your 160 Gb drive setup as master, then connecting the Window's drive as slave...you'd just need to edit your /boot/grub/menu.lst to boot your Windows drive.  I'm sure you already know you'd need to change the jumper settings on the hd's, or have them set to cable select, if supported.

If you're going to download another iso, you might want to consider downloading the alternate cd and install with a separate home partition, as described on Herman's website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
There are excellent screenshots of installation with the alternate cd...although it's for dual-booting with Windows, it'd still be the same procedure, basically, for installing just Ubuntu with a separate home and a swap partition.

If you use the desktop live cd, you could follow this guide to set up a separate home(manual partitioning):
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Herman, do you think having a separate home partition, and a smaller root partition as a result, help correct the grub boot problems, possibly due to a too large  root partition?  I don't know, I'm just wondering.

---

### Post by Herman on 2006-10-15
> Replaced it just like you instructed... and rebooted.... and "Grub Error Message 17"... what next? Download a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") and either just try to [boot it with that]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#A_Guided_Tour_of_Super_Grub_Disk_0.9508_"), or press 'c' for a [command line]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and use Grub to investigate your computer and boot it. Then use the same commands to edit your menu.lst with.

                                                                                __________________
> is it normal for a single hard drive system that is wanting to use just ubuntu and no other os's to have problems like this... or am i just special... My older pc runs ubuntu like a champ.. but it has a 80GB windows drive and an 80gb ubuntu drive...and the install for it was as easy as 1...2....3 your done? A single hard disk system with just Ubuntu...?  But you said it was a computer with two hard drives with Ubuntu on the second dirve and Windows on the first, > I just got a new computer (actually used but it's new for me) and i put in 2 hard drives.... one Hardrive is a 80GB and i did a fresh install of Windows XP pro and it workes fine.... the second hard drive is a 140GB and i did a fresh install of Ubuntu 6.06 from the live cd and it doesnt work at all. The 80GB windows drive is set as the master and the 140GB Ubuntu drive is set as the slave. Anyway, no, it is relatively unusual to have many problems with Grub, especially with a single hard disk. Unplugging hard disks and swapping things around can conribute to some problems though, Home made computers or old ones that have been doctored up can be more troublesome. 
> maybee this cd has a scratch on it, or the cd drive is messed up... not sure but im going to shutdown and pull this cd drive out and put the cd drive in from my older pc as it is a much more expensive one, and then log on to windows and download a new iso and burn it to cd, thenm try a new install again on the ubuntu drive. Well okay then. Bye for now. :D

---

### Post by Herman on 2006-10-15
> is it normal for a single hard drive system that is wanting to use just ubuntu and no other os's to have problems like this... or am i just special... My older pc runs ubuntu like a champ.. but it has a 80GB windows drive and an 80gb ubuntu drive...and the install for it was as easy as 1...2....3 your done? Aha! Now I see what went wrong, I was looking at your original fdisk output and made your new menu.lst based on that, then later on in the proceedings you unplugged you first hard disk and you were only using that one one its own at the time I gave you the new menu/lst.  Sorry about that.
I think we would have had it fixed by now too. Darn! ](*,)

---

### Post by Herman on 2006-10-15
> Herman, do you think having a separate home partition, and a smaller root partition as a result, help correct the grub boot problems, possibly due to a too large root partition? I don't know, I'm just wondering. I don't know, confused57 I don't think it would make any difference though. 
As far as the error 18 goes, if you keep reading a little further in that link I gave earlier, there's this link at the bottom of that page,  [BIOS Handling of "Oversized" Hard Disks]("http://www.pcguide.com/ref/hdd/bios/sizeHandling-c.html") Different BIOSes handle oversized hard disks in different ways, so it's hard to say for sure if that would be any help or not. 

Regards, Herman :D

---

