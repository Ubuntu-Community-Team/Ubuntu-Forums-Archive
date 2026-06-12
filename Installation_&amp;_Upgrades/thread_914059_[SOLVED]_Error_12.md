---
title: "[SOLVED] Error 12"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by bilkas on 2008-09-08
Error 12: Invalid device requested

This is the thing I see when I try to boot to Vista in GRUB. I`ll be greatfull for any help. I have NONE experience in Linux so PLEASE write everything in a way that a child will understand. Thanks for any help!

Mat

I`ve lost all my data, but now I know where I`ve made the mistake. Right now I`am running Vista and Ubuntu without any problems. Thanks all you guys who wanted to help me.

---

### Post by manishtech on 2008-09-08
Can you please post the contents of this file 

```
/boot/grub/menu.lst
```

---

### Post by bilkas on 2008-09-08
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
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows Vista
root		(hd0,4)
savedefault
makeactive
chainloader	+1


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
# kopt=root=UUID=691ae202-b449-40ba-a169-dbf0e29d623a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=691ae202-b449-40ba-a169-dbf0e29d623a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=691ae202-b449-40ba-a169-dbf0e29d623a ro single
initrd		/boot/initrd.img-2.6.24-16-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Dell Utility Partition
#root		(hd0,0)
savedefault
makeactive
chainloader	+1






thats all; thanks for reply :)

---

### Post by manishtech on 2008-09-08
Your windows is on first partition or 4th? Looks like some config error in GRUB. Its simple to fix if I can know the layout the partitions. Can you just tell us the output of command 

```
sudo fdisk -l
```


This command gives the partitions of all disks attached on the system.

---

### Post by Pumalite on 2008-09-08
You are trying to boot Vista from a logical partition. Vista needs a primary partition, preferably sda1

---

### Post by bilkas on 2008-09-09
sudo fdisk -1  :

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317       13281    96100586    7  HPFS/NTFS
/dev/sda4           13282       14594    10539665    f  W95 Ext'd (LBA)
/dev/sda5           14333       14594     2096128   dd  Unknown
/dev/sda6           13282       14281     8032468+  83  Linux
/dev/sda7           14282       14332      409626   82  Linux swap / Solaris

Partition table entries are not in disk order



:D

---

### Post by manishtech on 2008-09-09
This means disk is like 

[COLOR=Blue]sda1 sda2 sda3[/COLOR] [COLOR=Purple]sda4[/COLOR] [[COLOR=DarkOrange]sda6 sda5 sda7[/COLOR]]

Here sda1,sda2,sda3 are primary partitions and sda4 is extended which contains sda6 then sda5 and then sda7

---

### Post by manishtech on 2008-09-09
Looks like windows is on sda3

```

title		Microsoft Windows Vista
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

change this to

```

title		Microsoft Windows Vista
 root		(hd0,2)
 savedefault
 makeactive
 chainloader	+1
```

---

### Post by bilkas on 2008-09-09
ok, something has changed - now when i try to boot on vista i see:

Error 13: Invalid or unsupported executable format

any ideas what to do next? :(

---

### Post by caljohnsmith on 2008-09-09
It could be that Vista is actually on sda2 instead of sda3, so try this in your menu.lst:
```
title		Microsoft Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```
Also, at the very end of your menu.lst you have:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title Dell Utility Partition
#root (hd0,0)
savedefault
makeactive
chainloader +1
```
You should put pound signs (#) in front of all those lines:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title Dell Utility Partition
#root (hd0,0)
[COLOR="Blue"]#[/COLOR]savedefault
[COLOR="Blue"]#[/COLOR]makeactive
[COLOR="Blue"]#[/COLOR]chainloader +1
```
Let us know if that works or if you get another error.

---

### Post by bilkas on 2008-09-09
i`ve made all the changes  and when i tried to boot on vista i get:

BOOTMGR is missing
press ctrl + alt + del to restart

what next? :|

---

### Post by caljohnsmith on 2008-09-09
> **bilkas said:**
> i`ve made all the changes  and when i tried to boot on vista i get:

BOOTMGR is missing
press ctrl + alt + del to restart

what next? :|
Well that's good news and bad news; the good news is that we found the correct partition for Vista, but the bad news is Vista is broken. 

Did you use gparted (i.e. the partition editor in Ubuntu) to repartition your HDD when you installed Ubuntu? Because if that is the case, it would probably explain your error; Microsoft (in their infinite wisdom) designed Vista so that it maintains its own partition table outside of the main one stored in your HDD's master boot record (MBR). What that means in practicality is that if you make any changes to your HDD's partitions without using the Vista Disk Management tool, you can break Vista. I'm imagining that's what unfortunately happened to you. Is that your scenario?

If it is, you'll need a Vista Recovery CD/DVD to fix Vista (you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") if you don't have one). Boot that disk, go into the recovery console or command line, and run the command:
```
bootrec /rebuildbcd
```
That should hopefully be all it takes to get Vista going again. Let me know how it goes. :)

---

### Post by manishtech on 2008-09-09
> it would probably explain your error; Microsoft (in their infinite wisdom) designed Vista so that it maintains its own partition table outside of the main one stored in your HDD's master boot record (MBR)
That's sweet kicking the a$$ badly with sweet words! Nice explanation... :)

---

### Post by Pumalite on 2008-09-09
That happened becuase they didn' allocate 'free space' for Ubuntu first with the Vista Partitioner.

---

### Post by bilkas on 2008-09-09
I`ve got a 'Reinstalation DVD for Windows Vista Home Premium 32BIT` is that it? Anyway I did what you told me: boot that DVD, whent to console, insert bootrec /rebuildbcd and I`ve got something like this:

X:\Sources>bootrec /rebuildbcd

Scanning all disks for Windows installations...

Please wait since this may take a while..

Succesfully scanned Windows installations
Total identified Windows installations: 0

The operation completed succesfully





Maybe its the wrong DVD I got? O nthe bottom of it its written: Only use this DVD to reinstall the operating system on a Dell PC; 

I dont care about the operating system (vista) but i do care about some folders witch, right now, i cant access from Ubuntu. Is there any chance of getting them out, someway, somehow? :)

Thanks for everything!

---

### Post by caljohnsmith on 2008-09-09
> **bilkas said:**
> I`ve got a 'Reinstalation DVD for Windows Vista Home Premium 32BIT` is that it? Anyway I did what you told me: boot that DVD, whent to console, insert bootrec /rebuildbcd and I`ve got something like this:

X:\Sources>bootrec /rebuildbcd

Scanning all disks for Windows installations...

Please wait since this may take a while..

Succesfully scanned Windows installations
Total identified Windows installations: 0

The operation completed succesfully





Maybe its the wrong DVD I got? O nthe bottom of it its written: Only use this DVD to reinstall the operating system on a Dell PC; 

I dont care about the operating system (vista) but i do care about some folders witch, right now, i cant access from Ubuntu. Is there any chance of getting them out, someway, somehow? :)

Thanks for everything!
OK, first to access your Vista partition in Ubuntu, if you open up Ubuntu's default file browser nautilus (look under the "Places" menu on your desktop), on the left side should be a list of partitions or "media" that you can mount. Click on the one that says something like "10 GB media" and that will probably be your Vista partition; you can copy and paste folders to back up from there. 

I think you have the right DVD, but since bootrec didn't seem to find your Vista partition, first do the command:
```
bootrec /fixboot
```
and then try doing again:
```
bootrec /rebuildbcd
```
Let me know exactly what it says, and if it doesn't work, we can try another method.

---

### Post by bilkas on 2008-09-09
Ok, I`ve entered the console one more time and this is what I`ve got

X:\Sources>bootrec /fixboot
The operation ended succesfully

X:\Sources>bootrec /rebuildbcd
Scanning all disks for Windows installations...

Please wait since this may take a while..

Succesfully scanned Windows installations
Total identified Windows installations: 0

The operation completed succesfully




The same as above. What next? :)

---

### Post by caljohnsmith on 2008-09-09
Using the nautilus file manager, look in both sda2 and sda3 and see if either of those Windows partitions have the "bootmgr" file in their root directory. Nautilus should show those partitions in the left pane as something like "10 GB media" and "95 GB media" or similar. If you can't find that file that way, please do the following:
```
sudo umount /dev/sda2 [COLOR="Blue"][don't worry if this or the next command returns an error about it not being mounted, this is just to make sure][/COLOR]
sudo umount /dev/sda3   
sudo mkdir /media/sda2
sudo mkdir /media/sda3
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda3 /media/sda3
ls -l /media/sda2
ls -l /media/sda3
```
And post the output.

---

### Post by bilkas on 2008-09-09
here are the results:

sudo umount /dev/sda2
umount: /dev/sda2: not mounted

sudo umount /dev/sda3
umount: /dev/sda3: not mounted

sudo mkdir /media/sda2
mkdir: nie mo&#380;na utworzy&#263; katalogu `/media/sda2': File exists
      (could`nt open the folder? catalog? 
         its in polish :))

sudo mkdir /media/sda3
mkdir: nie mo&#380;na utworzy&#263; katalogu `/media/sda3': File exists
      (could`nt open the folder? catalog?)
 
sudo mount /dev/sda2 /media/sda2
mount: /dev/sda2 already mounted or /media/sda2 busy
mount: according to mtab, /dev/sda2 is already mounted on /media/sda2

sudo mount /dev/sda3 /media/sda3
and nothing happened

ls -l /media/sda2
ls: nie mo&#380;na otworzy&#263; katalogu /media/sda2: Permission denied 
   (could`nt open the folder? catalog? 
         its in polish :))

ls -l /media/sda3
razem 16     ('razem' means total)
drwx------ 2 root root 16384 2008-09-08 16:43 lost+found




thats all... 

when i try to open nautilus I see: Nosnik (means HDD) 98,4 GB and this the place where all my files are; including Vista. The RECOVERY HDD is... i dont know i never used it. it was made by Vista in first place. Ow and i try to get those files but it didnt work. 

Thanks - Mat

---

### Post by caljohnsmith on 2008-09-09
Hmmmm... It looks like maybe nautilus was all ready looking in that /media/sda2 directory or something similar, because that might have prevented sda2 from being mounted there. How about rebooting to start fresh, and before you open any file browsers or anything else, open a terminal and try the following (similar to before):
```
sudo umount /dev/sda2
sudo umount /dev/sda3   
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda3 /media/sda3
ls -l /media/sda2
sudo ls -l /media/sda3/lost+found
```
Please post the output.

---

### Post by bilkas on 2008-09-09
Ok, after I reboot I`ve opened the terminal before anything else and here is what I`ve got:

sudo umount /dev/sda2
                 sda3
umount: /dev/sda2: not mounted
             sda3: not mounted

sudo mount /dev/sda2 /media/sda2
                sda3        sda3
nothing happened; it just moved to another line in the terminal; and there are icons on the desktop (they also appeared last time but I didnt know this might be important)

ls -l /media/sda2
ls: nie mozna otworzyc katalogu /media/sda2: permission denied
    (`couldnt open folder? catalog?`)

sudo ls -l /media/sda3/lost+found
total 0



and I`ve entered one thing more:
sudo ls -l /media/sda2

total 12
dr-x------ 1 root root    0 2008-09-10 03:05 Boot
dr-x------ 1 root root    0 2007-08-22 02:29 dell
dr-x------ 1 root root    0 2006-11-02 11:22 ProgramData
dr-x------ 1 root root    0 2006-11-02 11:23 Program Files
dr-x------ 1 root root    0 2007-08-28 10:30 $RECYCLE.BIN
dr-x------ 1 root root    0 2006-11-17 17:06 sources
dr-x------ 1 root root    0 2007-08-21 16:47 System Volume Information
dr-x------ 1 root root    0 2008-09-10 03:12 Temp
dr-x------ 1 root root 4096 2007-08-22 02:42 Tools
dr-x------ 1 root root    0 2006-11-02 11:22 Users
dr-x------ 1 root root 8192 2007-08-22 02:29 Windows



but there is nothing interesting for me on that partition; its the sda3 witch holds all the files I need

---

### Post by caljohnsmith on 2008-09-09
> **bilkas said:**
> 
sudo ls -l /media/sda3/lost+found
total 0

but there is nothing interesting for me on that partition; its the sda3 witch holds all the files I need
I hate to break the bad news about sda3, but the only thing on your sda3 partition is that empty "lost+found" folder. I don't know what files you had there previously, but based on what you've posted, there is nothing on sda3 besides the empty lost+found folder. :(

I'm not sure what happened with your Vista partition either, but it is definitely missing the bootmgr file that you need to boot. You should be able to fix it with your Vista DVD. Just boot the Vista DVD, and when you get to the screen that looks like:
[IMG]http://lifehacker.com/assets/resources/2007/04/systemrecovery.png[/IMG]
Select the "startup repair" option. I think it is fairly self-explanatory from there, but let me know if you have problems.

---

### Post by Pumalite on 2008-09-09
It will not repair your Vista in a logical partition
Post a screenshot of Gparted

---

### Post by caljohnsmith on 2008-09-09
> **Pumalite said:**
> It will not repair your Vista in a logical partition
Post a screenshot of Gparted
His Windows Vista is on sda2, which is a primary partition. :)

---

### Post by Pumalite on 2008-09-09
I'd like to see the screenshot first.

---

### Post by bilkas on 2008-09-10
Could you guys tell me how to do this? When I search for file Gparted, computer finds it, but I cant open it. It says that I dont have the right explorer to view those files. So what should I do? 

Are there any chances of getting back those files? MAybe there is some kind of program which can restore data? ;(

Ow! I try to use the `Startup Repair' option even before I`ve posted here but all it says is: 'Vista can not repair the startup right now. You can try to help us by sending the problem to Microsoft bla bla bla...' I`ve tried everything in that menu so its not the answer.

---

### Post by Pumalite on 2008-09-10
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Take a shot with the camera icon and place it here.

---

### Post by caljohnsmith on 2008-09-10
> **bilkas said:**
> 
Ow! I try to use the `Startup Repair' option even before I`ve posted here but all it says is: 'Vista can not repair the startup right now. You can try to help us by sending the problem to Microsoft bla bla bla...' I`ve tried everything in that menu so its not the answer.
I think if Vista can't repair itself, your best bet at this point would be to back up all your important files from Vista and just do a reinstall. But if you want to try a last ditch effort to save Vista, you could search your Vista DVD for that "bootmgr" executable, and if it is not in some special compressed format, you could just copy it over to your Vista root directory and see if that gets you any closer to getting Vista to boot.

---

### Post by bilkas on 2008-09-10
Thanks :) But when I tried to do a screenshot I could`nt find it. It was`nt in /root folder. Im sure of it. So I just write everything down:

partition                  label      size       used      free     flag

/dev/sda1     fat16        -          86.26MB    7.15MB    79.1     -

/dev/sda2     ntfs         recovery   10GB       3.65GB    6.35     boot

/dev/sda3     ext3         -          91.65G     927.95MB  90.74G   -

unallocated   unalloceated            4.13MB     -         -        -

/dev/sda4     extended     -          10.05GB    -         -        lba

  /dev/sda6   ext3         -          7.66GB     2.9GB     4.76GB   -

  /dev/sda7   linux-swap   -          400.03MB   -         -        -

  unallocat.  unallocated  -          1.38MB     -         -        -

  /dev/sda5    fat32        Mediadirec 2GB        780.76    1.24GB   -

---

### Post by bilkas on 2008-09-11
Is there possibility that everything will work after switching from ext3 to ntfs? Is it possible to do that?

I dont care about Vista, all I need is just some files from my user directory. When try to open the partition where all that stuff should be,  all I can see is just Lost+found folder :(

---

### Post by Pumalite on 2008-09-11
Save your pictures movies and vides. Delete everything in your drive and install Ubuntu alone.

---

