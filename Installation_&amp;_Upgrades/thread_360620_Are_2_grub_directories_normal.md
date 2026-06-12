---
title: "Are 2 grub directories normal?"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by frafu on 2007-02-13
Hello, 

I have a celeronbox with 2 ide and 1 sata harddisks. 

The ide harddisks don't have any OS. 

The sata harddisk has ubuntu 6.06 on one partition and ubuntu 6.10 on a second partition. 

Further, there is a grub directory in ubuntu 6.06 and another grub directory in ubuntu 6.10. Is it normal to have 2 grub directories? 

I am asking because there is a strange behaviour: 
When the kernel in Ubuntu 6.10 gets updated, the menu.lst of ubuntu 6.06 receives the entries for the new kernel. However, when the computer boots, it reads the menu.lst from 6.10,because it still boots from the old kernel until I manually edit the menu.lst from ubuntu 6.10.

By the way, is there any utility that can read the boot sectors of all installed harddisks and partitions and that tells the user how many it has found, where they are and where they point to? Maybe a second grub directory was created during the installation of ubuntu 6.10, because I changed the boot order of the harddisks in the bios of the celeronbox!? (However I don't remember exactly when I changed the boot order; maybe between the installation of ubuntu 6.06 and 6.10.) 

Thanks in advance for any explanation and help. 

Francesco 

PS: The celeronbox is usually headless. However in a few days I am probably connecting it to a monitor for a few hours; so I might use that opportunity to fix the menu.lst problem...

---

### Post by frafu on 2007-02-15
Hello,

Maybe I should try another approach to get help: 

When I install to copies of Ubuntu onto one computer; each copy of Ubuntu having of course its own partition. 

Will there be by default a grub directory in each partition? 

Francesco

---

### Post by confused57 on 2007-02-15
> **frafu said:**
> Hello,

Maybe I should try another approach to get help: 

When I install to copies of Ubuntu onto one computer; each copy of Ubuntu having of course its own partition. 

Will there be by default a grub directory in each partition? 

Francesco
You might want to open a terminal(from Dapper?)...(Applications---Accessories---Terminal), post the output of these commands:
```
sudo fdisk -l
```
The -l is a small "L"

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list
you just need to post the entries to boot Ubuntu

I suppose it's possible that you also have grub installed to the root partition of Edgy, that may account for a 2nd grub menu when you boot to it.

---

### Post by frafu on 2007-02-15
Thanks for your reply. 

```
 
frafum@UbuntuDesktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       36481   293033601   83  Linux

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666   83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1570    12610993+  83  Linux
/dev/sda2           38595       38913     2562367+   5  Extended
/dev/sda3            1571        4757    25599577+  83  Linux
/dev/sda4            4758       38594   271795702+  83  Linux
/dev/sda5           38595       38913     2562336   82  Linux swap / Solaris

Partition table entries are not in disk order
frafum@UbuntuDesktop:~$ 

``` 

Why is there a "*"  only next to sda1 which contains Dapper? 
As sda3 contains edgy, should it not also have an "*"? 

Edgy is the main system; in fact, when I installed the computer I thought it would be a good idea to have a second system on the computer as fallback, especially because I am using it headless. 

Here is menu.lst on sda1:
```

# menu.lst on sda1
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
# myEdit: sda1 contains ubuntu dapper
# myEdit: sda2 is an extended partition containing the swap on sda5
# myEdit: sda3 contains ubuntu edgy
default		0

fallback 10

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash access=m1

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

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		-- Operating Systems-- This is menu.lst on sda1
root


title		MediaServer, kernel 2.6.15-27-386 on sda1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash access=m1
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		MediaServer, kernel 2.6.15-27-386 on sda1 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		MemoryTest, memtest86+ boot from sda1
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

```

Here is menu.lst on sda3:
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

fallback 10

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
# kopt=root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro

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

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		-- Operating systems -- menu.lst on sda3
root

title		MediaServer, kernel 2.6.15-27-386 on sda1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash access=m1
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		MediaServer, kernel 2.6.15-27-386 on sda1 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

```



I am suspecting that the problem arose because I once changed the boot order in the bios. 

>  
you just need to post the entries to boot Ubuntu
 

I don't understand what you mean. 

Anyway, I can boot to dapper and edgy without a problem. However there are weird things going on (a kernel update in edgy altering menu.lst in dapper (afterwards I edit menu.lst from edgy manualy)), which I will try to fix the next time I connect the computer to a monitor. 

> 
I suppose it's possible that you also have grub installed to the root partition of Edgy, that may account for a 2nd grub menu when you boot to it.


Indeed; there is also grub in edgy as I already told. Based on your remark, I suppose that it is not normal.

Francesco

---

### Post by confused57 on 2007-02-15
I must admit, this is something I've never seen before...I'll have to think about this, I don't want to try to suggest something that may affect your system adversely...may have to enlist the expertise of Herman, a member of the forum and he may be able to sort out a solution.
Here's his website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
he has an entire section devoted to grub

I'm glad you posted your entire menu.lst for both sda1 & sda3...because on your menu.lst on sda1(for Dapper), I would have expected the entries at the end of the file would between the lines ###BEGIN AUTOMAGIC... and ###END DEBIAN...and the kernel entries that are now between the above lines would be at the bottom of the file.

If you look at the lines in your sda1 menu.lst:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```

and the same lines in your sda3 menu.lst:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)
```
The kopt & groot lines are correct for Dapper & Edgy in both, but the kernel entries in your Dapper menu.lst are "reversed" from what I would have expected.

When there's a kernel update, update-grub is automatically run to add the new kernels to your menu.lst, between the "###BEGIN...and ###END" lines.

I honestly don't know what happened here, you might want to send a Private Message to Herman to see if he has any ideas...just give him a link to this thread, I'd like to see what he thinks.  He's pretty busy, so it may take a day or two for him to respond.

---

### Post by frafu on 2007-02-15
I must admit that I fiddled around in both menu.lst. However, don't ask me to tell you exactly what I did; it lies several months back... 

For example, I remember that originaly, in one menu.lst the entries were not (hd0,x), but (hd2,x). I also remember changing the groot parameter. I once also edited the device.map, but I think that afterwards I put it back to its original state. 

At the moment, I don't have time to contact Herman; I will probably do it tomorrow. 

Maybe, the best solution is to do a fresh install. But for my information: there should have been only one grub on the computer; or am I wrong? 


I have to leave now. 

Have a nice day. 

Francesco

---

### Post by confused57 on 2007-02-15
Rather than reinstall, boot up the live cd & (re)install Edgy's grub to the mbr(since that's your main OS)just to make sure Edgy's grub is on the mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Using the above link:
```
find /boot/grub/stage1
```
should show:
```
root (hd0,0)
root (hd0,2)
```

to install Edgy's grub to the mbr:
```
root (hd0,2)
setup (hd0)
```

Boot into Dapper:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
to make a backup...
then edit your Dapper grub, so that the entries at the bottom(for Dapper) are within the ###BEGIN AUTOMAGIC... & ###END DEBIAN AUTOMAGIC... section and your Edgy entries are below the ###END DEBIAN AUTOMAGIC... line.

THEN, reboot back into Dapper & then to Edgy to make sure both are booting OK, especially Dapper...out of curiosity you might want to add this entry at the very end of your Edgy menu.lst:
```
title   Dapper
rootnoverify  (hd0,0)
chainloader +1
```

if this entry boots Dapper, then you indeed have a copy of grub on your Dapper root partition.

Reinstalling may be easier than doing any of the above, which may not work anyway...the suggestions I've offered will take some effort...

Maybe a Dapper menu.lst change to this section similar to this:
```

## ## End Default Options ##

title		MediaServer, kernel 2.6.15-27-386 on sda1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash access=m1
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		MediaServer, kernel 2.6.15-27-386 on sda1 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

###END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=f3dafecc-568c-4c2a-8426-0f8c13506a56 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot
```

I'm wondering if initially that you installed Edgy's grub to Dapper's root partition, which "may" account for your current Dapper menu.lst.

---

### Post by frafu on 2007-02-16
Hello, 

Thanks again for your reply.

As I have not yet connected the monitor to the ubuntu computer (which is headless as you know and consequently I cannot see the grub-menu) I launched grub not by starting from the LiveCD, but from within dapper and edgy. Things seem even more messed up: 

```
 
when booted in dapper: 

grub> find /boot/grub/stage1
 (hd2,0)
 (hd2,2)

grub>


when booted in edgy: 

grub> find /boot/grub/stage1
 (hd2,0)
 (hd2,2)

grub> 


``` 


By the way: what is the purpose of the device.map? 

```
 
device.map on dapper:

(hd0)	/dev/sda
(hd1)	/dev/hda
(hd2)	/dev/hdb

but there is also a backup of the device.map on dapper; the backup contains the same as the device.map on edgy 


device map on edgy:

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda


``` 



I had to edit the menu.lst on dapper to make it boot into dapper; editing the default parameter in menu.lst from edgy did not have any effect. (As I am working remotely, I don't see the grub menu, to choose the kernel or OS; so I use the default parameter to choose what to boot.) 

But I think that I am understanding a little how it works. As I didn't boot into dapper for a few months, there were many updates available. There was also a kernel update in the queue. The update changed menu.lst on dapper; all the entries referring to edgy in the automatic section were gone and replaced with the kernel entries of dapper. 

Now I wonder what happens when there is a new kernel in edgy. Will the entry be added in the menu.lst of dapper below the automatic section? (In other words, below "### END DEBIAN AUTOMAGIC KERNELS LIST") 

I tried to remove the last kernel in edgy from the /boot directory and from menu.lst in dapper. I then booted again into edgy and did an update in the hope the last kernel would be downloaded again to see what would happen to the menu.lst on dapper. But it did not download it again. Maybe there is a command I can use in grub started in edgy to make it add the kernels present in edgy to menu.lst in dapper?

Tomorrow, I will probably connect a monitor to the ubuntu computer. 

Thanks again for your help. 

Francesco

---

### Post by frafu on 2007-02-16
Are these in the root directory of edgy normal? 

```
 
ls -al
... 
lrwxrwxrwx   1 root root    29 2007-02-09 19:32 initrd.img -> boot/initrd.img-2.6.17-11-386
lrwxrwxrwx   1 root root    29 2006-10-15 20:44 initrd.img.old -> boot/initrd.img-2.6.17-10-386
... 
lrwxrwxrwx   1 root root    26 2007-02-09 19:32 vmlinuz -> boot/vmlinuz-2.6.17-11-386
lrwxrwxrwx   1 root root    26 2006-10-15 20:44 vmlinuz.old -> boot/vmlinuz-2.6.17-10-386

```

---

### Post by confused57 on 2007-02-16
Here's an excellent tutorial for how grub works:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Anyone can correct me if I'm wrong, but your device.map is the hard drive boot order that is recognized by grub when you install Ubuntu...it appears that you had your OS drive as the 3rd boot hard drive(hd2) at that time and I assume you had to manually change the root entries in your menu.lst to boot when you selected to boot your SATA drive first.  There's a section in the link above that describes the device.map, if you are going to leave your system set this way, you might want to manually change your SATA drive to (hd0) in your device map for "find /boot/grub/stage1" to accurately display your root partitions.

The entries in your root directory are normal, they're just symlinks that point to the newest kernel and the next oldest.

Any kernel entries below the ###END DEBIAN AUTOMAGIC... line won't be changed when up-date grub is run, due to a kernel update.

Read over the link I gave you, it explains how grub works much better than I ever could.  It's still "confusing" to me at times, but I'm starting to understand it a little better...you might consider "chainloading" to boot your Dapper partition, again there's an explanation in the link of the benefits of booting multiple Linux distros this way & a couple of other ways are described.

---

### Post by frafu on 2007-02-16
> **confused57 said:**
> Here's an excellent tutorial for how grub works:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I was just reading that page before I checked whether you had answered. 
:-)
I found it due to the link that you gave me in a previous post... 

>  
... if you are going to leave your system set this way, you might want to manually change your SATA drive to (hd0) in your device map for "find /boot/grub/stage1" to accurately display your root partitions.
 
In the device.map of dapper, the sata drive is set to (hd0); but the find command in grub in dapper nevertheless says  (hd2,x) instead of (hd0,x). 

>  
The entries in your root directory are normal, they're just symlinks that point to the newest kernel and the next oldest.
 
In fact, I have just read on the page that you gave me above, that they can be used for booting multiple linuxes. 

>  
... you might consider "chainloading" to boot your Dapper partition, again there's an explanation in the link of the benefits of booting multiple Linux distros this way & a couple of other ways are described.

Again, thank you very much for the help. I will continue reading that page now... 

Francesco

---

### Post by frafu on 2007-02-16
> **frafu said:**
> 
In the device.map of dapper, the sata drive is set to (hd0); but the find command in grub in dapper nevertheless says  (hd2,x) instead of (hd0,x). 


It is probably due to the following bug: 
[https://launchpad.net/ubuntu/+source/grub/+bug/8497](https://launchpad.net/ubuntu/+source/grub/+bug/8497)

---

### Post by confused57 on 2007-02-16
> **frafu said:**
> It is probably due to the following bug: 
[https://launchpad.net/ubuntu/+source/grub/+bug/8497](https://launchpad.net/ubuntu/+source/grub/+bug/8497)

That's interesting, thanks...may very well be what's happening on your system...I had based my suggestion to manually change your device.map from Herman's grub page...which   had worked for someone else.   Learn something new every day.

I believe you're close to getting it, reading Herman's grub page, as well as other sections from his homepage...should answer any questions & give you some excellent guidance for configuring your bootloader files.

Added: Thanks for letting me know how things went, glad you were able to get everything working to your satisfaction...you caught on very quickly for getting your grub issues configured correctly.

---

### Post by frafu on 2007-02-21
Hello confused57, 

Sorry for replying so late. I would only like to inform you that I have finished with setting up my 2 ubuntu instances and grubs ([http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)), and thank you again for your help. 

Have a nice day. 

Francesco

---

