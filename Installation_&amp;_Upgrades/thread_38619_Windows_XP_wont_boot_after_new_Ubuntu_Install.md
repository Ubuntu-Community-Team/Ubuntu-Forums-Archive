---
title: "Windows XP wont boot after new Ubuntu Install"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by jamberu on 2005-06-01
I did a quick search to see if anything like this had been posted before but I couldn't find anything to here goes.

Ive just install a copy of Ubuntu on my laptop, its dual booting with windows xp professional. I can boot into Ubuntu fine from Grub the trouble is when I select windows it goes to the boot screen (the one with the bar that moves left to right) but then resets itself straight away :(

I can mount the windows partition in Linux so the files are still there, I really have no idea what to do.

Thanks in advance for any help,

Duncan


This is the output from fdisk:

duncan@Duncan:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3570    28675993+   7  HPFS/NTFS
/dev/hda2            3571        4807     9936202+  83  Linux
/dev/hda3            4808        4864      457852+   5  Extended
/dev/hda5            4808        4864      457821   82  Linux swap / Solaris#




This is my current Grub menu.lst file:


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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mingus on 2005-06-01
Duncan,

First, several questions:

When you did the Ubuntu install, did you have it modify the Windows partition in *any*  way?

Is the Windows partition NTFS?

Have you/do you know how to, verify that Windows is still bootable without going thru GRUB (that is, a direct boot like you had before)?

---

### Post by jamberu on 2005-06-01
Hi,

Thanks for the reply. Before I had fedora core 3 installed dual boot (Both the windows and Linux boots worked fine) and I decided that I wanted to try Ubuntu. I just used the Ubuntu installation to delete the fedora partitions and allowed it to overwrite the MBR. I didn’t make any changed to the Windows parition

Yep the Windows partition is NTFS.

Sorry I’m not sure how to do a direct boot, I thought after installing grub there was no way around it.

Thanks again,

Duncan

---

### Post by mingus on 2005-06-01
Yes, I have a big gripe with the Ubuntu installation not giving a clear alternative to loading GRUB in the MBR.  I know they want to keep this simple, but if a problem like yours arises, the user is frequently stuck.

First, if you want to make sure there is no problem with Windows, you'll need to boot it directly.  I couldn't seen anything wrong with the chain loader syntax in menu.lst, and your device.map is OK, right?  (Did you use GRUB with Fedora?).

Before you try the the step below, it is critical that you create an alternative booter for Ubuntu, or youll have trouble getting back in.  Get into Ubuntu, go to /boot/grub, and make sure that your floppy is defined in device.map.  Then do a #grub-install /dev/fd0 and this will write grub to the floppy.  If you wish, also do a #grub-install /dev/hdaX where X is the partition where /boot resides (depending on how you intalled, either its own or shared with /).  You now will be able to boot to Ubuntu from floppy, or if needed down the road, boot to Ubuntu from the Windows ntldr.

Now all you need to do is take a W2K or XP CD, or a W98 boot diskette, or create a boot diskette from any W2K/XP installation (instructions on support.microsoft.com) , and boot from it.  The diskettes will drop you into a command prompt, the CD you need to navigate to recovery mode, and there a prompt.  Then do >fixmbr, and this will restore the Windows MBR.  You can then re-boot and verify Windows is OK.

If it doesn't boot, we go from there.  If it does, there may be a problem somewhere with the boot loader.  Your GRUB floppy should chain-load the Windows boot, so that would be your next test.  When running GRUB, you can also break out into interactive mode, and enter the commands directly.  This can be useful so trap GRUB error messages.  If GRUB still can't get you to Windows, I would get back into Ubuntu, install LILO, modify lilo.conf to chain-load Windows (diff syntax), and then create another floppy to test this with.

BTW, if it comes to re-installing Ubuntu for any reason, the install docm indicates that you can choose LILO over GRUB and that install branch will give you the option of creating a floppy or installing to the partition sector, bypassing the MBR.

Good luck.

---

### Post by mingus on 2005-06-01
Sorry, neglected to mention . . . above presumes your BIOS can boot from CD or floppy.

---

### Post by jamberu on 2005-06-01
Thanks again for your help, hopefully I should be up and running soon! Just one thing my laptop doesn’t have a floppy, is there a way of writing to a cd? I tried simply with the command grub-install it wouldn’t let me.

Duncan

---

### Post by mingus on 2005-06-01
Nope.  My other pet gripe, "floppies are not longer necessary".  

Assuming then that you do have the XP bootable CD, and can restore the MBR, yes?

Install the boot loader to the partition boot sector.  Then setup Windows to dual-boot into Ubuntu.  I think there us a wiki entry on this, but there are plenty of other write-ups you can google for the details.  Been quite a while since I fooled with this, but don't remember it being difficult.

Alternatively, or if the prev step didn't work, you could try LILO.  Again, either chain loaded from ntldr as above or installed to the MBR, as long as you can again restore the Windows MBR if necessary.

This approach will enable you to test both GRUB and LILO, and test the partition boot sector method vs the MBR. 

--mingus

BTW, this is off your question . . . I don't know what you use for backup/recovery of Windows and that partition's data, but Window's built-in disaster recovery mechanism - ASR - only works with a floppy.

---

### Post by pdk001 on 2005-06-01
This is my current Grub menu.lst file:


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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

#title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

#title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

how about this method?

---

### Post by mingus on 2005-06-02
This says that your Ubuntu boot sector is located on the second partition and XP's is on the first partition that GRUB will chain-load (hand off to ntldr).  If you run grub-install the loader will be placed in the MBR (your only alt, since no floppy).

Were you able to boot Windows after doing >fixmbr?

---

