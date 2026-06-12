---
title: "Can no longer load XP after Ubuntu install."
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Scotty B on 2008-11-14
Here's the whole story:

I have an old XP computer with two hard drives. I wasn't really using the second hard drive and so decided to try out Ubuntu. 
A couple of months ago, I formatted my second drive and, using ~1/2 the drive, installed Ubuntu 8.04. Everything was fine and I could load Ubuntu or XP at startup.
About a month later, I tried to run Ubuntu, but I couldn't remember my username/password to log on. So, I decided to wait for 8.10 to be released and I would reinstall Ubuntu then.
At that point, I put my 8.04 disc in and reinstalled Ubuntu (figuring I could upgrade to 8.10 later). There were no real problems (although I did the manual partition/install, rather than the automatic) and once installed, I managed to upgrade to 8.10. I've been using 8.10 and I like it a lot, but this evening, I wanted to run XP again.
I restarted my computer and at the GRUB loader, selected XP. At this point, the screen said:

> Starting up...
GRUB _

And it would go no further.

Does anybody know what the problem may be or have an easy fix for this? Would it work to uninstall Ubuntu? Or can I even do that? Is it a problem with the GRUB loader? Or perhaps with my manual install of Ubuntu? Maybe even an issue with 8.10?

I'm not sure really where I should even start, and any help that can be offered would be appreciated.

Thanks so much,
Scotty B

p.s. Almost forgot: I did have one error while upgrading to 8.10:
> Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0

---

### Post by littlebat on 2008-11-14
post your /boot/grub/menu.lst here.
If you can boot your Ubuntu 8.10 with grub, it should can boot your Windows XP too.
Mount your Windows XP partition, check if your Windows xp partition be destroyed when you make partitions for Ubuntu with some mistake.

---

### Post by caljohnsmith on 2008-11-15
Uninstalling Ubuntu is probably not a good idea at this point, because we don't know yet whether Grub is in the MBR (Master Boot Record) of your Windows drive; if it is, you unfortunately won't be able to boot Windows for sure if you uninstall Ubuntu. How about opening a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". Lastly, please post:
```
cat /boot/grub/menu.lst
```
And we can work from there if you want. :)

---

### Post by Scotty B on 2008-11-16
sudo fdisk -lu:
> Disk /dev/sda: 30.0 GB, 30020272128 bytes
240 heads, 63 sectors/track, 3877 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52904879    26452408+   c  W95 FAT32 (LBA)
/dev/sda2        52904880    58620239     2857680    f  W95 Ext'd (LBA)
/dev/sda5        52904943    58620239     2857648+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4880b011

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1        81963630   160071659    39054015   83  Linux
/dev/sdb2        72196110    81963629     4883760   82  Linux swap / Solaris

Partition table entries are not in disk order

sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system":
> GRUB 

sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system":
> (nothing)

sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}':
> 8100

cat /boot/grub/menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=3c8dcbfb-80b6-4fbc-a2fb-27a4eb364d10 ro

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3c8dcbfb-80b6-4fbc-a2fb-27a4eb364d10 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3c8dcbfb-80b6-4fbc-a2fb-27a4eb364d10 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3c8dcbfb-80b6-4fbc-a2fb-27a4eb364d10 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3c8dcbfb-80b6-4fbc-a2fb-27a4eb364d10 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


:)

---

### Post by caljohnsmith on 2008-11-16
OK, I think I see the problem; it sounds like Grub was accidentally installed to the boot sector of your Windows partition at some point. To correct it, you'll need to boot your Windows Install CD, go to the "recovery console", and do:
```
fixboot
```
If you don't have a Windows Install CD, let me know, and I can instead give you directions for using "testdisk" in Ubuntu to accomplish the same thing.

---

### Post by Scotty B on 2008-11-20
Sorry for the delay. I've been busy and had to find my cd.

I did what you said with the fixboot and it said that it worked, but the next time I tried to load XP from GRUB, I got this:

> [ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename ]
grub> _

and couldn't load XP.

---

### Post by caljohnsmith on 2008-11-20
Since you have two FAT32 partitions, it might be that fixboot ran on the wrong partition. How about trying again, but this time first run:
```
map
```
That should show the drive letters of your two FAT32 partitions, and use the one that is for the Windows partition:
```
fixboot C:
```
Or change the C to D if Windows is considered to be on the D partition (I don't think it should be though). After that reboot, try Windows from the Grub menu again, and if you still get dumped into the Grub command line, then from your Live CD do:
```
sudo dd if=/dev/sda1 count=1 | gzip -c > ~/Desktop/sda1.gz
```
And please attach the small "sda1.gz" file that's on your desktop to your next post so I can take a look at it. Let me know how it goes. :)

---

### Post by Scotty B on 2008-11-24
Hello again,

I tried the fixboot again, but to no avail.

I'm afraid I didn't know what you meant by running that code from my "Live CD," so I ran it from my Terminal application in Ubuntu and have attached the "sda1.gz" file. I hope that'll work. :(

---

### Post by caljohnsmith on 2008-11-24
OK, just to summarize and let you know what I think is going on so far:
[LIST]
[*]Grub is in the MBR of your Windows sda drive as revealed by the "dd" commands you previously ran, and it points correctly to your sdb drive for its boot files.
[*]Your menu.lst entry for Windows should be correct since it uses (hd0,0), which is the first boot drive; that should be correct since you must be booting your sda drive on start up at this point.
[*]Your Windows sda1 boot sector fortunately does not contain any Grub boot code; it looks like a healthy FAT boot sector for Windows XP (it will boot "ntldr") from the best I can tell.
[/LIST]
I think then the next step would be to use "testdisk" to see if it finds any problems with your Windows partition boot sector, because in addition to containing the boot code, the partition boot sector also seems to contain some of XP's file system parameters. First make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens when you try and boot Windows. :)

---

### Post by Scotty B on 2008-11-24
I'm still running into the same message when I try to boot XP.

When testdisk was done running, this was displayed:
> TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 30 GB / 27 GiB - CHS 3649 255 63
     Partition                  Start        End    Size in sectors
 1 * FAT32 LBA                0   1  1  3293  44 63   52904817

Boot sector
OK

Backup boot sector
OK

Sectors are identical.

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.

I don't know if that helps...

---

### Post by caljohnsmith on 2008-11-24
OK, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Windows XP
rootnoverify (hd0,0)
chainloader +1
```
Next do the following to reinstall Grub:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
Please post the output of the above commands, reboot, and try to boot Windows from the Grub menu again. Let me know exactly what happens. :)

---

### Post by Scotty B on 2008-11-24
Ok, I've got the menu.lst open, but which part do you want me to change?
This:
> #
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
or this:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-11-24
Change the entry in your second quote. :)

---

### Post by Scotty B on 2008-11-24
sudo apt-get purge grub:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 938kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119507 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
Processing triggers for man-db ...

sudo apt-get install grub:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/402kB of archives.
After this operation, 938kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub.
(Reading database ... 119456 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu45_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu45) ...
sudo grub-install --recheck /dev/sda:
> Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

Going to reboot now.

---

### Post by Scotty B on 2008-11-24
Well, I rebooted and I'm still getting that same message when I try to boot XP. :?

---

### Post by caljohnsmith on 2008-11-24
> **Scotty B said:**
> Well, I rebooted and I'm still getting that same message when I try to boot XP. :?
What exactly is the message? In post #6 you showed you were getting dumped into the Grub command line after trying to boot Windows. Does this still happen or what exactly happens when you try and boot XP?

---

### Post by Scotty B on 2008-11-24
Yes, sorry. Grub command line, same as in post #6.

---

### Post by caljohnsmith on 2008-11-24
Can you set your BIOS to boot the Ubuntu sdb drive on start up? If so, I think it would be good to restore a Windows MBR to your Windows drive and see how far Windows gets when you boot it, because I think at this point you have a Windows problem and not a Grub problem; but I could be wrong. If that sounds OK with you, please post the output of all the following commands:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
The above commands will install Grub to the MBR of your Ubuntu drive so you should be able to boot it. Next boot your Windows Install CD, go to the recovery console and run:
```
fixmbr
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. Next reboot, and before changing your BIOS to boot the Ubuntu drive, go ahead and boot the sda Windows drive and let me know exactly what happens.

---

### Post by Scotty B on 2008-11-25
sudo grub:
>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 

grub> root (hd1,0):
[nothing]
grub> makeactive:
[nothing]
grub> setup (hd1):
>  Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

Now I'm off to the Windows recovery console to run those commands.

---

### Post by Scotty B on 2008-11-25
I ran fixmbr from the recovery console and it appeared to have worked:
> Writing new master bood record on physical drive
\Device\Harddisk0\Partition0.

The new master boot record has been successfully written.
I then ran the chkdsk /r command and it finally checked everything with no apparent errors.

But, there is some bad news. I restarted and was unable to do anything. If I have the Windows disc in, it tells me I can press any key to run it, but if I don't have a disc in, all I get is a blinking cursor. Grub doesn't load and I don't even get the C: prompt.

I am currently running from my Ubuntu 8.04 disc. Did I do something wrong? Is there a special way I can "boot the sda Windows drive"?

---

### Post by caljohnsmith on 2008-11-25
OK, it sounds like you have a problem with Windows at this point, and not Grub, because restoring the Windows MBR (via fixmbr) should be enough to boot Windows. Can you set your BIOS to boot your Ubuntu sdb drive? How about doing that, and you should get the Grub menu on start up. Booting any of the Ubuntu entries will unfortunately result in a Grub error though since we haven't changed your menu.lst yet, but that should not be a problem; just select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd1,0)", press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. That should hopefully be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hd1,0)" to use the (hd0,0) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And then booting Ubuntu should work after that. 

About getting Windows to work, how about posting the following before we go further:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```

---

### Post by Scotty B on 2008-11-25
How do I set my BIOS to boot my Ubuntu sdb drive?

If I hit F10, I can get into some options, and I'm guessing maybe to change the boot order, but the only options listed are CD-ROM Drive (1st), Floppy Drive A: (2nd), and Hard Drive C: (3rd).

---

### Post by caljohnsmith on 2008-11-25
> **Scotty B said:**
> How do I set my BIOS to boot my Ubuntu sdb drive?
It depends on your BIOS; some modern BIOSes will let you press F10 or F12 on start up for example to give you a quick choice of which drive to boot off of, but that is only temporary. What you really want to do is go into your BIOS and set the "boot order" so that the sdb drive boots before the sda drive. Do you get any kind of BIOS/manufacturer screen that flashes immediately on start up that tells you which key to press to get into BIOS? Most likely it is one of the function keys (F1-F12), so if you don't know, just press as many off them as you can when you restart the computer and maybe you'll get lucky. The best way though would be to check your computer documentation or even the manufacturer of your motherboard to find out. Let me know how it goes.

---

### Post by Scotty B on 2008-11-25
I tried F1-F12 and the only one that did anything was F10 (or hitting delete took me to the same place). This takes me to the "Compaq Computer Corporation Setup Utility" which is where I was when I mentioned the three devices listed in the boot order options.
However, it does recognize that my other drive is there because if I go to the "IDE DPS Self-test" it lists both of my hard drives:
Primary Drive 0 Quantum Fireball (the Windows, C: drive), and
Primary Drive 1 Maxtor (the second hard drive containing Ubuntu)

If I put in the Ubuntu CD and restart and get to that menu, and I hit "F1 Help" then "F3 Boot methods for special ways of using this CD-ROM." there's a part that says: "...Press F4 to select alternative start-up and installation modes. Press F6 to edit boot parameters. Press F6 again to select from a menu of commonly-used boot parameters."

Is this something I could try, or is this not related to my (new) problem?

---

### Post by caljohnsmith on 2008-11-25
> **Scotty B said:**
> I tried F1-F12 and the only one that did anything was F10 (or hitting delete took me to the same place). This takes me to the "Compaq Computer Corporation Setup Utility" which is where I was when I mentioned the three devices listed in the boot order options.
However, it does recognize that my other drive is there because if I go to the "IDE DPS Self-test" it lists both of my hard drives:
Primary Drive 0 Quantum Fireball (the Windows, C: drive), and
Primary Drive 1 Maxtor (the second hard drive containing Ubuntu)

If I put in the Ubuntu CD and restart and get to that menu, and I hit "F1 Help" then "F3 Boot methods for special ways of using this CD-ROM." there's a part that says: "...Press F4 to select alternative start-up and installation modes. Press F6 to edit boot parameters. Press F6 again to select from a menu of commonly-used boot parameters."

Is this something I could try, or is this not related to my (new) problem?
Unfortunately those function key options from the Live CD won't help at this point, because they are just for booting the Live CD. Do you have a Windows Install CD, or maybe only some OEM Windows CDs? It's looks like you might have to repair you Windows that way at this point. But first, let's do one more check of your Windows partition; go ahead and boot your Live CD, and please post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```

---

### Post by Scotty B on 2008-11-25
sudo mount /dev/sda1 /mnt:
[nothing]
ls -l /mnt:
> total 524992
drwxr-xr-x   3 root root     16384 2000-08-03 11:03 All Users
drwxr-xr-x   3 root root     16384 2008-01-19 16:50 ati
-rwxr-xr-x   1 root root       143 2008-01-19 10:35 autoexec.bak
-rwxr-xr-x   1 root root       211 2008-01-19 10:35 autoexec.bat
-rwxr-xr-x   1 root root        27 2000-06-20 16:58 autoexec.dos
-r-xr-xr-x   1 root root       217 2008-08-28 10:53 boot.ini
-rwxr-xr-x   1 root root       512 2008-01-19 10:35 bootsect.dos
drwxr-xr-x   6 root root     16384 2000-08-03 11:02 compaq
-rwxr-xr-x   1 root root         0 2008-01-19 10:35 config.bak
drwxr-xr-x   2 root root    131072 2008-10-18 23:07 Config.Msi
-rwxr-xr-x   1 root root         0 2008-01-19 10:35 config.sys
drwxr-xr-x   3 root root     16384 2000-08-03 10:52 cpqdrv
drwxr-xr-x  10 root root     16384 2000-08-03 10:51 cpqs
drwxr-xr-x   7 root root     16384 2008-01-19 10:48 Documents and Settings
drwxr-xr-x   2 root root     16384 2008-07-23 19:05 found.000
-rwxr-xr-x   1 root root 536465408 2008-10-26 18:10 hiberfil.sys
-r-xr-xr-x   1 root root    110080 2000-06-08 17:00 io.sys
-rwxr-xr-x   1 root root    129078 2000-06-08 17:00 logo.sys
drwxr-xr-x   2 root root     16384 2000-08-03 11:03 lutil
-r-xr-xr-x   1 root root      1660 2000-08-03 10:47 msdos.sys
-r-xr-xr-x   1 root root     47564 2008-01-19 11:22 ntdetect.com
-r-xr-xr-x   1 root root    250048 2008-05-12 19:14 ntldr
dr-xr-xr-x  65 root root     16384 2008-01-19 10:58 Program Files
drwxr-xr-x   2 root root     16384 2008-01-19 16:21 Recycled
drwxr-xr-x   2 root root     16384 2000-06-21 11:53 system.sav
drwxr-xr-x   3 root root     16384 2008-01-19 11:08 System Volume Information
drwxr-xr-x   2 root root     16384 2008-01-19 11:53 temp
drwxr-xr-x   2 root root     16384 2008-01-19 10:37 undo
-rwxr-xr-x   1 root root     65536 2008-01-19 10:28 videorom.bin
drwxr-xr-x 198 root root     32768 2000-06-20 16:15 windows

cat /mnt/boot.ini:
> [boot loader]
timeout = 30
default = multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS = "Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

p.s. Yes, I do have a Windows Install CD

---

### Post by caljohnsmith on 2008-11-25
Just out of curiosity, did you type part of that output in your last post by hand? I'm only asking because some of the important Windows files/folders do not have the correct capitalization; for instance, the "ntdetect.com" file should actually be "NTDETECT.COM", and same with the "windows" directory--it should be "WINDOWS" to the best of my knowledge. Did you possibly do anything previously that would have changed those files/folders? 

I think at this point I would recommend doing a "Windows Repair"; if you boot your Windows XP Install CD, select the "install Windows" option at the first main menu, then after that you will be given a choice to repair your existing Windows instead of reinstalling. If you can get Windows booting again, we can add Grub back to your MBR and boot Ubuntu/Windows from Grub. How about giving that a shot and let me know how it goes.

---

### Post by Scotty B on 2008-11-25
Nope, I merely copied and pasted everything. The only time I type in things manually is when was getting messages doing the start up stuff. Even then, I tried to keep any caps. Also, I can't think of any reason those wouldn't be capitalized.

I'll try the "Windows Repair" thing.

---

### Post by Scotty B on 2008-11-25
I did the Windows Repair, but I'm still just getting the blinking cursor when I start the computer. :(

---

### Post by caljohnsmith on 2008-11-25
> **Scotty B said:**
> I did the Windows Repair, but I'm still just getting the blinking cursor when I start the computer. :(
So did the Windows repair claim that it was successful? Everything seemed to go OK? If so, I think you might have a hardware issue; can you open your computer and re-seat the HDD cable connector to make sure it is snug and well-connected? I notice that it's only a 30 GB drive, so how old is it?

---

### Post by Scotty B on 2008-11-26
Yes, it said the repair was successful and everything seemed to go OK. I disconnected and reconnected both hard drives, but it didn't seem to help. 

We bought the computer new around the time Windows XP came out so... seven years old? It actually had Windows Me on it when we bought it, and we bought XP as soon as it came out.

One thing I noticed, and I'm not sure it matters, but whenever I go into the recovery using the Windows disc, the C: prompt has always read:
C:\WINDOWS\> (or something like that) instead of C:\>. Would that make a difference? Because I can't seem to get it to go to the C:\>.

Also, I'm pretty sure the hard drive still works and is connected because when I was still able to use Ubuntu 8.10, I could access the files off of the C: drive.

At this point, unless you have any other suggestions, would it still be possible to even reinstall XP? Because right now I'm not wholly averse to the idea as I don't have much on it, and its not my primary computer.

---

### Post by caljohnsmith on 2008-11-26
At this point I'm not sure even a complete reinstall of Windows would work, because just getting a blinking cursor might mean something more fundamental is wrong; it seems like you should get some sort of Windows error or indication that Windows is even trying to boot since you fixed the MBR, the XP boot sector, and even did a Windows repair. Can you possibly swap that drive out and try it in another computer? If not, you could go ahead and back up your important files on it and try to reinstall Windows, but I'm skeptical that it will work (but maybe it will). If you do a reinstall, I would recommend setting up the Windows partition as NTFS instead of FAT32. Also, since you have Grub installed to the sdb drive and it should be bootable, can you physically swap the sdb drive with the sda drive and see if the Ubuntu sdb drive will boot? If it doesn't boot, that could give a clue if there is something wrong with where the sda drive is plugged in, in other words, possibly a motherboard issue. Anyway, let me know how it goes. :)

---

