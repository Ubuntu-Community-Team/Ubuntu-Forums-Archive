---
title: "Dual boot, error 21"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Lethys on 2007-04-14
I’ve just installed Ubuntu on my computers second hard drive.  After I restarted it, whenever I try to load window I get

```
GRUB Loading stage1.5

GRUB loading, please wait…
Error 21

```

I’m only able to load ubuntu with the disc and whenever I shut it down, the disk will eject and my computer will freeze.

---

### Post by bulldog on 2007-04-14
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

So you have to correct this in menu.lst.
 Can you give us the output of the fdisk command?
Use the live cd to perform the next command fro a terminal.
```
sudo fdisk -l
``` it's a lowercase L,not a 'one'

---

### Post by matth1 on 2007-04-14
I have a very similar problem, that is I also get an error 21 from grub when trying to boot in. However I have my dual boot on a single HD.

Should I post here or start a new thread (to avoid confusion)?

---

### Post by bulldog on 2007-04-14
> **matth1 said:**
> I have a very similar problem, that is I also get an error 21 from grub when trying to boot in. However I have my dual boot on a single HD.

Should I post here or start a new thread (to avoid confusion)?

Well you can post here,there's no respons from the original TS.
If you have just one hdd with the two OS's,it's odd GRUB won't see  your hdd.
Did you install ubuntu without problems on the same hdd?

---

### Post by van1 on 2007-04-14
I was trying to install on an external hard drive (Iomega) on a Windows/Intel laptop and I had the same issue with my computer booting only from the live cd. It no longer boots Windows. On running sudo fdisk -l I got the following info:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device          Boot              Start              End          Blocks      Id     System
/dev/hda1       *                      1            4864      39070048+   7    HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device          Boot              Start              End          Blocks       Id     System
/dev/sda1        *                      1           60613    486873891    83    Linux
/dev/sda2                         60614           60801       1510110      5    Extended
/dev/sda5                         60614           60801       1510078+  82    Linux swap / Solaris

When I try to access the external drive from Computer (from the live cd) it gives me an error:
Unalble to mount the selected volume
mount: /dev/sda1:can't read superblock
error:could not execute pmount


If anyone can help me solve this issue, thanks in advance.

---

### Post by bulldog on 2007-04-14
> **van1 said:**
> I was trying to install on an external hard drive (Iomega) on a Windows/Intel laptop and I had the same issue with my computer booting only from the live cd. It no longer boots Windows. On running sudo fdisk -l I got the following info:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device          Boot              Start              End          Blocks      Id     System
/dev/hda1       *                      1            4864      39070048+   7    HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device          Boot              Start              End          Blocks       Id     System
/dev/sda1        *                      1           60613    486873891    83    Linux
/dev/sda2                         60614           60801       1510110      5    Extended
/dev/sda5                         60614           60801       1510078+  82    Linux swap / Solaris

When I try to access the external drive from Computer (from the live cd) it gives me an error:
Unalble to mount the selected volume
mount: /dev/sda1:can't read superblock
error:could not execute pmount


If anyone can help me solve this issue, thanks in advance.

Some questions.

1/ you did the install without errors on a external hdd?
2/on which device is GRUB installed?
3/you can boot {BIOS} from an USB device?

---

### Post by van1 on 2007-04-14
Hi,
When I initially tried to install I had an error message saying that the ext3 partition file could not be written to the drive. However when I tried reinstalling, I used the erase entire disk option and then it installed without any trouble. I do not know for sure where GRUB is installed (Can you tell me how I could find out?). I am able to access the BIOS from the startup screen.
Thanks.

---

### Post by bulldog on 2007-04-14
To find GRUB just start from the internal hdd,if it's there you'll notice :D 
It's installed to the hd0 by default,which should be the internal hdd.
It should be better,however,to install it on the external hdd,so when you choose to boot from USB hdd,GRUB loads and you can access ubuntu.
You van boot windows with it's own boot loader.

If GRUB is on the windows hdd,you need the windows install cd to correct this.
Boot the windows install disk and go trough it till you get three options
1/Install windows
2/repair a windows install
3/exit
Choose repair windows,which bring you to a console window.
Log in to the existing windows,mostly 1,and provide the administrator password.
Type fixmbr and fixboot after the login,you'll get a warning but just ignore that one,in most cases there's nothing wrong.
After that you can boot windows again without GRUB.

Now boot from the live cd and reinstall GRUB to the external hdd.
 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Take a good look at the find/boot/stage1 command,the hdd which will be returned can be (hd0,?) or (hd1,?),if it's hd1 use setup (hd1) instead of (hd0).

After this we'll have a look if ubuntu will boot,there's a fair chance it won't but we'll see.

---

### Post by van1 on 2007-04-14
Hi,
Thanks for trying but I could not get Windows recovery cd to work. So, I am not able to try what you suggested. The cd boots but freezes.

---

### Post by bulldog on 2007-04-14
Try this link,
[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

If I'm well informed you can do the rescue with this program too.

---

### Post by Lethys on 2007-04-14
```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 822280 bytes

	Device Boot	Start	End	Blocks		Id	system 
/dev/hda1		1	5	40131		de	Dell Utility
/dev/hda2       *	6	7294	58548892+	7	HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

	Device Boot		Start		End		Blocks		     Id	     System
/dev/hdb1       *		1		14405		115708131	83	Linux
/dev/hdb2			14406		14593		1510110	        5      Extended
/dev/hdb5			14406		14593		1510078+      82     Linux swap / Solaris

```

I did as you said and this is what I got.

---

### Post by bulldog on 2007-04-14
> **Lethys said:**
> ```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 822280 bytes

	Device Boot	Start	End	Blocks		Id	system 
/dev/hda1		1	5	40131		de	Dell Utility
/dev/hda2       *	6	7294	58548892+	7	HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

	Device Boot		Start		End		Blocks		     Id	     System
/dev/hdb1       *		1		14405		115708131	83	Linux
/dev/hdb2			14406		14593		1510110	        5      Extended
/dev/hdb5			14406		14593		1510078+      82     Linux swap / Solaris

```

I did as you said and this is what I got.

Well that seems to be in order :D 
Now we have to take a look at the menu.lst to see how things are listed in there.
I presume you use the live cd,so we mount your ubuntu first,just copy and paste the commands.
```
sudo mkdir /mnt/rescue
sudo mount /dev/hdb1 /mnt/rescue
sudo cp /mnt/rescue/boot/grub/menu.lst /mnt/rescue/boot/grub/menu.lst-backup
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```
This will open the menu.lst in a text editor,don't change anything,just copy and paste it to the forum please.

---

### Post by Lethys on 2007-04-14
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
# kopt=root=UUID=e448fd77-e635-47c0-b4ef-d3d3fb3f256f ro
# kopt_2_6=root=/dev/hdb1 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

Ok, here it is.

---

### Post by confused57 on 2007-04-14
You might need to enter your bios setup(I think it's F2 at bootup), make sure your slave drive is set to "auto"...my Dell bios had the slave hd set to "off" by default with only one hard drive installed.

---

### Post by Lethys on 2007-04-14
Yay! It worked.

---

### Post by confused57 on 2007-04-15
> **Lethys said:**
> Yay! It worked.

Great, I thought it would...I had the same problem installing on my Dell:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

