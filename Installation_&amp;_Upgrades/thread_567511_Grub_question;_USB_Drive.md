---
title: "Grub question; USB Drive"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by mitch2k2 on 2007-10-04
Hello all. I've got a bootable, lovable, wonderful gutsy installation on an external USB drive. Grub is installed on the USB drive, with the laptop set to boot from USB if it's there.

So all is well and good and I can boot into Ubuntu with no problem. Thing is, I installed another distro to a separate partition on that drive. I've tried editing the menu.lst file, but to no avail. Grub always balks at loading the second distro. 

The way I was able to get the USB installation to boot was by changing the HD1,0 in menu.lst, which the USB drive was designated as during install, to HD0,0, So logic followed (I thought) that the partition with the other distro would be HD0,1.

But that didn't work. I remembered that the swap partition sits between them and tried HD0,2 as well. No dice. 

Is there some simple way for me to get Ubuntu's grub loader to see and properly load this second distro, keeping grub solely on the USB drive?

---

### Post by meierfra on 2007-10-04
Please post the output of

```
sudo fdisk -l
```

and 

```
 cat /boot/grub/menu.lst 
```

(all l's are lower case L)

---

### Post by mitch2k2 on 2007-10-04
> **meierfra said:**
> Please post the output of

```
sudo fdisk -l
```
Here's the output of fdsik -l:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3936    31615888+   7  HPFS/NTFS
/dev/sda2            3937        9729    46532272+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x028e028d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1905    15301881   83  Linux
/dev/sdb2            3629        4864     9928170   83  Linux
/dev/sdb3   *        1906        2242     2706952+  82  Linux swap / Solaris

Partition table entries are not in disk order
```
The sdb partitions being, obviously, the USB in question (by the way, is it usual for a swap partition to be marked to boot?)

sdb1 is Gutsy, sdb2 is PCLinuxOS, which I can't boot into, which brings us to:
> and 

```
 cat /boot/grub/menu.lst 
```
Here's that: ```
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
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive    title Your New Operating System’s Name
    root (hd0,0)
    makeactive
    chainloader +1 


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
# kopt=root=UUID=ef9dce63-028f-4f2b-a45a-3c68bc8caa9a ro

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

title           Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=ef9dce63-028f-4f2b-a45a-3c68bc8caa9a ro quiet splash
initrd          /boot/initrd.img-2.6.22-12-generic
quiet

title           Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=ef9dce63-028f-4f2b-a45a-3c68bc8caa9a ro single
initrd          /boot/initrd.img-2.6.22-12-generic

title           Ubuntu gutsy (development branch), memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title           PCLinuxOS
root            (hd0,1)
kernel          /boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb2  acpi=on resume=/dev/sdb3 splash=silent vga=788
initrd          /boot/initrd.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```Any ideas? I appreciate the help.

---

### Post by meierfra on 2007-10-04
Edit: I misread your post and posted some nonsense.  I have to leave now but will be back later

---

### Post by meierfra on 2007-10-04
I don't see anything wrong with your menu.lst.  

Do you get any error messages when you try to boot PCLinuxOS?  

Try  mounting  sdb2 in Gutsy to see whether there are any problems with the sdb2 partition.

---

### Post by logos34 on 2007-10-04
You need to take the pclinuxos entry out of the Debian 'automagic' section and put it at the bottom (otherwise during the next kernel update Grub will eject it). 

Also, you forgot to change the '**groot**' line to (hd**0**,0)

Use the [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") or [chainloader]("http://docs.pclinuxos.com/Adding_PCLinuxOS_to_an_existing_GRUB") boot entry format:

> title           PCLinuxOS
configfile      (hd0,1)/boot/grub/menu.lst (or /boot/grub/**grub.conf**)

> title PCLinuxOS
rootnoverify (hd0,1) 
chainloader +1

---

### Post by dabl on 2007-10-04
The answer may be to "mount by UUID" -- i.e. to use the UUID numbers for the partitions on the USB drive, rather than the /dev/sdn numbers, which can change dynamically and cause trouble.  Likewise, substitute the UUID numbers in /boot/grub/menu.lst to point to the partition where the kernel(s) live.

Here's an example of my /etc/fstab file, using this method:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=b1869c3e-b13a-4772-914c-bcc6db718967 / reiserfs nouser,notail,noatime,auto,rw,dev,exec,suid 0 1
# /dev/sdb2
UUID=a6c2ba7b-8492-4746-92af-5182dcb4daab /home reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=f222f97f-278f-4db5-8642-513294f30193 /media/sda1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sda3
UUID=adf641ca-f64e-4311-bc30-86bfcdcb669c /media/sda3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc1
UUID=1ddd0144-0875-4667-9f98-e90a23f58ff3 /media/sdc1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc2
UUID=710efad8-9f97-4bcd-8f57-8f8cc1facc2f /media/sdc2 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc3
UUID=f1912a56-2e5c-45ce-b91b-3ebbe69e20f4 /media/sdc3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd1
UUID=cffddf89-57f3-40ab-a97f-40bb1ea45f16 /media/sdd1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd3
UUID=9b7658da-59e1-4b2b-a4b9-fa3ee11b68cf /media/sdd3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sde1
UUID=d182b7c3-298c-49b3-ac66-b378033b815c /media/sde1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd2
UUID=94d4d572-3581-491b-90dc-e5f619c65908 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
# /dev/sdf1
UUID=A8FC3435FC33FC5E /media/NTFSTICK ntfs-3g user,atime,rw,nodev,nosuid 0 0
```


Find the UUID numbers for the partitions on that USB drive by using ```
blkid
``` when the drive is mounted (I know, kind of a Catch-22 there). It also is listed in /dev/disk/by-id but it's a little tricky to figure out which UUID goes with which /dev/sdn partition.  You can also "label" the partitions, and there is a "mount by label" capability, but I haven't had a lot of success with it.

:)

---

### Post by mitch2k2 on 2007-10-04
> **logos34 said:**
> Also, you forgot to change the '**groot**' line to (hd**0**,0) That line was commented out, so I didn't touch it. Should I?

> Use the [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") or [chainloader]("http://docs.pclinuxos.com/Adding_PCLinuxOS_to_an_existing_GRUB") boot entry format:

Trying this now.

---

### Post by mitch2k2 on 2007-10-04
Okay, the chainloader option throws up an error (13, I think, but it could have been 21) in the grub loader, and sends me back to the menu. the UUID linked entry (below the Debian default so as not to get overwritten on upgrade) brings up the PCLinuxOS boot screen but then nothing - no activity whatsoever on screen or on the external drive. The boot screen just hangs, and the machine locks up; cant even CTRl-backspace or anything; only way out is to manually cut power and reboot (into Gutsy)

Could there be something in the boot folder on the PCLOS partition that I should be looking at?

---

### Post by logos34 on 2007-10-04
For the chainloader entry to work the pclinux os Grub must be written to the bootsector of the root partition (hd0,1).  

Did you try the configfile entry?

Post the pclinuxos menu.lst/grub.cfg file.

---

### Post by mitch2k2 on 2007-10-04
> **logos34 said:**
> Did you try the configfile entry? Yes, I did, and it did succeed in bringing up the PCLinuxOS boot menu, but the same thing happened when trying to boot from there (boot screen and nothing, no activity, no ESC into verbose mode, need to hard power down to get out). 

> Post the pclinuxos menu.lst/grub.cfg file.
Here 'tis:
```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,1)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title linux
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb2  acpi=on resume=/dev/sdb3 splash=silent vga=788
initrd (hd0,1)/boot/initrd.img

title linux-nonfb
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sdb2  acpi=on resume=/dev/sdb3
initrd (hd0,1)/boot/initrd.img

title failsafe
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sdb2  failsafe acpi=on resume=/dev/sdb3
initrd (hd0,1)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title windows1
root (hd1,1)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1
```
Anything jump out at you? It seems like it should be working (as far as I can tell), but it's not. I'm waiting for the inevitable 'A HA!' moment where I realize how stupid and blind to the obvious I've been and see the solution right in front of me.

---

### Post by logos34 on 2007-10-04
What's in your pclinuxos /boot folder?

**ls** /path/to/sda2**/boot**

I think vmlinuz and initrd.img should show the specific kernel, i.e.:

kernel (hd0,1)/boot/vmlinuz-2.6.<version>.mdk  ...
initrd (hd0,1)/boot/initrd-2.6.<version>.mdk.img  ...

---

### Post by mitch2k2 on 2007-10-05
> **logos34 said:**
> What's in your pclinuxos /boot folder?

**ls** /path/to/sda2**/boot**```
config                    kernel.h                System.map-2.6.18.8.tex5
config-2.6.18.8.tex5      kernel.h-2.6.18.8.tex5  us.klt
grub                      memtest-1.65.bin        vmlinuz
initrd-2.6.18.8.tex5.img  message-graphic         vmlinuz-2.6.18.8.tex5
initrd.img 
```   

> I think vmlinuz and initrd.img should show the specific kernel, i.e.:

kernel (hd0,1)/boot/vmlinuz-2.6.<version>.mdk  ...
initrd (hd0,1)/boot/initrd-2.6.<version>.mdk.img  ...

Should that change be made to Ubuntu's or PCOL's menu.lst file? Or both?

---

### Post by mitch2k2 on 2007-10-05
Well, I changed the PCLOS menu.lst (since the ubuntu grub points at that via the configfile entry) as suggested, but the same thing happens - PCLinux boot screen loads and then everything just stops. As I'd mentioned, I can't get into verbose mode to even see what's happening.

---

### Post by logos34 on 2007-10-05
If you subsituted these entries

vmlinuz-2.6.18.8.tex5
initrd-2.6.18.8.tex5.img 

in your pclinuxos menu.lst and still all you get is a blank screen, then I'm at a loss what to suggest next. Maybe there's one or more boot options you could add to the kernel line.  It's not (yet) a graphics problem because the boot process never gets that far.  It might be the kernel image and/or initrd is corrupted in some way.   

Double check your pclinuxos device.map file in /boot/grub...(hd0) should point to sdb and (hd1) to sda.

To answer an earlier question about groot line: yes, go ahead and change it...grub will read it despite the single '#' mark

---

### Post by mitch2k2 on 2007-10-05
Crazy busy at work, so have to stay in XP for at least the next several hours, but when I can get back to a moment of freedom I'll boot back in to Ubuntu and make those changes. 

And regardless, thanks so much for all your help. I really do appreciate it.

---

### Post by mitch2k2 on 2007-10-05
Changed the groot line and verified that the device map in PCOL was correct, but still no luck.

 It seems like it goes to the PCLinuxOS boot directory (it fetches the boot image from there) and then just stops. Could it have anything to do with the boot parameters in (both) menu.lst?
```
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb2  acpi=on resume=/dev/sdb3 splash=silent vga=788
```
Also, I noted early on in this process that fdisk -l showed the swap as boot:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1905    15301881   83  Linux
/dev/sdb2            3629        4864     9928170   83  Linux
/dev/sdb3   *        1906        2242     2706952+  82  Linux swap / Solaris
```
That seemed odd to me, but I just chalked it up to my ignorance. Might that have something to do with this boot problem?

---

### Post by mitch2k2 on 2007-10-05
Tried booting into the PCLOS live cd to rewrite the boot info to the PCLOS partition, thinking maybe that would help the Ubuntu grub find it, but neither configfile nor chainloader works.

---

### Post by mitch2k2 on 2007-10-05
Well, I've fixed it (for anyone who may have a similar issue). By changing the /dev/sdb2 to /dev/sda2 in the ubuntu grub, I've managed to load PCLOS from Ubuntu's grub. 

Now I just need it to inherit permissions on the local (non-usb) drive partitions on the laptop. and I'll be gold.

Thanks fo r all the help, y'all.

---

### Post by logos34 on 2007-10-05
> **mitch2k2 said:**
> By changing the /dev/sdb2 to /dev/sda2 in the ubuntu grub, I've managed to load PCLOS from Ubuntu's grub. 

Strange...I just don't understand that.  And I wish I knew why it won't chainload.  

Anyway, glad it's working for you now.    

Could you post the ubuntu grub entry?  Just curious.

> Now I just need it to inherit permissions on the local (non-usb) drive partitions on the laptop. and I'll be gold.

install ntfs-3g driver.  It'll give you r+w access to ntfs and edit your fstab so they automount with the correct permissions.

[B]sudo apt-get install ntfs-config

sudo ntfs-config[/B]

>enable write support internal devices

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by meierfra on 2007-10-05
>   And I wish I knew why it won't chainload.


Chain loading only works if grub is installed  in the PCLinux partition. 
And even if grub was install there,  it would use the PCLinux  "menu.lst", which contains the "sdb2" mistake.  For the same reason "configfile" did not work. 

> 
By changing the /dev/sdb2 to /dev/sda2 in the ubuntu grub, I've managed to load PCLOS from Ubuntu's grub.

If you want hibernation to work  you should also change "resume=/dev/sdb3"  to "resume=/dev/sda3"


Don't worry about the boot flag in the swap partition. It was set then you tried  to boot  (hd0,2). Grubs ignores it.  But if you want, you can use gparted to remove the boot  flag.

---

### Post by logos34 on 2007-10-05
> **meierfra said:**
> Chain loading only works if grub is installed  in the PCLinux partition. 
And even if grub was install there,  it would use the PCLinux  "menu.lst", which contains the "sdb2" mistake.  For the same reason "configfile" did not work. 

Well, mitch2k2 did write grub to the pxlinuxos partition.  So the question is *why* is it booting with root=/dev/sda2?  Fdisk is showing the opposite.  sdb is clearly hd0.

---

### Post by meierfra on 2007-10-05
> Well, mitch2k2 did write grub to the pxlinuxos partition. 

Probably true,  but I  can't find any place  mitch2k2 ever said so.


>  So the question is why is it booting with root=/dev/sda2? 

True, it caught me by surprise, too.  But maybe PCLinux has a different "fdisk -l" output?

So  mitch2k2   just to satisfy my curiosity, could  you post your "fdisk -l" from a PCLinux terminal?

---

### Post by mitch2k2 on 2007-10-05
> **meierfra said:**
> Probably true,  but I  can't find any place  mitch2k2 ever said so. I think I had the first time, and earlier this afetrnoon when I'd posted about using the PCLOS LiveCD to rewrite the bootloader, I did it again, for certainty.

As to the switching to sda from sdb, I stumbled across a post on the PCLOS forums where that worked for someone. So I tried it. Voila. One of the mysteries of the universe.

Now, the fdisk output is only showing the USB drive, and not the local drive. Not sure why, when both ntsf partitions are mounted and accessible to me in Ubuntu. > True, it caught be by surprise, too.  But maybe PCLinux has a different "fdisk -l" output?

So  mitch2k2   just to satisfy my curiosity, could  you post your "fdisk -l" from a PCLinux terminal?Gladly:

*Edited: misread your question and pasted Ubuntu's. After Ubuntu finishes updating I'll boot into PCLOS and show you what I find.*

So, yeah, according to fdisk and by all normal logic, this shouldn't work. But it has. Sort of like how you need to change HD1,0 to HD0,0 to get the external drive grub-bootable. Maybe the sd entries need to follow suit.

---

