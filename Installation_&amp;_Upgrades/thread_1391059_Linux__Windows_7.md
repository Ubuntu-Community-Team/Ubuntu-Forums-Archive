---
title: "Linux / Windows 7"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by ixAndyix on 2010-01-26
I was running Windows 7 Ultimate, 32-bit, but I wanted to try out Linux, so I made a boot disc of Ubuntu (9.04) and selected to install it. The program partitioned my drive, making a new volume (it was only about 2gb). This was all fine, I could choose whether to launch windows or linux at startup. However, I decided that I wanted to remove Linux, so I opened up the drive manager and deleted the partitions it had made. This turned out to be a mistake, as next time I booted up, I got an error - something about "grub error 22". So I used the boot disc to re-install ubuntu to fix the problem. but, this time it seems to have over-written windows 7, and wiped all of my files! I don't have a windows 7 disc because my computer came with it installed already. So now I'm stuck with an operating system I barely know how to use and no means of changing it back, other than getting a product key illegally or spending £170 on windows 7, even though I've already paid for a copy. 

Something rather strange is that when I select properties of my "filesystem", it says I'm using 3.5gb of space and have 6.5gb left. My hard drive is 1tb. However, it isn't showing any other volumes.

Any help would be greatly appreciated, this is causing me. a massive headache. Is there a way to recover windows 7 or at the very least all the files I've lost?

Thanks a lot,
-Andy

---

### Post by Grenage on 2010-01-26
> I opened up the drive manager and deleted the partitions it had made. This turned out to be a mistake, as next time I booted up, I got an error - something about "grub error 22". So I used the boot disc to re-install ubuntu to fix the problem.

Oh dear.  Well you can try something like photorec to get some of the files back, but the Win7 installation is toast.

My advice would be to try and get hold of a copy of Windows 7 and install it, using the code you already own (probably on the base of the computer).  Unless of course you have some recovery disks.  Failing all of that, you could erase the whole drive and try the manufacturer out under a warranty claim.

---

### Post by Cabs21 on 2010-01-26
Sounds like you only have a partition of 12 gb for your OS of ubuntu.  to access the rest of your hard drive you would have to mount it.  Look in media folder for a folder that is not your CD-ROM drive and mount that folder.  This will give you access to the rest of your HDD.  If this does not work use gparted ```
sudo apt-get install gparted
``` to find your other drive and see if it is formatted at all.  (Use the terminal to enter the code shown.  Terminal is in Applications>Accessories>Terminal)  If while in gParted you see that the rest of your drive is still Windows 7 then you might be able to recover the OS but i have no idea how.

If you are hell bent on getting Win 7 back and your computer is fairly new (i am guessing) the store you bought it from will be able to reinstall win 7 for you. (if they are nice)  If this is not the case and you have a warranty for your computer then the warranty should cover your OS restore.

NOW, if all that does not work then Welcome to Ubuntu your stuck unless you pay up.  Sorry.

---

### Post by presence1960 on 2010-01-26
Before you go fiddling around with that hard disk we need to see what you have there. Do not mount your hard disk for if there is a write operation you can kiss goodbye to any chance of recovering data if your disk has indeed been wiped!

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ixAndyix on 2010-01-26
Ok, thanks for the quick response. I tried to boot_inf file. Here's what I got, It looks like windows is gone, but why can't I access the rest of my hard drive?


```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a9d5e7a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *  1,933,519,140 1,953,520,064    20,000,925  83 Linux
/dev/sda2       1,933,117,515 1,933,519,139       401,625   5 Extended
/dev/sda5       1,933,133,580 1,933,519,139       385,560  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3b24c7ff-9eed-4512-90ee-ac56b4900638   ext3                                     
/dev/sda5        d41dd885-325b-4080-80ed-86ae5d6434f4   swap                                     

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

/dev/sda1        /                ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
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
# kopt=root=UUID=3b24c7ff-9eed-4512-90ee-ac56b4900638 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3b24c7ff-9eed-4512-90ee-ac56b4900638

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		3b24c7ff-9eed-4512-90ee-ac56b4900638
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=3b24c7ff-9eed-4512-90ee-ac56b4900638 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		3b24c7ff-9eed-4512-90ee-ac56b4900638
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=3b24c7ff-9eed-4512-90ee-ac56b4900638 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3b24c7ff-9eed-4512-90ee-ac56b4900638
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3b24c7ff-9eed-4512-90ee-ac56b4900638 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3b24c7ff-9eed-4512-90ee-ac56b4900638
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3b24c7ff-9eed-4512-90ee-ac56b4900638 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3b24c7ff-9eed-4512-90ee-ac56b4900638
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3b24c7ff-9eed-4512-90ee-ac56b4900638 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d41dd885-325b-4080-80ed-86ae5d6434f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 993.5GB: boot/grub/menu.lst
 993.5GB: boot/grub/stage2
 993.5GB: boot/initrd.img-2.6.28-11-generic
 993.4GB: boot/initrd.img-2.6.28-17-generic
 993.4GB: boot/vmlinuz-2.6.28-11-generic
 993.4GB: boot/vmlinuz-2.6.28-17-generic
 993.4GB: initrd.img
 993.5GB: initrd.img.old
 993.4GB: vmlinuz
 993.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by ixAndyix on 2010-01-26
UPDATE: after using Gparted, I found that the rest of my hard drive is just unallocated space. Well, that's all my files gone : / What should/can I do now?

---

### Post by Cabs21 on 2010-01-26
try to get your OS system recovered by either the retail store you purchased from or the manufacture of the hardware.  Other then that you are kinda stuck with what you got.  Personally I like ubuntu and would reinstall using the entire drive but that is what I would do.  I dont really like windows anymore but it is up to you.

---

### Post by howefield on 2010-01-26
Are you able to contact your computer vendor about a recovery disk or similar, they should be able to help you even if it costs you ?
That's the price of experience.

Trying this without having your files backed up and a way of getting back to your starting position is asking for trouble.

---

### Post by ixAndyix on 2010-01-26
I guess so :( Thanks for the help either way. Personally, I much prefer Windows (probably because I've always used it and I really have no idea how to use Linux). I'll just have to contact the people I bought my machine from. I guess this isn't such a terrible thing, I was going to upgrade to 64-bit windows soon anyway. I regret not backing up my files however :(

Can someone tell me how to allocate the 900gb or so that's been wiped? Thanks.

---

### Post by darkod on 2010-01-26
> **ixAndyix said:**
> I guess so :( Thanks for the help either way. Personally, I much prefer Windows (probably because I've always used it and I really have no idea how to use Linux). I'll just have to contact the people I bought my machine from. I guess this isn't such a terrible thing, I was going to upgrade to 64-bit windows soon anyway. I regret not backing up my files however :(

Can someone tell me how to allocate the 900gb or so that's been wiped? Thanks.

You might be able to restore with free TestDisk. I haven't used it personally but the description of the software says you can use it for recovery. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And for future reference, after deleting the ubuntu partition all you needed to do was restore windows MBR on your hdd. Of course grub was complaining about missing files since you deleted its config files by deleting the partition. If you just restored windows MBR on the disk, windows would have worked without any issues.

Another remark, if you get into situation like yours, don't panic! The great thing about ubuntu is that you can also boot with the cd, select Try Ubuntu, and it will load the live desktop. You can use the computer running ubuntu from the cd, even have internet access usually and look for help here for example. That's a great difference compared to windows which you can't run in live mode. DO NOT reinstall right away if you don't know what happened.

Just my humble opinion.

---

### Post by presence1960 on 2010-01-26
Do not boot into Ubuntu if you want to try to recover your files etc. Use the Live CD for now. test disk may be able to recover your stuff, but I personally have never had to use it. If meierfra is around he knows how to use testdisk.

---

### Post by ixAndyix on 2010-01-26
I can't seem to get testdisk to work.. but I have another idea. Couldn't I just plug my hard-drive into a different computer and use software to recover the window 7 files?

---

### Post by darkod on 2010-01-26
> **ixAndyix said:**
> I can't seem to get testdisk to work.. but I have another idea. Couldn't I just plug my hard-drive into a different computer and use software to recover the window 7 files?

You could. Just be careful which software you use because you don't have any backup of the data. Otherwise, a recovery software would usually scan all disks and offer to restore data if it finds it.

---

### Post by meierfra. on 2010-01-26
> ```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *  1,933,519,140 1,953,520,064    20,000,925  83 Linux
/dev/sda2       1,933,117,515 1,933,519,139       401,625   5 Extended
/dev/sda5       1,933,133,580 1,933,519,139       385,560  82 Linux swap / Solaris
```

You have roughly 860 GB of unallocated  space on your hard drive.  So if you are lucky only you partition table is messed up, and you should be able to recover your Windows partition with testdisk.  So try this:

Boot from the Ubuntu Live CD.You will have to enable the universe repository: 
System->Administration->Software Sources
Check the box in the Universe line
close
Reload

Then open a terminal and type:

```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```
After starting testdisk with the above command, choose

"Proceed",
"Intel",
"Analyze",
"Quick search",
Press  "Y" (if  asked if you have any partition created by Vista)
   This will give the  list of partitions testdisk was able to find via   the "Quick Search".  But its best to run the "Deeper Search". So:
Press "Enter" to continue,
select "Deeper Search" ( which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let us know exactly which partitions give you a directory listing.

Once you posted that "Deep Search" screen, we will be able to give you further advice.

---

### Post by ixAndyix on 2010-01-26
Ok, I tried putting my harddrive into a different computer, but it wouldn't even recognize it, so I'm back here. I'll try the testdisk method now.

---

### Post by darkod on 2010-01-26
> **ixAndyix said:**
> Ok, I tried putting my harddrive into a different computer, but it wouldn't even recognize it, so I'm back here. I'll try the testdisk method now.

After you open that window, the first tab should be selected by default, and in my case it's the second choice, the second checkbox:

Community supported..... (universe)

---

### Post by ixAndyix on 2010-01-26
Ok.. now the live CD isn't working.. I press "try without making changes" and it comes up with the ubuntu loading screen, then just goes black : / Can I do this without using the Live CD? Or will I have to burn a new copy?

---

### Post by meierfra. on 2010-01-26
> Or will I have to burn a new copy?
That would be best. Logging into your Ubuntu partition, decreases your chance to recover your Windows partition.

---

### Post by llawwehttam on 2010-01-26
Erm if you have a licence key then [http://www.mydigitallife.info/2009/11/10/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/  ]("http://www.mydigitallife.info/2009/11/10/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/")

I think its legal.

---

### Post by ixAndyix on 2010-01-26
Ok, I'll burn a new disc.

As for the ISO, I want Windows Ultimate to be honest - and I don't have a product key. :(

---

### Post by Grenage on 2010-01-26
You _really_ should have a key, if not then talk to your supplier.

---

### Post by ixAndyix on 2010-01-26
> **Grenage said:**
> You _really_ should have a key, if not then talk to your supplier.

I had my machine custom built, and the guys who built it didn't give me a product key or disc : /

I'm just running a deep search with testdisk at the moment.

---

### Post by presence1960 on 2010-01-26
> **ixAndyix said:**
> I had my machine custom built, and the guys who built it didn't give me a product key or disc : /

I'm just running a deep search with testdisk at the moment.

They should have given you a disk most likely an OEM version of windows & a genuine windows sticker of authenticity (see pic below). If they did not you should contact them. Hopefully they did not give you a pirated version of windows.

---

### Post by meierfra. on 2010-01-26
> I'm just running a deep search with testdisk at the moment.
I have noticed that the testdisk deep seach is pretty slow when one has lots of unallocated space. So with 800GB of unallocated space it could take a really long time.

---

### Post by ixAndyix on 2010-01-26
Ok, it's done. Here's some screenshots of the results.

Deep Search results:

[http://i48.tinypic.com/15ojql3.jpg](http://i48.tinypic.com/15ojql3.jpg)

The first two volumes listed showed this in the directory:

[http://i49.tinypic.com/m7e3gn.png](http://i49.tinypic.com/m7e3gn.png)


There was a folder in this volume called "Recovery", this is what it looked like when I opened it:

[http://i48.tinypic.com/bhaesz.png](http://i48.tinypic.com/bhaesz.png)


Does this mean I can recover windows and restore my files? And if so, how do I go about doing it?

Thanks a lot for everyone's help so far. I appreciate it :)

---

### Post by meierfra. on 2010-01-26
Looks good.  To write the new partition table:

1) Select the first volume and then use the "right arrow" key to turn the "D" at the beginning of the line into a "*"

2) Select the second to last volume (Linux Swap  120332) and turn the "D" into a "L".

3) Select  the  last volume (Linux 120356) and turn the  "D" into  "P"

Press "Enter" and then choose "Write". Type "Y" if  asked to confirm. Then press "q"a few times to quite testdisk.


Ubuntu will now be the third partition on the drive and you will have to reinstall Grub.  

```
sudo partprobe
sudo grub

```
and at the grub prompt:

```
root (hd0,2)
setup (hd0)
quit
```


I'm not sure whether this will work, since you just changed the partition table. If reinstalling grub fails, reboot to the Live CD and  try the last  two commands again.  If you still have problems after that, run the boot info script again and post the new "RESULTS.txt"

You also need to add Windows to the grub menu, but we will worry about that later.

---

### Post by meierfra. on 2010-01-26
Once you rewrote the partition table and successfully  booted into Ubuntu, you have to add  Windows to the Grub menu. Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Add the following to the very end of the file: (after the line
### END DEBIAN AUTOMAGIC KERNELS LIST)


title Windows 7
root (hd0,0)
chainloader +1

Save the file, reboot and see whether you can boot into Window 7.


Edit:  I forgot that you  do not want to keep Ubuntu. But since  I'm not sure 100% sure that you will be able to boot into Window 7 until  further fixing,  this probably  still is  the best course  of action.  Once you are able to boot into both OS's, we can show  how to remove Ubuntu safely.

---

### Post by Codykru on 2010-01-26
i had grub error 22 after uninstalling ubuntu also, 

i had to use the windows xp install disk and restore the original boot manager,

i'm not sure if windows 7 has the same option though..

hmph.

---

### Post by garvinrick4 on 2010-01-26
When you get Windows 7 you can make an image of  on 3 DVD's and all the recovery disks
you want just 1 DVD for recovery. You get one chance to make the image of Windows 7 which
is your installation disks. And the Recovery partition in 7 is an image of the original installation.
They are gone. The people who installed your system most likely have a set of the disks!!! Hope you get it worked out. But who ever put together that system should have given you your disks.

---

### Post by rpaskudniak on 2010-01-27
Some sage advice from one who has made the same mistakes...](*,)

My own experiences with messed up booting, from which others in this forum have helped me a great deal:

I still have a dinosaur system (Dell XPS-T500) running XP.  After a few knots in the head, before my finally successful Ubuntu installation, here is my after-the-disaster preventative advice:

[LIST=1]
[*]Do not resize and otherwise manipulate your partitions during the install process; this is error-prone under the pressure of getting on with the install.  Rather, first download and burn the [_gparted-live CD_]("http://sourceforge.net/projects/gparted/files/gparted/gparted-0.5.1/").  Boot from that to see about resizing your NTFS partitions to make room for the Ubuntu partitions.
[*]Download and burn Adrian Raulete's [_SuperGrub CD_]("http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml"). When some of my installations failed, I booted this CD and one of the options repaired my Windows MBR.  This worked for my XP stuff; I await enlightenment from others in this forum (or from Adrian) as to if this works for Windows-7.  I certainly hope so because I plan to purchase a Windows-7 box and install Ubuntu on that for dual booting.
[*]Download and burn the [_Linux System Rescue CD_]("http://www.sysresccd.org/Main_Page").  Lots of great stuff here, including a partition editor and MBR restoration.  It is, in fact, a bootable Linux CD with a specialized task.
[/LIST]

And, of course, back up your data, as well as keeping a record of all your license keys.:guitar:

This does not help ixAndyix at this stage of the game. :-({|= But, Andy, should you manage to get your Windows-7 back, please prepare yourself with all of the above before you try installing Ubuntu again.

---

### Post by ixAndyix on 2010-01-27
Ok, the second last one "linux swap" doesn't have the option L : / What should I do?

---

### Post by meierfra. on 2010-01-27
try "P" instead.

---

### Post by meierfra. on 2010-01-27
If "P" does not work, leave it at "D". But then you have to use

```
root (hd0,1)
setup (hd0)
quit
```

to reinstall grub.

---

### Post by ixAndyix on 2010-01-27
Ok, I changed  the letters for the partitions, then I tried to do sudo partprobe and I got this:

[http://i47.tinypic.com/2vab513.png](http://i47.tinypic.com/2vab513.png)


- By the way, I couldn't get my live CD to work (I tried to burn a new copy, but I had the same problem), so I did it all from the normal install, is that ok?

---

### Post by meierfra. on 2010-01-27
> Ok, I changed the letters for the partitions, then I tried to do sudo partprobe and I got this:

I was worried about that.  You will have to reboot. But after the partition table change you won't be able to boot into Ubuntu anymore. 
And since your LiveCD is not working, you have a little bit of a problem.

But lets hope for the best and see whether your are able to boot directly into Windows:

```
sudo apt-get install lilo
```
ignore the message you get, just press enter.
Then

```
sudo lilo -M /dev/sda mbr
```

This install a Windows type MBR and on reboot you should boot directly into Windows.

---

### Post by ixAndyix on 2010-01-27
Oh! wait a second, I left the terminal open and when I got back I had this up instead:

[http://i50.tinypic.com/qzgkeb.png](http://i50.tinypic.com/qzgkeb.png)

What should I do from here?
 Thanks a lot

---

### Post by meierfra. on 2010-01-27
Since "partprobe" did not work, reinstalling grub probably won't work either. So follow the instruction  from post 35.

---

### Post by ixAndyix on 2010-01-27
Ok, I can now boot up in Windows. Thank you very very much for your help, you've saved me a lot of money. The only problem I have now is that in the corner of my screen it's suddenly saying "This copy of windows is not genuine"? It never said that before - can it be fixed without a product key? If not I'll have to call the person I bought the machine off : /

---

### Post by meierfra. on 2010-01-27
> "This copy of windows is not genuine"?
This can happen when you resize or move the  Windows partition.

> can it be fixed without a product key? 

No idea. 


> I can now boot up in Windows. 
Great.  I assume  you did   "lilo -M /dev/sda mbr" and  are booting directly into Windows? Then you can now delete  the Ubuntu partition, without effecting the booting.

---

### Post by ixAndyix on 2010-01-28
Ok, it's all sorted now. As for the notice about windows not being genuine, I called the guy I bought the machine off and he's going to have a look at it. Thanks a lot for all your help, it's saved me a lot of time and money.

---

### Post by presence1960 on 2010-01-28
> **ixAndyix said:**
> Ok, it's all sorted now. As for the notice about windows not being genuine, I called the guy I bought the machine off and he's going to have a look at it. Thanks a lot for all your help, it's saved me a lot of time and money.

Make sure you get recovery disk(s) or a windows installation disk & a Genuine Windows sticker of Authenticity like I attached to an earlier post of mine. If he can't produce these for you it is probably not genuine windows or he used someone else's disk and product key to install your windows. You need a genuine windows disk or recovery disk. Insist on the sticker also!

---

