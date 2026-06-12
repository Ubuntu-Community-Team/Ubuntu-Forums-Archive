---
title: "Cannot Boot Windows Vista"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Vaio_User on 2008-05-16
I thought that setting a partition it allows you to be able to use both ubuntu and vista until I finally rebooted and I lost Vista. My computer always boots ubuntu. Is there any way I can get vista back? even if it means having to delete ubuntu.

---

### Post by iaculallad on 2008-05-16
Lost vista? how? Did you re-partition you're drive? What partition option did you choose when installing your Ubuntu? (Is it manual, or use the entire disk)

---

### Post by Vaio_User on 2008-05-16
Neither, I used what came up and I moved the little switch and now vista doesn't boot any more.

---

### Post by iaculallad on 2008-05-16
If you are already logged in your Ubuntu, do post the content which shows up after entering this command at the terminal:

sudo fdisk -l

---

### Post by Vaio_User on 2008-05-16
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16645   133700931    7  HPFS/NTFS
/dev/sda2           29489       30401     7333672+   7  HPFS/NTFS
/dev/sda3           16646       29488   103161397+   5  Extended
/dev/sda5           16646       29114   100157211   83  Linux
/dev/sda6           29115       29488     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by iaculallad on 2008-05-16
> **Vaio_User said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16645   133700931    7  HPFS/NTFS
/dev/sda2           29489       30401     7333672+   7  HPFS/NTFS
/dev/sda3           16646       29488   103161397+   5  Extended
/dev/sda5           16646       29114   100157211   83  Linux
/dev/sda6           29115       29488     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Post the content of your menu.lst

sudo gedit /boot/grub/menu.lst

---

### Post by Ericyzfr1 on 2008-05-16
During the install did you see an option to select another OS to boot on your PC?

---

### Post by Vaio_User on 2008-05-16
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
# kopt=root=UUID=2b450f1e-bcf5-47df-93e7-341d6f085417 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b450f1e-bcf5-47df-93e7-341d6f085417 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b450f1e-bcf5-47df-93e7-341d6f085417 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Vaio_User on 2008-05-16
No, I don't belive I did see that option. Is it the part where you choose how much space you are going to give to ubuntu and how much you will leave for vista?

---

### Post by iaculallad on 2008-05-16
Try editing/commenting (place the hash sign) this part on your menu.lst then restart your PC.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root(hd0,1)
savedefault
makeactive
chainloader

Seems like your grub menu is loading two vista entry.

Make sure to create a backup first.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

---

### Post by Vaio_User on 2008-05-16
I menu.lst isn't opening

---

### Post by iaculallad on 2008-05-16
> **Vaio_User said:**
> I menu.lst isn't opening

On your terminal: Applications->Accesories->Terminal:

sudo gedit /boot/grub/menu.lst

Be sure to backup it first before editing.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

---

### Post by Vaio_User on 2008-05-16
alright. now, where do I add the hash mark?

---

### Post by iaculallad on 2008-05-16
> **Vaio_User said:**
> alright. now, where do I add the hash mark?

On the last part of your menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
# title Windows Vista/Longhorn (loader)
# root (hd0,1)
# savedefault
# makeactive
# chainloader +1 

Then restart your PC

---

### Post by Vaio_User on 2008-05-16
I'm sorry, I'm having a little trouble following you on this.
If you can, can you show me where to put it on here?
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by iaculallad on 2008-05-16
> **Vaio_User said:**
> I'm sorry, I'm having a little trouble following you on this.
If you can, can you show me where to put it on here?
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

I had already commented the part. Remove first the existing texts on your menu.lst then Copy and Paste the texts below on your menu.lst. Just be sure that you created your backup. 

#-------------Copy from this Part and Paste it -------------
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2b450f1e-bcf5-47df-93e7-341d6f085417 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2b450f1e-bcf5-47df-93e7-341d6f085417 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2b450f1e-bcf5-47df-93e7-341d6f085417 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title Windows Vista/Longhorn (loader)
#root (hd0,1)
#savedefault
#makeactive
#chainloader +1
#--------------------------End Part ------------------

---

### Post by Vaio_User on 2008-05-16
Well, here goes.

---

### Post by Vaio_User on 2008-05-16
I restarted it and is it supposed to go to windows?

---

### Post by tommcd on 2008-05-16
> **Vaio_User said:**
> I restarted it and is it supposed to go to windows?

Grub will boot Ubuntu by default. To boot Vista (or any other operating system) you will have to scroll down to the entry for Vista with the arrow keys to select the Vista entry, then press the enter key.
Do you see a listing for Vista on the grub menu when you boot up your PC?

---

### Post by Roberticus on 2008-05-16
> **iaculallad said:**
> 
Seems like your grub menu is loading two vista entry.

One entry is for Vista and the other one is for Vista Recovery (D2D recovery Partition by eg. Acer).

Or at least it is like that for me :)

But when the GRUB menu shows up, choose the 
"# on /dev/sda2
title Windows Vista/Longhorn (loader)" (Second Entry)
To Boot up Vista.

Or when you need to recover vista, use:
"# on /dev/sda1
title Windows Vista/Longhorn (loader)" (First Entry)

---

