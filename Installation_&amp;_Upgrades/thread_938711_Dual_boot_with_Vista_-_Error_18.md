---
title: "Dual boot with Vista - Error 18"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by cr0wn3r on 2008-10-05
I have just followed a guide here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

to install Ubuntu on to my PC to dual boot with a previous Vista installation.

The problem is that now I have installed Ubuntu I get Error 18 when booting and so can not access Vista OR Ubuntu. I can still boot from the live CD however to run Ubuntu that way.

I've done a bit of googling and all I can work out is that if the GRUB data isn't in the first 8.something Gb of the disk then it cant find it, and hence the error. Is this right? Seems odd as anyone dual booting with a previous Vista install would have a Vista installation in the hundreds of Gb which makes that tutorial linked above a guaranteed fail.

I have a fairly new PC - running a dual core AMD processor on a  recent mobo (Gigabyte GA-MA74GM-S2H 740G) with 2 gig of ram.

I guess in order of priority I would like to:
 1. Make sure my Vista install is safe and that I can run it and access my files
 2. Fix the error 18 so I can dual boot without reinstalling Vista
 3. If I have to, once I've accessed vista again to back everything up, I can reinstall but doing Ubuntu first. If that's likely to make it easier.


I've used ubuntu a bit before, but only on an old PC where it was the only OS. Putting it on my main PC to dual boot is an attempt to have it more available so I can use it more and try to get more used to it.

Thanks in advance for the help

C

---

### Post by Pumalite on 2008-10-05
Vista always prefer to be sda1 and installed first. Use Vista partitioner to allocate space for Ubuntu. Install Ubuntu in that free space going 'Manual' at the installation. You can fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Error 18:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by caljohnsmith on 2008-10-05
> **cr0wn3r said:**
> 
I've done a bit of googling and all I can work out is that if the GRUB data isn't in the first 8.something Gb of the disk then it cant find it, and hence the error. Is this right? Seems odd as anyone dual booting with a previous Vista install would have a Vista installation in the hundreds of Gb which makes that tutorial linked above a guaranteed fail.

Actually, the 8 GB rule is for really old BIOSes, the new BIOS limit that you might run into is 137 GB. So just to confirm, do you get the error 18 before even getting the Grub menu, or after you get the Grub menu and select an OS? 

To check on the state of your partitions, please post the following from your Live CD (open a terminal with applications > accessories > terminal):
```
sudo fdisk -lu
```
Also, to make sure that Grub is pointing to the correct partition for its system files, do the following from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands and we can work from there.

---

### Post by cr0wn3r on 2008-10-05
Thanks for the replies guys.

For my original install I used the partition manager in Vista to shrink the single partition by 50Gb. Then I used the Live CD to install Ubuntu on to this 50Gb space (selecting "use largest available continuous space" in the install menu as instructed by the tutorial I linked in my first post).

Following the first reply to this thread I loaded Ubuntu from the Live CD and installed it again, but making a new 500mb partition with the mount point "/boot" and using the 49.5 ish Gb partition for everything else.

This hasnt changed anything - I still get the same problem. But just thought I'd let you know what I'd done in case it made anything better / worse / different.

So to answer those questions:

I get Error 18 BEFORE I get any boot menu options.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0d24be5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   677488631   338743292    7  HPFS/NTFS
/dev/sda2       677493180   781417664    51962242+   5  Extended
/dev/sda5       677493243   775152314    48829536   83  Linux
/dev/sda6       777080178   781417664     2168743+  82  Linux swap / Solaris
/dev/sda7       775152378   777080114      963868+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1
 (hd0,6)
grub> root (hd0,6)
root (hd0,6)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 

```

---

### Post by caljohnsmith on 2008-10-05
> ```

Disk /dev/sda: [COLOR="Red"]400.0 GB[/COLOR], 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total [COLOR="Red"]781422768[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0d24be5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   677488631   338743292    7  HPFS/NTFS
/dev/sda2       677493180   781417664    51962242+   5  Extended
/dev/sda5       677493243   775152314    48829536   83  Linux
/dev/sda6       777080178   781417664     2168743+  82  Linux swap / Solaris
/dev/sda7       [COLOR="Red"]775152378[/COLOR]   777080114      963868+  83  Linux
```
According to your fdisk numbers above, your boot partition (sda7) starts at:
```
775152378/781422768 * 400 GB = 397 GB

```
That is clearly beyond the 137 GB BIOS limit, so probably your problem is that your Grub files are out of range of what BIOS can access. :) Note though that your Windows partition sda1 starts at sector 2048, so you might have enough room at the front of your drive to make a dedicated Grub partition where you could put all your Grub files. If you can create a primary partition at the beginning of your HDD, format it to ext3, I can help you set up a dedicated Grub partition if you like. 

To make that partition, boot your Live CD and when you get to the Ubuntu desktop, press ALT + F2, and type:
```
gksudo gparted
```
That will bring up Ubuntu's partition editor. Try to use that, and let me know how it goes.

---

### Post by cr0wn3r on 2008-10-05
Ok, Thanks for all the help. I think I understand now about the limit and I can see why my /boot partition didnt work.

So Ive run gparted and I can see the small unpartitioned space before the Vista partition. If I try to use that space for a new partition it says the space is only 1mb in size and wont let me make it any larger. I'm guessing this wont be enough... ?

C

---

### Post by Pumalite on 2008-10-05
Make it 200 MB

---

### Post by caljohnsmith on 2008-10-05
> **cr0wn3r said:**
> 
So Ive run gparted and I can see the small unpartitioned space before the Vista partition. If I try to use that space for a new partition it says the space is only 1mb in size and wont let me make it any larger. I'm guessing this wont be enough... ?

C
The Grub files only take a few hundred KB of space, so it might be enough *if* gparted will even let you make a partition with that space; gparted nornally has to make partitions end on a cylinder boundary I think, so you might run into problems making that partition. When you try and create the partition, you might have to uncheck the "round to cylinders" option to make it work in gparted. Give it a try and let me know how it goes.

---

### Post by Rebelli0us on 2008-10-05
Looks like your Vista partition is there, good thing.

Another approach. Run Windows CD and repair the boot sector. Then you can download & use EasyBCD (neosmart.net) to setup Windows as your boot loader. Not a Linux solution, but it will give you dual booting, same as Grub.

---

### Post by cr0wn3r on 2008-10-06
Hi Guys

I had time last night so followed both lines of attack.

gparted wouldnt let me make a new partition with that 1mb space at the begining of the disk, so no luck there. Is it safe to use the tools available in gparted to move the windows vista partition further back on the disk, to free up more space at the begining for the GRUB files partition? If not... I'm stumped again.

So next I tried EasyBCD. I made a fresh Ubuntu install from the Live CD, then fixed the Vista boot records using the Windows DVD so I could boot in to Vista. Next I installed EasyBCD and added Linux to the Entries List with type "Grub". When I reboot I get a boot menu. Vista works fine but selecting Linux just takes me to a terminal style "GRUB>" prompt.

Im not too fussed which route I use in the end as long as one will work eventually.

Thanks a lot for your help guys.

---

### Post by cr0wn3r on 2008-10-06
It may be that the GRUB> prompt is exactly what should happen, but I havent found anything to explain how to get from there to load Ubuntu.

---

### Post by caljohnsmith on 2008-10-06
> **cr0wn3r said:**
> Hi Guys

I had time last night so followed both lines of attack.

gparted wouldnt let me make a new partition with that 1mb space at the begining of the disk, so no luck there. Is it safe to use the tools available in gparted to move the windows vista partition further back on the disk, to free up more space at the begining for the GRUB files partition? If not... I'm stumped again.

So next I tried EasyBCD. I made a fresh Ubuntu install from the Live CD, then fixed the Vista boot records using the Windows DVD so I could boot in to Vista. Next I installed EasyBCD and added Linux to the Entries List with type "Grub". When I reboot I get a boot menu. Vista works fine but selecting Linux just takes me to a terminal style "GRUB>" prompt.

Im not too fussed which route I use in the end as long as one will work eventually.

Thanks a lot for your help guys.
To use EasyBCD to boot your Ubuntu, I believe you first need to have Grub installed to the boot sector of your boot partition (sda7) so that the Vista boot loader can just "chain load" the boot partition in order to boot Ubuntu. So how about giving this a try: boot up your Live CD, and do the following from a terminal in order to install Grub to the boot sector of your sda7 partition:
```
sudo grub
grub> root (hd0,6)
grub> setup (hd0,6)
grub> quit
```
Then follow the steps in the section "Adding Ubuntu to the Vista Bootloader" in the following link to add your boot partition sda7 to your Vista boot loader menu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

When using the above steps, choose to add your boot partition sda7 in EasyBCD to the boot menu instead of the Ubuntu partition sda5, since Grub will be in the boot partition. Let me know how it goes. :)

EDIT: I just realized you did a fresh install again--are the partitions still the same or did you change them? If you changed them, please post "sudo fdisk -lu" again.

---

### Post by cr0wn3r on 2008-10-06
Ok, yeah, I did change the partitions. I didnt touch Vista but I deleted the others and made just 1 for Ubuntu / and one for swap.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0d24be5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   677488631   338743292    7  HPFS/NTFS
/dev/sda2       677493180   775152314    48829567+  83  Linux
/dev/sda3       775152315   781417664     3132675   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

So Im thinking I need to

- shrink sda2 and use the space to create a new partition
- reinstall with /boot as the mount point for the new partition
- follow your instructions but replace (hd0,6) with whatever the ID is for the /boot partition.

C

---

### Post by caljohnsmith on 2008-10-06
No need to add a boot partition if you don't have it any more, just follow these steps then to install Grub to the boot sector of your Ubuntu partition sda2:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0,1)
grub> quit

```
After that, add your Ubuntu partition sda2 to your Vista boot menu via that link I gave in my last post. Let me know how it goes.

---

### Post by cr0wn3r on 2008-10-06
Okie dokie.

I ran those commands after booting the live CD, then followed the instructions Re: Adding Ubuntu to the Vista Bootloader

I tried with and without the tick the box saying "GRUB isnt installed to the boot sector".

In both cases Ubuntu appeared in the boot menu but just took me to a GRUB> prompt.

C

---

### Post by cr0wn3r on 2008-10-06
I dont know if this helps, but typing ```
root (hd0,1)
``` at this point returns ```
Error 20: Selected cylinder exceeds maximum supported by BIOS
```

Is this a similar problem to the Error 18 caused by the grub files not being close enough to the begining of the disk?

Thanks again for all your help.

C

---

### Post by cr0wn3r on 2008-10-06
This was the result when I ran those commands using the live CD

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0,1)
setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2008-10-06
OK, try again using EasyBCD to add Ubuntu to Vista's boot menu, and be sure to use the option to specify that Grub is installed to the boot sector. Let me know exactly what happens on start up when you choose Ubuntu after you do that.

---

### Post by cr0wn3r on 2008-10-06
Ok. I deleted the Ubuntu entry from EasyBCD and created a new one with the check box set to indicate that Grub is installed to the boot sector.

Vista and Ubuntu are the two options in the boot menu.

I select Ubuntu and, as before, it takes me straight to a grub> prompt:

```
[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command 
completions. Anywhere else TAB lists the possible
completions of device/filename. ]

grub>

```

---

### Post by caljohnsmith on 2008-10-06
OK, from the Live CD do:
```
sudo mount /dev/sda2 /mnt
cat /mnt/boot/grub/menu.lst
```
And post the output please.

---

### Post by cr0wn3r on 2008-10-06
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=f727ec70-6f64-4602-8f44-c4cc899b22fa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f727ec70-6f64-4602-8f44-c4cc899b22fa ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f727ec70-6f64-4602-8f44-c4cc899b22fa ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

ubuntu@ubuntu:~$ 

```

---

### Post by caljohnsmith on 2008-10-06
OK, it looks like you are going to have to put a partition at the front of your drive for Grub, but as one last check, when you try and boot into Ubuntu and get the Grub prompt, do:
```
grub> cat (hd0,1)/boot/grub/menu.lst
```
If that returns an error, then I think you definitely need to make a partition at the beginning of your drive for Grub at this point. 

So if that is the case, boot back into Vista, and use Vista's Disk Management to shrink Vista from the beginning of its partition to create space for a new partition; you need to shrink Vista's partition enough to make either a really small ~10 MB partition just for Grub, or you can create a larger ~200 MB partition and use that as your /boot partition, similar to what you did before (it's up to you). But once you free up space at the beginning of your drive using Vista's Disk Management (don't use gparted for this), then you can boot your Live CD and use gparted to create an ext3 primary partition with the unused space. Let me know when you get that far, or if you run into problems, and we can work from there.

---

### Post by cr0wn3r on 2008-10-06
Yeah - typing that in I get

```

grub> cat (hd0,1)/boot/grub/menu.lst

Error 18: Selected cylinder exceeds maximum supported by BIOS

grub>

```

So I'll do as you say and create a new partition in front of Vista for /boot.

I'll let you know how it goes.

Thanks

C

---

### Post by cr0wn3r on 2008-10-06
Ok, well it seems that there is no way in Vistas Partition manager to create new space before the current partition.

If I shrink the partition I can free 200mb of space but it will always be made available at the end of the partition, not at the front, and there is no option to change this.

Is that the end of the road then? I guess if theres nothing else to try then I'm going to need to reinstall Vista but create the 200mb partition at the front of the disk before I do.

C

---

### Post by cr0wn3r on 2008-10-06
[This]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") seems to suggest that it's ok to use gparted to move the windows partion... I guess if I've got to reinstall anyway, then once Ive backed everything up it cant hurt to try.

---

### Post by caljohnsmith on 2008-10-06
> **cr0wn3r said:**
> [This]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") seems to suggest that it's ok to use gparted to move the windows partion... I guess if I've got to reinstall anyway, then once Ive backed everything up it cant hurt to try.
Yes, like that link you gave shows, if you use gparted to resize Vista, it usually temporarily breaks Vista until you use a Vista Recovery CD to fix Vista again. The reason is because Vista (unlike any other OS I know of) maintains its own HDD partition table outside of the main one in the HDD's MBR (Master Boot Record); so if you use something like gparted to repartition, it updates the MBR with the new partition table but gparted knows nothing about Vista's own partition table. That then usually makes Vista unbootable until you can fix Vista's partition table with a Vista Recovery CD. 

So since you have nothing to lose, my vote is definitely go for it--use gparted to resize your Vista and we can work from there. :)

---

### Post by cr0wn3r on 2008-10-07
Well it took all night, but the partition move has worked and Vistas repaired itself.

So in this order ive got
- 200mb unallocated
- then vistas partition
- 50Gb unallocated 

Should I continue with this now using EasyBCD, or go back to the original method?

---

### Post by cr0wn3r on 2008-10-07
WOOHOOO!!

We're finally there.

After moving the Vista partition and getting that fixed, I booted from the Live CD and reinstalled Ubuntu, setting the first 200mb on the disk as /boot and the 50gb after the vista install as / and then swap. I let Ubuntu do its own thing with the boot loader.

Then .... it worked.

Ive now got the boot menu with the Ubuntu options and Vista, and everythings working.

Thanks to all the guys that helped - especially caljohnsmith. Much much appreciation.

C

---

### Post by caljohnsmith on 2008-10-07
That's great news its finally working, and I'm glad I could help out. It's also great that you were able to fix Vista after shrinking its partition without having to resort to a reinstall. Cheers and have fun. :)

---

### Post by Rebelli0us on 2008-10-08
Congrats. I'm also getting the hanging GRUB screen on dual boot, but my dual-boot OSes are on different disks. And I've no idea how to fix it:



[http://ubuntuforums.org/showthread.php?t=886762](http://ubuntuforums.org/showthread.php?t=886762)



...

---

