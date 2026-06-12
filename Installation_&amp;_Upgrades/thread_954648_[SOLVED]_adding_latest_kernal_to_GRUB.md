---
title: "[SOLVED] adding latest kernal to GRUB"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2008-10-21
I installed HH from a purchased DVD and applied all updates. I have Suse 10.0 on the first drive and HH on the second and made an entry for Suse in my GRUB menu. after a vacation I installed all the waiting updates which included a new kernal. I kept my old menu so I would not lose my Suse entry.
How do I go about adding the new kernal to GRUB?
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      224909      112423+  83  Linux
/dev/sda2          224910     2329424     1052257+  82  Linux swap / Solaris
/dev/sda3         2329425   156280319    76975447+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000abcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   150288074    75144006   83  Linux
/dev/sdb2       150288075   156296384     3004155    5  Extended
/dev/sdb5       150288138   156296384     3004123+  82  Linux swap / Solaris
root@tommy1-desktop:~# 

```
```

## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Suse 10.0
root            (hd0,0)
configfile      /boot/grub/menu.lst

title           Ubuntu 8.04.1, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by Ptero-4 on 2008-10-21
Copy the /boot/grub/menu.lst file to your home and type
```
sudo update-grub
```
This makes grub re-read it's menu file, which adds the new kernel and an entry for your SuSE partition.

---

### Post by Tom Atkins on 2008-10-21
That did not work. I still only have .16 and .19 on the menu. The updates I did included .21 but it is not on the menu. I did not do the automatic changes because of the reason I gave in my original post.

---

### Post by caljohnsmith on 2008-10-21
Hi Tom, if you want to make sure your Suse entry does not get modified, you can either put it before the lines:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
Or you can put it after:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
Then you can use the "update-grub" command safely to update your Grub menu with new kernels while the Suse entry shouldn't be touched. To successfully use the update-grub command, make sure that at least the "groot" line uses (hd1,0), or your Ubuntu partition:
```
# groot=(hd1,0)
```
Even though it is "commented" with the pound sign, the update-grub script uses that line to know where your Ubuntu is located. Also, did you confirm by looking in your /boot directory that you have the new .21 kernel update? You can always manually add an entry for the new kernel with:
```
title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet
```
Let me know how it goes. :)

---

### Post by Tom Atkins on 2008-10-21
I saved the menu.lst file under menu.lst.save. I moved the Suse entry below  the DEBIAN markers. and saved the file. I reran the update grub and it still did not have the .21 listed.

Here is my /boot dir.
```

tommy1@tommy1-desktop:/boot$ ls
abi-2.6.24-16-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic             initrd.img-2.6.24-21-generic
abi-2.6.24-21-generic             initrd.img-2.6.24-21-generic.bak
config-2.6.24-16-generic          memtest86+.bin
config-2.6.24-19-generic          System.map-2.6.24-16-generic
config-2.6.24-21-generic          System.map-2.6.24-19-generic
grub                              System.map-2.6.24-21-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-21-generic
tommy1@tommy1-desktop:/boot$ 

```

---

### Post by caljohnsmith on 2008-10-21
OK, so you ran update-grub as root, i.e. "sudo update-grub"? How about posting the full contents of your menu.lst, because one of the options used by the update-grub script might be off. Also, can you post the output of running the sudo update-grub command?

---

### Post by Tom Atkins on 2008-10-21
here is the outout of update
```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


```
here is menu.lst
```


title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title           Suse 10.0
root            (hd0,0)
configfile      /boot/grub/menu.lst



^G Get Help               ^O WriteOut         

```

---

### Post by caljohnsmith on 2008-10-21
> **Tom Atkins said:**
> here is the outout of update
```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
[COLOR="Blue"]Found kernel: /boot/vmlinuz-2.6.24-21-generic[/COLOR]
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

According to the update-grub command above, it found your .21 kernel just fine. Are you sure you are posting the correct menu.lst? Please post the full output of:
```
cat /boot/grub/menu.lst
```

---

### Post by Tom Atkins on 2008-10-22
Here it is:
```

tommy1@tommy1-desktop:~$ cat /boot/grub/menu.lst
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
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title           Suse 10.0
root            (hd0,0)
configfile      /boot/grub/menu.lst

```

tommy1@tommy1-desktop:~$

---

### Post by caljohnsmith on 2008-10-22
That's really bizarre that the update-grub script found the new kernel, but it doesn't look like it updated the menu.lst. Try manually opening your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that has "# groot=(hd1,0)" to arbitrarily be:
```
# groot=(hd1,5)
```
Then run:
```
sudo update-grub
```
And look at the menu.lst to see if all the Ubuntu entries now use (hd1,5) instead of (hd1,0). If they don't change, then we will know that the update-grub script is for some reason not updating that menu.lst. Please also post the output of the update-grub command.

---

### Post by Tom Atkins on 2008-10-23
Here it is
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
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title           Suse 10.0
root            (hd0,0)
configfile      /boot/grub/menu.lst

```

As you can see it did not change.
I will reedit it to its previous entry, ie. hd1,0

Thanks for all your help!

---

### Post by caljohnsmith on 2008-10-23
Yes, that is really strange that update-grub didn't change the menu.lst. How about reinstalling Grub; note that it won't delete your menu.lst or Grub files in /boot/grub/, but maybe it will fix the problem with the update-grub command:
```
sudo apt-get purge grub
sudo apt-get install grub
```
Next post the output of:
```
ls -l /boot/grub
```
Where "-l" is a lowercase L. Then change the groot line in the menu.lst to (hd1,5) again and run:
```
sudo update-grub
```
And please post the output of the update-grub command. After that, check your menu.lst and let me know if the Ubuntu entries use (hd1,5).

---

### Post by Tom Atkins on 2008-10-23
That Worked !!!
it found .21, changed to hd0,5

I have changfed it basck to hd0,1 and everthing is ok

Thank you very much for your help.

I will mark this as solved

---

### Post by caljohnsmith on 2008-10-23
That's great news--glad that reinstalling Grub fixed the glitch. Cheers and have fun Ubuntu-ing. :)

---

