---
title: "Triple boot"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by dakkar9999 on 2008-10-31
Ok, I have windows XP and Ubuntu 8.04 installed through wubi that resides on my first disk.  I now have installed Ubuntu 8.10 through CD ISO onto another disk (slave 10gig).  But the Grub that was written by 8.10 does not work properly.  My boot grub still only shows XP and one instance of Ubuntu, which is version 8.4.  The new install (on a separate HD) is not listed.

How can I add it?  I know it's just a matter of adding a few lines to the grub.

Thanks!

---

### Post by caljohnsmith on 2008-10-31
In Windows, look at the following file if you have it:
```
C:\ubuntu\disks\boot\grub\menu.lst
```
I think that is where Wubi has its menu.lst, and you could add the 8.10 Intrepid to that menu.lst. You could use an entry like:
```
title Intrepid Grub Menu
configfile (hd1,0)/boot/grub/menu.lst
```
That will link to your menu.lst on the Intrepid drive, assuming the Intrepid drive is second in the boot order and Intrepid is on the first partition. If you would like more specific help, then please boot your Live CD, open a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by dakkar9999 on 2008-10-31
Yes, I found the menu.lst as you mentioned.  I just have no idea where to paste the lines you mention.

Here's what I have in that menu.lst file.

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
# kopt=root=UUID=2E64E2ED64E2B72D loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2E64E2ED64E2B72D loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2E64E2ED64E2B72D loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Thanks!

---

### Post by caljohnsmith on 2008-11-01
If you can boot your Live CD, how about opening a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
Please post the output of that and we can work from there.

---

### Post by dakkar9999 on 2008-11-01
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98542502

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   398283479   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10271026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   163846934    81923436    7  HPFS/NTFS
/dev/sdb2       163846935   390716864   113434965    7  HPFS/NTFS

Disk /dev/sdc: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders, total 19931184 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe00a9657

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    18988829     9494383+  83  Linux
/dev/sdc2        18988830    19920599      465885    5  Extended
/dev/sdc5        18988893    19920599      465853+  82  Linux swap / Solaris


I did it straight from Ubuntu 8.04 as it is still fully functional.  The hard drive that contains Ubuntu 8.10 installation that is not detected is installed on /dev/SDC (10.2 gig drive)

Thanks!

---

### Post by caljohnsmith on 2008-11-01
OK, I just realized there could be an issue with booting Intrepid from your Wubi Grub's menu, because unless Wubi is using a version of Grub4DOS later than about last July, you won't be able to boot the new Intrepid install; Intrepid creates partitions with the newer 256 byte inode size instead of the older 128 byte inode size that Hardy and previous versions used, and you need a Grub4DOS version more recent than the 2008-06-24 version to handle the newer 256 byte inode size partitions. 

So bottom line, can you boot from your sdc drive on start up and get the Intrepid Grub menu? If so, it would be easy to add your Windows drive to the menu. It would be easier to do that I think than install the newer Grub4DOS in Windows to boot Intrepid from Windows. Also, to clarify, is sda or sdb your Windows drive?

---

### Post by dakkar9999 on 2008-11-01
No, that's the problem.  During the install, Ubuntu says it installs Grub, but upon restart, it is the wubi grub that boot.  I don't know how to access the 8.10 install.

Also, from the menu.lst file, it list windows as follow

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

So I guess windows is on the sdb1 partition.

Thanks!

---

### Post by caljohnsmith on 2008-11-01
OK, to help clarify your setup, please post the output of the following commands: 
```
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
Also, you should mark one of your partitions on your sdc drive as bootable so that your BIOS doesn't complain that it isn't a bootable drive; to do that:
```
sudo fdisk /dev/sdc
```
Press "a", then "1", then "w" to write the changes. Next reboot, go into your BIOS (you'll need to find out which function key or other key will put you in BIOS), and change the boot order so that the sdc drive is first in the boot order. Then let me know what happens when you try and boot the sdc drive.

---

### Post by dakkar9999 on 2008-11-02
dakkar@dakkar-desktop:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
[sudo] password for dakkar: 
GRUB 
dakkar@dakkar-desktop:~$ 

and

dakkar@dakkar-desktop:~$ sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002
dakkar@dakkar-desktop:~$ 

dakkar@dakkar-desktop:~$ sudo fdisk /dev/sdc

The number of cylinders for this disk is set to 1240.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 


I didn't go any further than this because I didn't want to make any bad mistake that would crash both boot.  Just confirm that your sudo fdisk command is still appropriate and I'll go ahead and do it.

Thanks!

---

### Post by caljohnsmith on 2008-11-02
> **dakkar9999 said:**
> 
I didn't go any further than this because I didn't want to make any bad mistake that would crash both boot.  Just confirm that your sudo fdisk command is still appropriate and I'll go ahead and do it.

Thanks!
You don't need to worry about the geometry warning that fdisk gives you (at least at this point); go ahead and use fdisk to mark your sdc1 partition as bootable. It also looks like your sdc drive has Grub properly installed to it, so if you set your BIOS to boot it, you should at least get the Grub menu on start up. It might be that booting Ubuntu from the menu will give you a Grub error, but that will most likely be easy to correct. So go ahead and give it a shot, and let me know how far you get. :)

---

### Post by dakkar9999 on 2008-11-02
Well, now i was able to make drive sdc as the boot disk.  But now I get "Grub loading stage 1.5 error 2"

That appears before I get the option of choosing XP or Ubuntu.

Any suggestions?

---

### Post by caljohnsmith on 2008-11-02
According to the commands you posted in post #9, Grub appears to be correctly installed to sdc, so I think it is quite likely you could have a BIOS issue since you are getting that Grub error 2. Try going into your BIOS and look for settings related to HDDs or USB, such as "auto-detect", LBA, CHS, RAID, AHCI vs. IDE, ACPI, DMA, etc. Try changing them one at a time, reboot your USB drive, and see if anything changes. I would recommend writing down whichever settings you change so you can always revert back to the original settings if necessary. Let me know how it goes. :)

---

### Post by dakkar9999 on 2008-11-03
Yeah, no luck yet.  I've tried all the different combination of boot sequence through the Bios, to no avail.  I've also looked at the jumpers and both seem to be set at cable select.  But, the drive that should appear as master (200gig sdb1) is actually positioned as the slave on the IDE connector and it seems as if my SATA drive is considered as drive A.

Wouldn't it be   easier to just edit the Grub (wubi 8.04) wich I have access to and that is working properly, and just add an entry to point to the new 8.1 install on  sdc?

Just a thought, I'm just a noob!

Thanks!

---

### Post by caljohnsmith on 2008-11-03
OK, let's do a few sanity checks before going further; try the following command:
```
sudo dumpe2fs /dev/sdc1 | grep -i "inode size"
```
Let me know if that returns "128" or "256". Next boot your Intrepid Live CD (make sure it is Intrepid and not Hardy or earlier), and do:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
And post the output of the above commands. Go ahead and reboot, and let me know if you get anything besides the Grub error 2.

---

### Post by dakkar9999 on 2008-11-03
Ok, the first command gives me 256 (that's from the wubi 8.04 install)

Second, I did not use a live CD but the regular install CD.  I don't know how to access the terminal from that install CD.  I tried different options, but did not gain access to the terminal.

I was thinking, since the wubi install boots properly, wouldn't it be a good idea to look in it's grub for how the HD are seen, then go through the install (or repair install) from the CD.  When it's about to install it's grub, would it be possible to have it open and modify the lines telling Ubuntu about the HD order?  Sorry if I'm being confusing.

Sorry for all the trouble.

Thanks!

p.s. If it's easier, I'll download the live CD.

---

### Post by caljohnsmith on 2008-11-03
> **dakkar9999 said:**
> 
Second, I did not use a live CD but the regular install CD.  I don't know how to access the terminal from that install CD.  I tried different options, but did not gain access to the terminal.
When you boot the CD, does the first menu you see say something about "Try Ubuntu without making any changes to your computer"? That's the option you want to use. I'm not sure what you mean by regular install CD, because I think you might mean the same thing as the live CD. Do you have a link of where you donwloaded it from?
> **dakkar9999 said:**
> 
I was thinking, since the wubi install boots properly, wouldn't it be a good idea to look in it's grub for how the HD are seen, then go through the install (or repair install) from the CD.  When it's about to install it's grub, would it be possible to have it open and modify the lines telling Ubuntu about the HD order?  Sorry if I'm being confusing.

Unfortunately your problem is not just a simple problem with Grub's menu.lst, because you are getting the Grub error 2 before seeing a Grub menu. In other words, Grub can't access its boot files in the Intrepid partition, so Grub is not able to even boot. Give the Grub commands in my previous post a shot once you have a Live CD (which you may all ready), and let me know how that goes. :)

---

### Post by dakkar9999 on 2008-11-03
Nope, definately not a live CD.  I do not get the option to test the software.  It boot straight to install/repair of install.

What I downloaded was the bittorrent of version 8.1 (from the Ubuntu website)  the name is ubuntu-8.10-alternate-amd64.iso

This is not a live CD.

---

### Post by dakkar9999 on 2008-11-03
Ok, this might help.  I looked at the menu.lst from both the 8.04 install and the 8.10 install.  This should help us get the proper disk order, no?

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2E64E2ED64E2B72D loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2E64E2ED64E2B72D loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Then 8.10

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4916406e-1144-47c4-8325-8836abcc3da7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4916406e-1144-47c4-8325-8836abcc3da7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4916406e-1144-47c4-8325-8836abcc3da7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4916406e-1144-47c4-8325-8836abcc3da7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Hope this helps!

---

### Post by caljohnsmith on 2008-11-03
dakkar9999, unfortunately fixing your problem is not as simple as just adding the Intrepid install entries to your Wubi's menu.lst because of the reasons I gave in post #6. Can you download the 8.10 Live CD so we can use that for troubleshooting? If not, I think it is going to be difficult.

---

### Post by dakkar9999 on 2008-11-03
Ok, I've downloaded the live cd and ran the Ibex live.

I've put your instructions in the terminal and this is what I get.

ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sdc1 | grep -i "inode size"
dumpe2fs 1.41.3 (12-Oct-2008)
Inode size:	          256
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 


I will now try to shutdown and reboot, see what happens.

---

### Post by dakkar9999 on 2008-11-03
Well, back to square one.  I tried to install from that new live CD (which booted fine and all), but after restart, I'm back with the same Windows XP and Ubuntu 8.04 (wubi) Grub.  No trace of my new install in the Grub menu...

I'm starting to feel a lack of love on Ubuntu's part...

---

### Post by caljohnsmith on 2008-11-03
So what happened after you reinstalled Grub via your post #20? When you rebooted to your sdc drive, did you get the same Grub error 2?

---

### Post by dakkar9999 on 2008-11-03
Yes!  That did it!  The first time around, I did not follow the instruction properly.  I had entered the commands, but without changing the boot order of the drives.  Now I did it and it works!  The only quirky thing is that if I choose to boot XP, it takes me to the other grub.  But that's ok, I can live with that.  If everything goes well, I'll probably migrate in a more permanent fashion later.

How do I add a thank you to your profile?
:p

---

### Post by caljohnsmith on 2008-11-03
> **dakkar9999 said:**
> Yes!  That did it!  The first time around, I did not follow the instruction properly.  I had entered the commands, but without changing the boot order of the drives.  Now I did it and it works!  The only quirky thing is that if I choose to boot XP, it takes me to the other grub.  But that's ok, I can live with that.  If everything goes well, I'll probably migrate in a more permanent fashion later.

How do I add a thank you to your profile?
:p
If you want to fix your Windows problem, and if you have your Windows Install CD, just boot the Windows Install CD, go to the "recovery console", and run:
```
fixmbr
fixboot
```
Anyway, glad it's working for you now. About adding "thanks", you can do that by clicking on the little red medal in the lower right corner of a message. Cheers and have fun. :)

---

### Post by dakkar9999 on 2008-11-03
Thanks!  I'll hold on to the other grub for now.  I still need access to the 8.04 version for a bit.

Thanks again for your patience!

---

