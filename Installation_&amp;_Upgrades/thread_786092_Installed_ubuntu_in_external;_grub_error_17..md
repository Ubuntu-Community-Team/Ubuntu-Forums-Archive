---
title: "Installed ubuntu in external; grub error 17."
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by FusiveResonance on 2008-05-07
I've installed ubuntu on my external hard drive, and made sure to install grub to my external drive also (sdb). Every time i boot from the drive though, i receive grub error 17. When i unplug the external, windows boots from the internal normally. Help me boot linux, thanks.

Here is my "sudo fdisk -l"
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa8489dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11675    93773824    7  HPFS/NTFS
/dev/sda2           11675       19458    62514176    f  W95 Ext'd (LBA)
/dev/sda5           11675       19458    62513152    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3be71f61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       50227   403440430    7  HPFS/NTFS
/dev/sdb2           50228       60801    84935655    5  Extended
/dev/sdb5           50228       60365    81433453+  83  Linux
/dev/sdb6           60366       60801     3502138+  82  Linux swap / Solaris

```


and here is my "menu.lst"
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
# kopt=root=UUID=72b3e8b0-1692-47e1-8f7d-c190a5f2dbf5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72b3e8b0-1692-47e1-8f7d-c190a5f2dbf5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72b3e8b0-1692-47e1-8f7d-c190a5f2dbf5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
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


```

---

### Post by FusiveResonance on 2008-05-08
bump. Help Please

---

### Post by b0b138 on 2008-05-08
Try changing the (hd1,4) listed on menu.lst to other numbers. Grub may see your external drive as the first drive. I had the same thing happen. You can press "e" at the boot menu to go in and make edits without having to change the file and reboot every try. This change is only temporary so once you find the right numbers, you'll need to edit menu.lst once booted.

Can you boot into windows with the external drive connected?

---

### Post by b0b138 on 2008-05-08
try (hd0,3)

---

### Post by confused57 on 2008-05-08
Highlight your first Ubuntu entry in the grub boot menu, press "e", highlight the line with root, press "e" again, change root from (hd1,4) to (hd0,4), press "enter", then "b" to boot.  This change is temporary if it works, but can be made permanent:
```
gksudo gedit /boot/grub/menu.lst
```
Also, change the line with #groot to (hd0,4)...leave the # in front of groot.

---

### Post by FusiveResonance on 2008-05-08
i tried hd(0,3) --> no success
tried hd(0,4) --> no success.

I can't edit the entries from grub as you've mentioned. pressing e does nothing. It simply says error 17. I then pop in my live CD, press ctrl+alt+del to restart and change the menu.lst on my external drive once im into linux. 

Help Please.

---

### Post by FusiveResonance on 2008-05-09
bump. Help please

---

### Post by dstew on 2008-05-09
Just to be clear on this, grub is installed to the MBR of the external drive. When the external drive is plugged in, the BIOS sees it as coming before the internal hard disk in the boot order, and the BIOS loads grub. Am I correct so far?

Then when grub starts, do you see the grub menu, or does it just give Error 17 without any explanation? If you get the error before you see the menu, then grub is probably mis-installed, and editing the menu.lst will not help. You would have to re-install grub.

---

### Post by FusiveResonance on 2008-05-09
Correct.

Yes, i see the error before i get a menu. 

I tried re-installing grub by booting into the live cd and typing

```
sudo grub-install /dev/sdb
```

but i just see

```
ubuntu@ubuntu:/$ sudo grub-install /dev/sdb
Could not find device for /boot: Not found or not a block device.

```

thanks

---

### Post by Pumalite on 2008-05-09
Can you boot to Windows?

---

### Post by confused57 on 2008-05-09
> **FusiveResonance said:**
> Correct.

Yes, i see the error before i get a menu. 

I tried re-installing grub by booting into the live cd and typing

```
sudo grub-install /dev/sdb
```

but i just see

```
ubuntu@ubuntu:/$ sudo grub-install /dev/sdb
Could not find device for /boot: Not found or not a block device.

```

thanks

Try reinstalling grub to the external drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
something like:
```
root (hd1,4)
setup (hd1)
```

Added:  If you get a grub boot menu, try what I suggested earlier.

I'd recommend burning a copy of Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
See if SGD can boot Ubuntu or what error messages it gives...I've seen SGD give a grub error 18 when grub showed error 17...

---

### Post by dstew on 2008-05-09
Before you re-install grub, you need to figure out what you want your system to do. It seems that maybe you want it to boot the external hard drive to Ubuntu when it is plugged in, but boot to Windows when it is not plugged in. Is this right?

Assuming your BIOS can boot a USB drive, which it seems it can, you would need to install grub to the MBR of the external drive, but pointing to the correct root partition. The root partition is the partition that has grub's stage2 file and menu. The method outlined in the link that confused57 posted should be tried. The grub **find /boot/grub/stage2** command will tell you what root partition to use. Then, setup the grub boot loader in the MBR of the disk that contains the /boot/grub/stage2 file. That is, if find /boot/grub/stage2 returns (hd1,0), then the setup command should be ```
setup (hd1)
```

---

### Post by FusiveResonance on 2008-05-09
Thanks for your prompt replies.

I used find /boot/grub/**stage1** instead of _stage2_. Is this ok? Its the same thing for this purpose isnt it. So if it was ok to use that command with stage1, then it said (hd1,4) and so i executed:

```

sudo grub
find /boot/grub/stage1
root (hd1,4)
setup (hd1)
quit 
```

Everything finished successfully (i saw no error messages)

I restarted and attempted to boot in once more. Again - same thing. Error 17 with no menu prior. 

I also tried super grub. 

I tried this option "Boot GNU/Linux" and received error 15: file not found.

I also tried "Boot Automatically (Partition and Slice) and once again received error 15: file not found. 

If you would like to see me try any other option on the cd, do let me know which one and what menus to choose and i will comply. 

Regards,

---

### Post by Pumalite on 2008-05-09
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by confused57 on 2008-05-09
How old is your computer, just in case it might be a bios limitation(grub error 18)?:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

Other than a possiblity of grub error 18, I'm not sure what the problem might be...

Added:  If you haven't already seen this thread, it may help:
[http://ubuntuforums.org/showthread.php?t=761817&highlight=success+external](http://ubuntuforums.org/showthread.php?t=761817&highlight=success+external)

---

### Post by Pumalite on 2008-05-09
This is good reading:
[http://ubuntuforums.org/showthread.php?t=678146](http://ubuntuforums.org/showthread.php?t=678146)
[http://ww.ubuntuforums.org/showthread.php?t=747263](http://ww.ubuntuforums.org/showthread.php?t=747263)

---

### Post by FusiveResonance on 2008-05-09
My laptop is not old. Fairly new (8 mos.) and does support booting off an external otherwise i wouldnt have gotten so far. 

I tried changing the boot priority of the drives in my HDD as suggested by the error 17 link posted above, but that simply causes my internal to boot first. 

Whats going on here. I'm quickly losing motivation and linux will soon be history. ****

help. thanks

---

### Post by confused57 on 2008-05-09
> **FusiveResonance said:**
> My laptop is not old. Fairly new (8 mos.) and does support booting off an external otherwise i wouldnt have gotten so far. 

I tried changing the boot priority of the drives in my HDD as suggested by the error 17 link posted above, but that simply causes my internal to boot first. 

Whats going on here. I'm quickly losing motivation and linux will soon be history. ****

help. thanks

No, it's not a bios limitation...you might want to try reinstalling with the howto I provided earlier:
[http://ubuntuforums.org/showthread.php?t=761817&highlight=success+external](http://ubuntuforums.org/showthread.php?t=761817&highlight=success+external)

You might want to consider installing Ubuntu on your internal hard drive & use EasyBCD to boot Ubuntu from Vista's bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by dstew on 2008-05-09
It is possible that your BIOS changes its disk enumeration depending on the boot order. If this is the case, when you boot from the CD and install grub, maybe the external disk is (hd1), but when you boot the external disk directly, it becomes (hd0), and the internal disk becomes (hd1). If that happens, since the grub stage1.5 is looking for an ext3 file system in (hd1,4), it might find the NTFS system of /dev/sda5 instead, and give the error.

---

### Post by Pumalite on 2008-05-09
That's why I asked earlier if he could boot Windows.(without the external attached)

---

### Post by FusiveResonance on 2008-05-10
Thats right, you did ask earlier. Unfortunately though, i cannot test that behavior as i don't even get a chance to see the grub menu. I immediately see the 1.5 jazz and then grub error 17. Even the super grub disk that im using is not able to boot linux. Perhaps im using the SGD wrong then?

Help
Thanks.

---

### Post by Pumalite on 2008-05-10
Disconnect your external drive. Boot Super Grub. Fix your Windows MBR. Reinstall, but this time with the internal disconnected if possible.

---

### Post by FusiveResonance on 2008-05-10
Is it necessary to fix my windows MBR? My mbr is fine i think, cuz  when i start up w/o the external connected, it boots straight into windows. 

I might try what you said regarding the re-install w/ the internal disconnected.

---

### Post by Pumalite on 2008-05-10
Good luck.

---

### Post by Majiq on 2008-05-12
It sounds to me like the problem is that you don't have the right modules loaded for the initial ram file system (initramfs). Following the directions on this page [http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/](http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/) this is what you should do.


1. Boot from a live cd; you only need a command prompt and a text editor.


2. chroot into your filesystem. From the looks of it, the code will probably be something like ```
chroot /media/sdb5
```


3. Edit the /etc/initramfs-tools/modules using your favorite editor (nano's easy) or just using bash commands and redirection which I prefer 
```
cd /etc/initramfs-tools/
echo -e "ehci-hcd\nusb-storage\nscsi_mod\nsd_mod" >> modules
```
This appends the following lines to the modules file:
```
ehci-hcd
usb-storage
scsi-mod
sd_mod
```


4. Edit the /etc/initramfs-tools/initramfs.conf to make sure that everything can load before it tries to do anything. What this line does is add in WAIT=12 at the first line of the intramfs.conf file.
```

cd /etc/initramfs-tools/
sed -i -e'1 s/^/WAIT=12\n/' initramfs.conf
```


5. Recompile the initial ram file system. In the example from the webpage it's
```

mkinitramfs -o /boot/initrd.img-2.6.17-10-386 /lib/modules/2.6.17-10-386
```
For me it's ```
mkinitramfs -o /boot/initrd.img-2.6.24-16-generic /lib/modules/2.6.24-16-generic/
```
For you, it'll be easiest to use TAB to complete filenames or if TAB completion isn't working, ls the /lib/modules folder and use that number that you see (it's just your kernel)


After this, you should be good insofar as the error 17 goes. I just skimmed over the replies since your first one. Make sure you've changed the menu.lst to root (hd0, 4), otherwise you'll get stuck at the next point. Do know that you can change this line at the boot menu, though, so getting to the menu is really the key.


Also, if you really want to be able to get to windows with your external plugged in, make sure you have this after the root line in your menu.lst for each of the windows boots only.
```
map (hd0) (hd1)
map (hd1) (hd0)
```
The problem this fixes is that Windows has to be on your primary drive.


If this doesn't work, let me know.

EDIT:
Also let me know if it does.

---

