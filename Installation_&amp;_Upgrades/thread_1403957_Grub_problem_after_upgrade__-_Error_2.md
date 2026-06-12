---
title: "Grub problem after upgrade  - Error 2"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by mlamberg on 2010-02-10
I'm currently running Ubuntu 8.04 LTS on an Intel Pentium 4 Dell desktop system. After performing a normal upgrade from 2.6.24-25-generic to 2.6.24-26-generic I now get "Error 2: Bad file or directory type" upon bootup. The grub menu pops up and I can manually boot the early version (-25) with no problem... I thought the problem might go away with the subsequent upgrade to 2.6.24.27-generic, but I get the same error, and I'm only able to manually boot into -25 or earlier version from the menu.. What are the steps I should be performing to diagnose and hopefully correct this issue.. Thanks for your help -Mike

---

### Post by meierfra. on 2010-02-10
Sometimes error 2 is caused by a corrupted kernel and you just have to reinstall the kernel.  But it's unlikely that two different kernels got corrupted.  So let's  have a better look at your setup. Follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

---

### Post by Kir_B on 2010-02-11
If you're new to linux, I don't know about the instructions on the boot info script. I'm fairly new to linux and have had a similar problem a couple of months ago. The thread that helped me is titled "[COLOR=#cc33cc][my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR]". I'm not positive that it will help you, but I think it will. Follow to the letter, the instructions given to me from "lmarmisa" and ignore every other post {except mine Kir_b}. He really saved my bacon and it might help you to, as it has helped many others.

---

### Post by meierfra. on 2010-02-11
> I'd have had a similar problem a couple of months ago. 
??????
What does a deleted menu.lst  has in common with Grub error 2?

---

### Post by Kir_B on 2010-02-11
> **meierfra. said:**
> ??????
What does a deleted menu.lst  has in common with Grub error 2?

I had error 15 after trying to upgrade my grub and I suspect that something similar has happened to you. Do you have a livecd? If you do, it's worth a try. It solved my problem and at the very least, you might have some valuable info to post on the forum, which might be very informative to those that might be able to help you.

                     Peace Kir_b

P.S. Please post the results of any help you've recieved, so that in the future, those with problems that resemble yours might quickly find something helpful, rather than reading 15 posts, only to be left without an answer as to just how helpful the instructions were.

---

### Post by meierfra. on 2010-02-11
> Do you have a livecd? 
???????
The OP is able to boot into Ubuntu, so there is no need boot into a LiveCD.

>  had error 15 after trying to upgrade my grub and I suspect that something similar has happened to you.

?????
What does Grub error 15 after trying to upgrade to Grub2 have to do with Grub error 2 after a kernel update?

---

### Post by lindsay7 on 2010-02-11
meierfra., knows what he is talking about. run the script like he says and post it. You will get help from there.

---

### Post by Kir_B on 2010-02-11
Sorry, I've got a lot going on right now. I didn't realize that you are able to boot into your system. My mistake.

Have you run the following code and if so, could you please post the results.

```
 sudo update-grub
```

---

### Post by Kir_B on 2010-02-11
A lot of people are having problems with the latest kernels and I thought for sure that you were also having this problem. sorry.

More info will undoubtedly get you more help.

                            Kir_b

---

### Post by Kir_B on 2010-02-11
It pays to read. Sorry, I had you confused with someone else that I was helping earlier.

I'm willing to bet that you are running grub legacy. If updating your grub doesn't solve your problem, either wait for someone that can help {I'm, by no means an expert}, or start a new thread with a very concise description of the problem.

I wish I could be of more help, but I can only relay my own experiences/solutions.

                           Kir_b

---

### Post by mlamberg on 2010-02-11
I appreciate everyones responses so far...  I will initially follow meierfra suggestion and post the result...  Just home from work, will hopefully take care of this in the next several hours....  Thanks....

---

### Post by mlamberg on 2010-02-11
Here is the Results.txt file using the instructions posted by meierfra...

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00060f45

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   622,117,124   622,117,062  83 Linux
/dev/sda2         622,117,125   625,137,344     3,020,220   5 Extended
/dev/sda5         622,117,188   625,137,344     3,020,157  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4095b3fe-f072-45ff-9ad9-8c19f032ef44   ext3                                     
/dev/sda5        98625c87-87e7-4582-b645-1cf97a810ab5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=98625c87-87e7-4582-b645-1cf97a810ab5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


Thank you for your help...

---

### Post by meierfra. on 2010-02-11
Did you post the whole RESULTS.txt?  The last little bit seems to be missing.

---

### Post by mlamberg on 2010-02-11
Yes, I just checked...  it ended with the /dev/fd0 line...  I'll run it again but it wont be till tomorrow evening...

---

### Post by meierfra. on 2010-02-12
> I'll run it again 
The missing information was caused by a bug in the boot info script. I tried to fix the bug. So download the script again before you run it.  If you still have the old RESULTS.txt, the new one will be called RESULTS1.txt.

Could you also check your Bios?  Does it report the size of your hard drive somewhere?  If yes, does it report it as 320GB or something else?

---

### Post by mlamberg on 2010-02-12
I re-ran the updated Boot Info_script, results below.. Also the bios does report the size of my hard drive correctly as 320G..  Thanks

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00060f45

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   622,117,124   622,117,062  83 Linux
/dev/sda2         622,117,125   625,137,344     3,020,220   5 Extended
/dev/sda5         622,117,188   625,137,344     3,020,157  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4095b3fe-f072-45ff-9ad9-8c19f032ef44   ext3                                     
/dev/sda5        98625c87-87e7-4582-b645-1cf97a810ab5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=98625c87-87e7-4582-b645-1cf97a810ab5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 132.3GB: boot/grub/menu.lst
  97.7GB: boot/grub/stage2
  97.8GB: boot/initrd.img-2.6.24-19-generic
  97.7GB: boot/initrd.img-2.6.24-19-generic.bak
  97.7GB: boot/initrd.img-2.6.24-23-generic
  97.8GB: boot/initrd.img-2.6.24-23-generic.bak
 108.0GB: boot/initrd.img-2.6.24-24-generic
 107.5GB: boot/initrd.img-2.6.24-24-generic.bak
 108.0GB: boot/initrd.img-2.6.24-25-generic
 108.0GB: boot/initrd.img-2.6.24-25-generic.bak
 137.5GB: boot/initrd.img-2.6.24-26-generic
 137.5GB: boot/initrd.img-2.6.24-26-generic.bak
 137.0GB: boot/initrd.img-2.6.24-27-generic
 137.5GB: boot/initrd.img-2.6.24-27-generic.bak
  97.7GB: boot/vmlinuz-2.6.24-19-generic
  97.8GB: boot/vmlinuz-2.6.24-23-generic
 103.8GB: boot/vmlinuz-2.6.24-24-generic
 103.8GB: boot/vmlinuz-2.6.24-25-generic
 137.0GB: boot/vmlinuz-2.6.24-26-generic
 137.4GB: boot/vmlinuz-2.6.24-27-generic
 137.0GB: initrd.img
 137.5GB: initrd.img.old
 137.4GB: vmlinuz
 137.0GB: vmlinuz.old
=============================== StdErr Messages: ===============================

blkid: invalid option -- p
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghl] [-o format] [-s <tag>] [-t <token>]
    [-v] [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)

```

---

### Post by meierfra. on 2010-02-12
```
  97.7GB: boot/vmlinuz-2.6.24-19-generic
  97.8GB: boot/vmlinuz-2.6.24-23-generic
 103.8GB: boot/vmlinuz-2.6.24-24-generic
 103.8GB: boot/vmlinuz-2.6.24-25-generic
 137.0GB: boot/vmlinuz-2.6.24-26-generic
 137.4GB: boot/vmlinuz-2.6.24-27-generic
```

Some bios are only able to read files on the first 137GB of your hard drive. Your two new kernels  are just outside that limit.  If your bios would have reported your hard drive as 137GB, we would  know for sure that its a bios problem.
You could google your bios and see whether there is a problem  with the 137GB limits.  You could also do  little experiment :


```
cd /boot
ker=vmlinuz-2.6.24-19-generic
sudo mv $ker $ker.bu
sudo cp  $ker.bu $ker

```

Run the boot_info_script
Your  "-19" kernel  now should be at 137GB or higher.
Reboot and try to boot from the -19 kernel. You should get "grub error 2".  Then we will know for sure that the problem is caused by the physical location of the kernel.

If it s really a bios problem,  you have the following options:

1)  Check your bios to see whether there are any setting you can change. (make sure to  write down the original settings.)

2)  Check whether there  is an update available for your bios and flash your bios.

3)  Create   a small boot partition at the beginning of the hard drive. (if you need help with that, just ask)

---

### Post by mlamberg on 2010-02-13
I moved the -19 kernel as suggested and re ran the boot_info-script to confirm that the kernel had moved above the 137G (see below).  Unfortunately it still booted fine... Is it possible that I need to also move the initrd.img-2.6.24-19-generic file to prove the bios issue?  I did confirm with Dell that there is an update to my bios (A08 to A09) but I couldn't find what it fixed..  Also its a Dos executable and I haven't yet researched how to build a DOS bootable disk off my Ubuntu system.  Until we confirm the bios issue I'm alittle hesitant to flash my bios to see if that fixes the problem...

Any other suggestions?  BTW  I really appreciate your help so far..

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00060f45

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   622,117,124   622,117,062  83 Linux
/dev/sda2         622,117,125   625,137,344     3,020,220   5 Extended
/dev/sda5         622,117,188   625,137,344     3,020,157  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4095b3fe-f072-45ff-9ad9-8c19f032ef44   ext3                                     
/dev/sda5        98625c87-87e7-4582-b645-1cf97a810ab5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4095b3fe-f072-45ff-9ad9-8c19f032ef44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=98625c87-87e7-4582-b645-1cf97a810ab5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 132.3GB: boot/grub/menu.lst
  97.7GB: boot/grub/stage2
  97.8GB: boot/initrd.img-2.6.24-19-generic
  97.7GB: boot/initrd.img-2.6.24-19-generic.bak
  97.7GB: boot/initrd.img-2.6.24-23-generic
  97.8GB: boot/initrd.img-2.6.24-23-generic.bak
 108.0GB: boot/initrd.img-2.6.24-24-generic
 107.5GB: boot/initrd.img-2.6.24-24-generic.bak
 108.0GB: boot/initrd.img-2.6.24-25-generic
 108.0GB: boot/initrd.img-2.6.24-25-generic.bak
 137.5GB: boot/initrd.img-2.6.24-26-generic
 137.5GB: boot/initrd.img-2.6.24-26-generic.bak
 137.0GB: boot/initrd.img-2.6.24-27-generic
 137.5GB: boot/initrd.img-2.6.24-27-generic.bak
 137.0GB: boot/vmlinuz-2.6.24-19-generic
  97.7GB: boot/vmlinuz-2.6.24-19-generic.bu
  97.8GB: boot/vmlinuz-2.6.24-23-generic
 103.8GB: boot/vmlinuz-2.6.24-24-generic
 103.8GB: boot/vmlinuz-2.6.24-25-generic
 137.0GB: boot/vmlinuz-2.6.24-26-generic
 137.4GB: boot/vmlinuz-2.6.24-27-generic
 137.0GB: initrd.img
 137.5GB: initrd.img.old
 137.4GB: vmlinuz
 137.0GB: vmlinuz.old
=============================== StdErr Messages: ===============================

blkid: invalid option -- p
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghl] [-o format] [-s <tag>] [-t <token>]
    [-v] [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)

```

---

### Post by meierfra. on 2010-02-13
> Until we confirm the bios issue I'm a little hesitant to flash my bios to see if that fixes the problem...

I agree

> Is it possible that I need to also move the initrd.img-2.6.24-19-generic file to prove the bios issue? 

I doubt it. But  try it anyway. If you are still able to boot the -19 kernel afterwards we can be pretty sure that its not a bios issue.

---

### Post by mlamberg on 2010-02-13
-19 still boots....   Any other suggestions?

---

### Post by meierfra. on 2010-02-13
> Any other suggestions? 

Lets see what happens when you reinstall grub and the kernels (I don't think this will work but I don't have any better suggestions.)

Start with reinstalling Grub:

```
sudo apt-get purge grub-pc grub-common
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda 
```

---

### Post by meierfra. on 2010-02-13
Assuming the reinstalling grub did not make a difference, you can reinstall the kernels via


```
sudo apt-get purge   linux-{image,headers}-2.6.24-{26,27}-generic linux-headers-2.6.24-{26,27} 
sudo apt-get install linux-{image,headers}-2.6.24-{26,27}-generic linux-headers-2.6.24-{26,27} 

```

---

### Post by meierfra. on 2010-02-13
Opps. I messed up the instructions to reinstall grub. Use


```
sudo apt-get purge grub 
sudo apt-get install grub
sudo grub-install --recheck /dev/sda 
```

(the other instructions are for Grub 2)

---

### Post by mlamberg on 2010-02-13
No problem...  Not sure if reinstalling grub would have helped.  I reinstalled the kernels and everything is working fine!!  I am up on rev -27 of the kernel as I should be..  Since I did run the Grub 2 install (which seemed to have no effect) should I be concerned?  Should I reinstall grub anyway?

---

### Post by mlamberg on 2010-02-13
> **mlamberg said:**
> No problem...  Not sure if reinstalling grub would have helped.  I reinstalled the kernels and everything is working fine!!  I am up on rev -27 of the kernel as I should be..  Since I did run the Grub 2 install (which seemed to have no effect) should I be concerned?  Should I reinstall grub anyway?

I reinstalled Grub anyway and everything is working fine..  

Maiefra, thank you very much for helping to solve my problem..  Looks like there was something corrupted with kernels -26 -27...  Reinstalling them fixed everything....

Mike    :D

---

### Post by meierfra. on 2010-02-13
> Since I did run the Grub 2 install (which seemed to have no effect) 

I don't think grub-pc is in the 8.04 repositories.  So those commands probably just failed.


> reinstalled the kernels and everything is working fine!!
Great.  I would have suggested  that first, but I didn't think that both kernels would get  corrupted.

---

