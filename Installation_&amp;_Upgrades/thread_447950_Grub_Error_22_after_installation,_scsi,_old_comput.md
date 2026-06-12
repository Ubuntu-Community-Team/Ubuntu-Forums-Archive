---
title: "Grub Error 22 after installation, scsi, old computer"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by qwertzpoiu on 2007-05-18
I have a strange problem. I installed ubuntu server 6.06 on a older computer (from the late nineties): ASUS P2B Motherboard . it has a adaptec array1000 with a scsi disk connected to it. there's also a promise ultra 133 TX2 controller with 3 harddisks connected to it.
 (for more system specs go to [http://ubuntuforums.org/showthread.php?t=447818](http://ubuntuforums.org/showthread.php?t=447818))

I struggled to install ubuntu (on the scsi drive)  but it finally worked (and all four harddisks were found during installation.). After the installation when it's booting it says "grubstage 1.5 ... grub loading ....  error 22" . 

In bios i made it boot from scsi first. I then tried to boot from the harddisk through the ubuntu install cd which gave me the same error. 

I downloaded supergrub iso and tried to repair the MBR (master boot record) ...  didn't help. I still get the same error 22. 

Did anybody here had similar problems and could solve them?

Thanks for any help.


Ps: I'm not using dualboot. I only want to run ubuntu.

---

### Post by Herman on 2007-05-19
hello qwertzpoiu,
Can you boot a LiveCD and post the output from 'sudo fdisk -lu' here please?
 And also the boot entries at the bottom of your /boot/grub/menu.lst file.
Maybe there is a small mistake in menu.lst we can easily fix.

Also, while you have the LiveCD running, try a filesystem check, You can run a file system check on the unmounted filesystem from your terminal in the Ubuntu Live CD. Personally  I like this one to begin with,
```
sudo e2fsck -C0 -p -f -v /dev/hda2
```Where: /dev/hda2 is your Ubuntu partition and it has an ext3 filesystem.
That command shows a progress bar while the file system check is taking place, fixes what is fixable without human intervention, 'forces' the check (runs it anyway, whether it is needed or not), and gives you a verbose output when it's done.
If all goes well, that might fix it, if not, it will not do any harm (apart from possibly being a waste of time). This has fixed this same error for me once, (in my wife's computer, so it was really important! )

Regards, Herman :)

---

### Post by qwertzpoiu on 2007-05-19
Hi There

Thanks for your time.

Ok I booted with the newest Damn Small Linux Live CD (3.1 or 3.2).

Your commands with the results:
**sudo fdisk -lu**
```

Disk /dev/sda: 4335 MB, 4335206400 bytes
255 heads, 63 sectors/track, 527 cylinders, total 8467200 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/sda1              63     8466254     4233096    5  Extended
/dev/sda5   *         126      498014      248944+  83  Linux
/dev/sda6          498078     8466254     3984088+  8e  Linux LVM

Disk /dev/hdg: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hdg1   *          63   398283479   199141708+  a5  FreeBSD

Disk /dev/hde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hde1   *          63   488392064   244196001   a5  FreeBSD

```


Strangely the third harddisk connected to the promise controller isn't shown. . probably the live CD doesn't recognize the 2nd promise controller.

in **/mnt/sda5/grub** I wrote **cat menu.lst**
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/mapper/Ubuntu-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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
# defoptions=quiet splash noapic nolapic pci=noacpi acpi=off

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

title           Ubuntu, kernel 2.6.15-26-server
root            (hd2,4)
kernel          /vmlinuz-2.6.15-26-server root=/dev/mapper/Ubuntu-root ro quiet splash noapic nolapic pci=noacpi acpi=off
initrd          /initrd.img-2.6.15-26-server
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-server (recovery mode)
root            (hd2,4)
kernel          /vmlinuz-2.6.15-26-server root=/dev/mapper/Ubuntu-root ro single
initrd          /initrd.img-2.6.15-26-server
boot

title           Ubuntu, memtest86+
root            (hd2,4)
kernel          /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

then I changed back to root folder **cd /**

After that I executed **sudo umount /mnt/sda5**

 Then I made **sudo e2fsck -C0 -p -f -v /dev/sda5**
```

      30 inodes used (0%)
       2 non-contiguous inodes (6.7%)
         # of inodes with ind/dind/tind blocks: 7/3/0
   29376 blocks used (11%)
       0 bad blocks
       0 large files

      18 regular files
       3 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
      21 files

```

I hope this output will help you. If you need more information just tell me.

Ps: Something which I have to tell you. When I want to boot from CDROM I need to put IDE in BIOS to the "Boot first from..." parameter. When I want to boot from the SCSI Drive I need to switch that to SCSI. Probably this also interferes with the menu.lst ... Because when I installed the system I needed to boot from IDE. So it could be that the mounting points in menu.lst should be changed?

Thanks for your help!

---

### Post by Herman on 2007-05-19
Hello qwertzpoiu, :)
Your file system passed the file system check okay, a file system check is always good and it does solve problems sometimes.

I think I see a mistake in your menu.lst file. Yes it does confuse Grub if changes are made to the hard disk boot priority in the BIOS.
Having a mixture of scsi and IDE drive often gets grub all mixed up too.
At the moment you ran the fdisk command, your Ubuntu disk was /dev/hda5, which in Grub's language corresponds with (hd0,4).
In your menu.lst file you are trying to boot an operating system in (hd2,4), which mean your third hard disk's 5th partition.
You could try changing the entries in your menu.lst file from (hd2,4) to (hd0,4) and hopefully that will fix your problem.
```
 ## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-server
root            (hd[COLOR=Red]**0**[/COLOR],4)
kernel          /vmlinuz-2.6.15-26-server root=/dev/mapper/Ubuntu-root ro quiet splash noapic nolapic pci=noacpi acpi=off
initrd          /initrd.img-2.6.15-26-server
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-server (recovery mode)
root            (hd[COLOR=Red]**0**[/COLOR],4)
kernel          /vmlinuz-2.6.15-26-server root=/dev/mapper/Ubuntu-root ro single
initrd          /initrd.img-2.6.15-26-server
boot

title           Ubuntu, memtest86+
root            (hd[COLOR=Red]**0**[/COLOR],4)
kernel          /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```If that doesn't fix it, try booting up from grub's [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and do a [direct kernel boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."). While you are doing that you will be able to use the feedback from Grub's command line interface to guide you. Copy the commands you needed to boot in CLI mode down on a piece of paper. You can use the same commands to edit your menu.lst file with as soon as the operating system has booted.
Booting up from Grub's Command Line Interface is pretty reliable, you can use any Grub Command Line Interface, it can be from your hard disk installed Grub or from Super Grub Disk.
Please let me know if you have any more problems or need to check up on anything you're not sure about.
Regards, Herman :)

---

### Post by qwertzpoiu on 2007-05-19
Hello

Thanks for your fast reply.

I tried your stuff but it didn't work.

I remembered that I installed LVM on that disc and reinstalled the system without any LVM so there would be less problems.
The new error is Error 17 (partition not found or something like that)

After the reinstall the disk is now listed as /dev/sda1 and standard mountpoint in menu.lst is hd(2,0). 
I now changed it to
0,0
1,0
2,0
3,0
5,0
8,1 (which was shown when I started damn small linux in at runlevel 2 (console only) I think or no .. it was SuperGRUB .. not sure anymore , so I tried it out..  after so many tries :-)

None of those worked.

I also tried to run the system through direct kernel boot. It somehow worked but not until the end. It loaded the drivers for disks and other things but then in the end it couldn't find some drive "sdd" or something. It presented me a very simple console. Probably some rescue console?

I will try to change the menu.lst entries to 8,0 and 4,0 but after that I will go to sleep. It's already 5:20 am here.

PS: 4,0 doesn't work either.


Thanks for your help.

Greetings
qwertz

---

### Post by confused57 on 2007-05-20
If your bios is capable of booting first to your sda drive, you could use Herman's guide to install grub to the sda mbr:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Boot up the live cd, then open a terminal:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd2,0)", you would then enter:
```
root (hd2,0)
setup (hd2)
quit
```

This should install grub to your /dev/sda mbr, now set bios to boot first to this hard drive & you should get a grub menu at boot...if you do, highlight the Ubuntu entry, press "e", then change root from (hd2,0) to (hd0,0), then press "b" to boot.  This change is temporary(if it works), but it shouldn't hurt anything to try.

---

### Post by qwertzpoiu on 2007-05-20
Hi there

Thanks for your help.

Didn't work, though :(


I have read out some infos with live cd from the new installation: 


fdisk -lu

Disk /dev/sda: 4335 MB, 4335206400 bytes
255 heads, 63 sectors/track, 527 cylinders, total 8467200 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/sda1   *          63     8048564     4024251   83  Linux
/dev/sda2         8048565     8466254      208845    5  Extended
/dev/sda5         8048628     8466254      208813+  82  Linux swap

Disk /dev/hdg: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hdg1   *          63   398283479   199141708+  a5  FreeBSD

Disk /dev/hde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hde1   *          63   488392064   244196001   a5  FreeBSD

----------------------------------------------

[/mnt/sda1/boot/grub]# cat device.map

(hd0)   /dev/hde
(hd1)   /dev/hdg
(hd2)   /dev/sda

-----------------------------------------------

part of cat /mnt/sda1/boot/grub/menu.lst

title           Ubuntu, kernel 2.6.15-26-server
#root            (hd2,0)
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/sda1 ro quiet splash no
apic nolapic pci=noacpi acpi=off
initrd          /boot/initrd.img-2.6.15-26-server
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-server (recovery mode)
#root            (hd2,0)
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.15-26-server root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-26-server
boot

title           Ubuntu, memtest86+
#root            (hd2,0)
root            (hd2,1)
kernel          /boot/memtest86+.bin
boot

-------------------------------------

grub> find /boot/grub/stage2
 (hd2,0)

grub>

-------------------------------------


cd /mnt/sda1

 ls -l
drwxr-xr-x    2 root     root         4096 May 19 21:47 bin
drwxr-xr-x    3 root     root         4096 May 19 21:47 boot
lrwxrwxrwx    1 root     root           11 May 19 21:31 cdrom -> media/cdrom
drwxr-xr-x   11 root     root        32768 May 19 21:49 dev
drwxr-xr-x   54 root     root         4096 May 19 21:48 etc
drwxr-xr-x    3 root     root         4096 May 19 21:48 home
drwxr-xr-x    2 root     root         4096 May 19 21:33 initrd
lrwxrwxrwx    1 root     root           32 May 19 21:43 initrd.img -> boot/initrd.img-2.6.15-26-server
drwxr-xr-x   16 root     root         4096 May 19 21:47 lib
drwxr-xr-x    2 root     root        49152 May 19 21:31 lost+found
drwxr-xr-x    4 root     root         4096 May 19 21:31 media
drwxr-xr-x    2 root     root         4096 Aug  3  2006 mnt
drwxr-xr-x    2 root     root         4096 May 19 21:33 opt
drwxr-xr-x    2 root     root         4096 Aug  3  2006 proc
drwxr-xr-x    3 root     root         4096 May 19 21:43 root
drwxr-xr-x    2 root     root         4096 May 19 21:48 sbin
drwxr-xr-x    2 root     root         4096 May 19 21:33 srv
drwxr-xr-x    2 root     root         4096 May 21  2006 sys
drwxrwxrwt    2 root     root         4096 May 19 21:49 tmp
drwxr-xr-x   10 root     root         4096 May 19 21:33 usr
drwxr-xr-x   13 root     root         4096 May 19 21:33 var
lrwxrwxrwx    1 root     root           29 May 19 21:43 vmlinuz -> boot/vmlinuz-2.6.15-26-server


I don't know what else I could do ...   I could start trying hd0,1   1,1  2,1 3,1 and so on .. ;-)

---

### Post by qwertzpoiu on 2007-05-20
I added another harddisk (some old 1.6 GB disk which lie around) and connected it to the mainboard primary channel.

I wanted to put grub on that harddisk but didn't really know how to do it.

I then had the idea to put grub on a floppy. I found some manual online [http://gentoo-wiki.com/HOWTO_Bootable_Floppy_with_GRUB]("http://gentoo-wiki.com/HOWTO_Bootable_Floppy_with_GRUB")
 and did all the steps explained there. I changed the menu.lst on the floppy to (hd3,0) and booted.

Now the grub menu loads and it will load linux from the scsi-harddisk. It's probably not a "nice solution" but until I  find out what cause my problems I will stick to that.

Thanks for your help folks.

---

