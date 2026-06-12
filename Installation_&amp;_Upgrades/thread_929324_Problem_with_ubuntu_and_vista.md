---
title: "Problem with ubuntu and vista"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by milosh012 on 2008-09-24
I installed Ubuntu on a new partition on my N200 Lenovo yesterday, and have some problems about booting to vista.

I used Disk Manager in Vista to resize my C: Vista OS to create linux partition. Before installing Ubuntu hdd look like this:

[-R-][---------------------------C------------------------][--------D------]

R = Vista Recovery partition, Primary & Hidden
C = Vista OS, Primary,
D = freed space

Then I installed Ubuntu on the freed space. Now, i cant run my Vista. in boot screen (grub loader) it says:

1-Ubuntu 
2-Ubuntu (recovery mode)
3-Ubuntu memtest
Other operating systems:
4-Windows Vista/Longhorn (loader)

when i select (4) for login i get recovery screen... what happened to my vista? can i do restore to factory settings and keep linux partition anyway? or there is another way to keep my linux safe!? its important to me not to lose linux...

one more thing.. in ubuntu i cant mount my C partition where is Vista instaled!

i hope that someone will help me...
thx

---

### Post by lian1238 on 2008-09-25
Open up gparted if you have it (system->admin->partition editor) and remember the partition of C drive - for example /dev/sda1

Then when you boot, go to the 4th line (vista) and press e for edit. Then edit the partition to be /dev/sdaX, where X is the number you remembered from gparted. Press b to boot.

---

### Post by rconwayarl on 2008-09-25
Dual boot to Vista always comes up in Windows SAFE MODE. This makes Vista almost useless. New Ubuntu wantabee needs Help !!

---

### Post by lian1238 on 2008-09-25
> **rconwayarl said:**
> Dual boot to Vista always comes up in Windows SAFE MODE. This makes Vista almost useless. New Ubuntu wantabee needs Help !!
Ubuntu doesn't seem to be the cause here. Try holding down F12 while booting Vista and see if you could choose the normal mode.

**milosh012**, if you could boot into Vista and want to make the change permanent, you need to edit the file '/boot/grub/menu.lst'.

---

### Post by WWSmith36 on 2008-09-25
Please post output of 

```
sudo -fdisk -l
cat /boot/grub/menu.lst
```

Thank you

---

### Post by milosh012 on 2008-09-25
> **lian1238 said:**
> Ubuntu doesn't seem to be the cause here. Try holding down F12 while booting Vista and see if you could choose the normal mode.

**milosh012**, if you could boot into Vista and want to make the change permanent, you need to edit the file '/boot/grub/menu.lst'.

Holding F12 didnt help! Again "Lenovo Rescue Center" is running, but not Vista...

---

### Post by milosh012 on 2008-09-25
> **lian1238 said:**
> Open up gparted if you have it (system->admin->partition editor) and remember the partition of C drive - for example /dev/sda1

Then when you boot, go to the 4th line (vista) and press e for edit. Then edit the partition to be /dev/sdaX, where X is the number you remembered from gparted. Press b to boot.

When i pres e GRUB shows me screen:
root (hd0,0)
savedefault
makeactiv
chainloader +1

i had edit the 1st line, and write like u say /dev/sda2 (my is sda2), than enter, and b.. and computer has restart and it shows again the same screen...

in gparted boot flag has my C partition (recovery partition)! is that a problem... should it say D partiton there(where i have installed Vista)?

---

### Post by milosh012 on 2008-09-25
> **WWSmith36 said:**
> Please post output of 

```
sudo -fdisk -l
cat /boot/grub/menu.lst
```

Thank you

***sudo -fdisk -l

sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

***cat /boot/grub/menu.lst

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
# kopt=root=UUID=c29ac566-d4a6-4cca-a572-15a94e16c680 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c29ac566-d4a6-4cca-a572-15a94e16c680 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c29ac566-d4a6-4cca-a572-15a94e16c680 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
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
makeactive
chainloader	+1

---

### Post by milosh012 on 2008-09-25
Does anybody have any idea? :(

---

### Post by firewire7 on 2008-09-25
Well this may be a little off topic but I just saw some guy saying that Ubuntu sucks and that Vista is so much better and he would debate anyone on it. Does anyone want to take this guy on? [http://www.axethem.com/technology/why-ubuntu-still-sucks/](http://www.axethem.com/technology/why-ubuntu-still-sucks/)

---

### Post by Mark Phelps on 2008-09-25
I did almost exactly the same process with a laptop containing Vista, let GRUB be installed to the MBR, and it works fine. 

Your menu.lst file looks fine; nothing wrong with it.

Do the "sudo fdisk -l" command but this time, without the "-" in front of the "fdisk".  And post the results here.

To do a Vista system repair, you will need a Vista DVD, or you will need to have made a recovery DVD.  Do you have either of those?

Word of caution -- do NOT plan to update your Vista files from inside Ubuntu.  The standard NTFS packages don't work well with Vista; only NTFS-3G does -- and you have to enable that.

---

### Post by milosh012 on 2008-09-25
> **Mark Phelps said:**
> I did almost exactly the same process with a laptop containing Vista, let GRUB be installed to the MBR, and it works fine. 

Your menu.lst file looks fine; nothing wrong with it.

Do the "sudo fdisk -l" command but this time, without the "-" in front of the "fdisk".  And post the results here.

To do a Vista system repair, you will need a Vista DVD, or you will need to have made a recovery DVD.  Do you have either of those?

Word of caution -- do NOT plan to update your Vista files from inside Ubuntu.  The standard NTFS packages don't work well with Vista; only NTFS-3G does -- and you have to enable that.


it says:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf47f98ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         880     7066624   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             880       15416   116754625    7  HPFS/NTFS
/dev/sda3           15417       19335    31479367+  83  Linux
/dev/sda4           19336       19457      979965   82  Linux swap / Solaris


sda1 is recovery partition
sda2 is where is vista installed
sda3 Linux
sda4 swap for linux

I dont have Vista DVD, but i have that "recovery partition" which contains that Vista and lenovo software... the only option that i can do from that partition is to back all to factory settings. but that will destroy my linux? or not?

---

### Post by caljohnsmith on 2008-09-25
Since Vista is on the second partition, you need to change your entry for Vista in your menu.lst to:
```
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1
```
To do that, open menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
You might have more problems though other then your Grub's menu.lst entry being incorrect, but start with that, and tell us exactly what happens after you select it on start up.

---

### Post by milosh012 on 2008-09-25
> **caljohnsmith said:**
> Since Vista is on the second partition, you need to change your entry for Vista in your menu.lst to:
```
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1
```
To do that, open menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
You might have more problems though other then your Grub's menu.lst entry being incorrect, but start with that, and tell us exactly what happens after you select it on start up.

o my god! it works! Thank you man!

---

### Post by caljohnsmith on 2008-09-25
> **milosh012 said:**
> o my god! it works! Thank you man!
You're welcome--I'm glad it was that easy. Cheers and have fun. :)

---

