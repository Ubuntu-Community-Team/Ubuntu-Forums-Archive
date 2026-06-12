---
title: "Grub 1.5 error 2 after installing 7.10"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by jbhome on 2007-12-26
I booted the 7.1 CD as OEM and installed Ubunt 7.1 without incident. I had removed the internal hard drive for safey. My system has two ATA CD/DVD drives in addition to the external USB driver at this point.
When I booted, I removed the CD. The system started to boot to the external USB drive prompting Grub 1.5.
Then reported Error 2.
I keep reading the issue of letter changes from the CD boot to HD boot. I tried to follow instructions on correcting the boot/root information with Grub, but the same situation exists when I try to recover. I have to boot from the CD and this seems to change the drive configuration.
To start, is there anything within Grub that would let me see what the external driver is configured as?
Any suggestions  on how to fix this.
It seems this is a growing problem.
One solution has one putting Grub on the internal drive but the whole point for me is to make this a standalone install, needing only the USB drive to boot, this leaving the host system untouched.
Any suggestions woudl be greatlfully appreciated.

Sincerely,
Jim Brooks

---

### Post by meierfra on 2007-12-26
Boot into ubuntu, open a terminal  (Applications->Accesories>Terminal) and post the output of

```
sudo  fdisk -l
```

```
cat /boot/grub/menu.lst
```

```
sudo grub
```

and at the "grub>"  prompt

```
find /boot/grub/menu.lst
```

---

### Post by drogers on 2007-12-27
I too have the same problem.

So I just boot in via the live cd and follow meierfra's steps?

---

### Post by meierfra on 2007-12-27
> So I just boot in via the live cd and follow meierfra's steps?

Those commands are are supposed to be typed  in ubuntu (not in the ubuntu LIve CD). Are you able to get in ubuntu somehow? 

If not, then boot from the Live CD. Do the same commands, but skip the "cat /boot/grub/menu.lst" (since it won't work)

 Those command won't fix your problem. But  if you give me that information I might be able to figure out what is going on and tell you how to fix the problem.

---

### Post by drogers on 2007-12-27
Instead of doing all of that, can I just reinstall the OS onto the external and edit the boot loader part so that instead of the *Device for boot loader installation* being **(hd0)** can I change it to **(sdb)** since that's what my external is registering as? Shouldn't it then just rest on the external rather than wherever it does normally?
Won't that make it so that when I'm booting and I have my external in, the grub will show up since the priority is to boot from USB?

---

### Post by meierfra on 2007-12-27
That should work. But  use  "/dev/sdb" in the advanced tab, not "(sdb)".  Also there is some chance that Ubuntu  will generate the wrong "menu.lst".
I'll write up instruction, how to do the same thing without having to reinstall (see next post)

---

### Post by meierfra on 2007-12-27
drogers:  This will install grub to "sdb". It assumes that  Ubuntu is on the first partition of sdb (if it is for example on the second, you would have to replace (hd0,0)  by (hd0,1), sdb1 by sdb2 and so on)

Boot from the LiveCD

Step 1: Edit menu.lst

```

mkdir ubuntu 
sudo mount -t ext3 /dev/sdb1 ubuntu
gksudo gedit ubuntu/boot/grub/menu.lst

```

Change #groot (hd1,0)" to "#groot (hd0,0)"

Change  all "root (hd1,0)" in the titles section to "root (hd0,0)" (there are three  of them)


You also need to edit the windows item, but you can do that later (ask for help if you need  it)

Save the file

Step 2 Install grub to the MBR  of sdb:

```
sudo grub
```

and at the "grub>" prompt

```
root (hd1,0)
setup (hd1)
quit
```

Step 3 Reboot from your external drive

---

### Post by jbhome on 2007-12-27
Thanks for the responses.
I have done most of the first set of instructions, and the values match what's in menu.lst
The frustrating part is I did find a set of instructions, using the text installer, that allowed me to boot from the drive.
It would be nice if Grub would present a list of drives, with the option to choose the correct one.
Booting and running from the CD confuses the system.
Urgh.

I will boot from the CD and post the results just for reference.

Sincerely,
Jim

---

### Post by dstickst on 2007-12-27
I have sort of the same issue. I just installed Gutsy on a USB flash drive with no problems. Since then, two things have happened.

1. I wanted to be able to boot into Windows without having the flash drive in all the time.
2. I added a second SATA hdd.

Now, when I boot with or without the flash drive, I get a GRUB 1.5 error. What I would like to do is just get the boot menu regardless of whether I have the flash drive in or not. As an aside, I would also like to discontinue use of my USB Ubuntu installation and re-install it on a partition I set aside on my new SATA hdd.

So I guess my question is (sorry if this has been a tad convoluted): if I remove the flash drive, boot from the live CD, and install Gutsy on my hdd partition, will that get rid of the GRUB error?

---

### Post by meierfra on 2007-12-27
> So I guess my question is (sorry if this has been a tad convoluted): if I remove the flash drive, boot from the live CD, and install Gutsy on my hdd partition, will that get rid of the GRUB error?

Yes, almost certainly.

(You can also achieve 1. without reinstalling ubuntu. But as long as you want to install ubuntu on the SATA drive anyway, that's the way to go)

---

### Post by jbhome on 2007-12-27
Funny you should mention that.
That is exactly what I was trying to do, without putting grub on my original internal drive.
Seemed like a good idea at the time.
I'm in upgrade mode right now. two kids, more memory, p/s etc so soon I will try the previous suggestion.
I did try similar directions but...
Hd0,1 was the only device Grub was happy with when booting from the Ubuntu live CD and this matched the drives identified with fdisk.
Seems though that this changes when you remove the cd from the drive and boot from the USB hard drive.
Sort of cat and mouse.
Oh well, it is Christmas time and I have some free time to what the heck.

Thanks for all the help everyone.

Jim

---

### Post by meierfra on 2007-12-27
jbhome: I'm confused, Did you solve your problem or are you still looking for help. If you want my to help,  I need the information requested in my first post.  

Also I don't think that your case  and  dstickst's are related.

---

### Post by jbhome on 2007-12-27
Sorry, got sidetracked.

Here are the results of the tests you suggested.
Thanks for the help.
Jim is my name by the way.

*****************
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         611       24321   190458607+   7  HPFS/NTFS
/dev/sda2               1         610     4899793+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d5f32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30225   242782281   83  Linux
/dev/sdb2           30226       30401     1413720    5  Extended
/dev/sdb5           30226       30401     1413688+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

*****************
Cat menu.lst step result
*****************
ubuntu@ubuntu:~$ cat ubuntu/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=024c023c-a7a7-4b29-9346-14ac709193e2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=024c023c-a7a7-4b29-9346-14ac709193e2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=024c023c-a7a7-4b29-9346-14ac709193e2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ 

*****************
Grub find test result
*****************
grub> find /boot/grub/menu.lst
 (hd1,0)

grub> 

grub> 

*****************

---

### Post by meierfra on 2007-12-27
jbhome: The method in post 7 should work for you. (with exactly those numbers)

When you reboot, make sure that the boot order in the bios is

External Drive
Internal Drive
CD Drive 1
CD Drive 2

---

### Post by dstickst on 2007-12-27
Thanks, I'll go ahead and install on that partition then.

---

### Post by jbhome on 2007-12-27
My bios is funky.
It allows me to select hard drive or cdrom to boot from.
Further, it lets me select internal or external as the hard drive.
I am able to start the grub boot (Grub 1.5 text) but grub seems to loose it when it has to find the image to boot.
This is why I mention, and have seen commented on, the fact the drive numbers change from when I boot from the live CD vs booting from the Ubuntu on the hard drive.

Thanks,
Jim

---

### Post by meierfra on 2007-12-27
> am able to start the grub boot (Grub 1.5 text) but grub seems to loose it when it has to find the image to boot.

jbhome:  I believe the method in  post 7 will  solve your problem.

---

### Post by jbhome on 2007-12-28
I'm baaack.

Same results. No change.
Set drive to hd0 from hd1.
Grub Stage 1.5
Grub booting wait...
Error 2

Jim

---

### Post by meierfra on 2007-12-28
I was sure it would work. I just don't see how it could fail.

Did you had any error messages during 
root (hd1,0)
setup (hd1)


Change  "hiddenmenu" to "#hiddenmenu" and "timeout 3" to "timeout 10"
I want to see whether the "grub menu" appears during boot-up, when you boot from the external drive.

If it easier for you, you  can edit menu.lst from ubuntu rather than the LiveCD. To open menu.lst in Ubuntu just type "gksudo gedit /boot/grub/menu.lst".

Can you describe in more details how and under what circumstances you are able to boot into Ubuntu? 
Could you repeat the instructions from my first post but from Ubuntu rather than  the LiveCD (of course you won't have to mount the ubuntu partition)

---

### Post by jbhome on 2007-12-28
I'll give that a try.
The last time I got things to work, using the 6.x install not live cd, I found instructions from Dave (DaBruGo) Jun 21st, 2007.
THe article was in the Installation and Upgrades directory and titled ...
SUCCESS - Breezy loaded on external USB drive!
Perhaps part of the problem is missing USB drivers????
In the article, I had to rebuild the the ramfs.
I'll let you know how I make out.
Sure would be nice if there was a debug mode with Grub to let us know what it sees. This boot, edit, rebot, test, .... gets kind of old.

Thanks for you help, attention and patience. It is very much appreciated.

Jim

---

### Post by meierfra on 2007-12-28
I'm confused. I somehow thought  the whole time you have  a way to  boot into ubuntu (the real ubuntu on your external drive, not the LiveCD). Is that wrong? 

If  that is wrong you don't need to  repeat the instructions from my  first post.

---

### Post by jbhome on 2007-12-28
Sorry to be confusing. Guess it's my middle name...
I was able to boot into Ubuntu 6x on the external USB drive.
More recently, I wanted to upgrade to 7.1 and decided to try the install procedure as shown on the Ubuntu forums.
To quote a phrase the operation/install was a success but the patient died, the system boot fails.
That is where I/we are at currently.

Jim

---

### Post by meierfra on 2007-12-28
O.K.  That changes the picture. Looking back at your post I don't even understand why I thought you can boot into Ubuntu.  I guess I just tried to turn this into a grub problem (since that's my area of expertise).  But if it would be  a Grub problem then the  method in Post 7 would have solved it.

So just forget about my last set of instructions.I'm sure they won't  lead to anything.

Sorry for wasting your time and good luck with solving  your problem.

---

### Post by jbhome on 2007-12-28
Where does this leave me?
Do you think the problem is Ubuntu missing the USB drivers needed to access the drive?

Thanks,
Jim

---

### Post by pietjanjaap on 2007-12-28
If you get a grub error then your grub is working.
(if you want to reinstall grub then use supergrub)

Then you should change the menu.lsi file.
This is mine:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

From this you make copies in the menu.lst, but change the harddisk, hd,0,0 then hd0,1 etc.
Example:
**(only make more copies of your first entry)**
title		Ubuntu, kernel 2.6.20-16-generic
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
**(same as above but only change drive number)**
title		Ubuntu, kernel 2.6.20-16-generic
root		**(hd0,1)**
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
**(do this for more drives if you want)**



So you have now all your harddisk in more then 1 ubuntu, now you startup and you see you have a lot of ubuntu's.
find the one that works, and change everything to that  wat works.

---

### Post by meierfra on 2007-12-28
> Do you think the problem is Ubuntu missing the USB drivers needed to access the drive?

Could  be. But I really have no idea.

---

### Post by meierfra on 2007-12-28
> If you get a grub error then your grub is working.

No. It only says that grub is installed in the MBR. You can even erase all the partitions on a hard drive and still get an Grub error.

---

### Post by meierfra on 2007-12-28
You could  try using lilo instead of grub.

Or  if you are willing to give up on the standalone idea, then you can  create a separate boot partition on the internal drive. That would almost certainly work.

---

### Post by jbhome on 2007-12-28
I guess I have time and since the better direction is to figure how to make this automatic, I think staying with Grub and figuring out what's going wrong would be better.
My understanding is this.
Grub is loading from the MBR of the external USB drive as I started with the internal Sata drive disconnected.
Grub is executing as I see the Grub Stage 1.5 message.
I understand the Error 2 message means grub can't find the root partition where the initrd image is stored.
Is this correct?
Grub I'm assuming is using the BIOS to access the drive, the same BIOS that found the drive and loaded Grub from the MBR.
Is this correct?
Is there a way like a recent post that will allow me to try several drive numbers to try and locate the correct one?
Currently there are three choices but I never see a menu displayed.

Jim

---

### Post by pietjanjaap on 2007-12-28
Check my post above , there you can check all the drives.

---

### Post by meierfra on 2007-12-28
If you really still want to    try to configure grub, then change "hiddenmenu" to "#hiddenmenu" and "timeout 3" to "timeout 10", to see whether the grub menu appears. 


If  grub menu does not appear, it means that grub cannot find  "menu.lst". In particular you can edit menu.lst as much as you want, it will not make a difference.

---

### Post by meierfra on 2007-12-28
The setting from my post 7 are correct.  There is no absolutely no doubt in my mind  about that.

But you  could carry out the instructions from post 7 again. Maybe you had  a typo. Post  your menu.lst after you edited it so that I can check for typos. Post the the content of the terminal after "setup (hd1)"  so that  I can see that the grub install went  o.k.

I did some googeling to find somebody with a similar problem. I found this 

[http://kubuntuforums.net/forums/index.php?topic=3082032.0]("http://kubuntuforums.net/forums/index.php?topic=3082032.0")

A quote from one of the last posts in that thread:

> I changed my BIOS from having it look first at my USB hard drive then my IDE hard drive, to the opposite of that.  Then I went into the boot menu and told it to boot from the USB drive.  That brought up the GRUB menu and I was able to log in from there.

You might not be able to do the same in in your bios. But  I suggest to check  on the various setting in your bios, play around a little bit and see whether it makes a difference.

---

### Post by jbhome on 2007-12-30
Well... I have some updates.
1 - I booted as user not OEM and installed and magically I was able to boot.
2 - I plugged in my internal drive, checked the BIOS and found I could choose three devices, the CDrom, internal, and USB drives.
3 - The BIOS on restart, then reverted either or, USB or internal and while Grub runs, presenting a menu, it' cant find a drive to boot from. Ergg!
 
1 - So it seems either the install, or I messed up the Grub image.
2 - My Bios is not working properly detecting and assigning drive numbers/names.
3 - The USB drivers are available in the generic boot image for 7.1

I'll try to do some more probing tonite.

Thanks for everyones help.

Sincerely,
Jim

---

