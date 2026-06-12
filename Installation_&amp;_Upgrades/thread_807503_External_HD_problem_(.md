---
title: "External HD problem :("
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by sysope on 2008-05-25
After installing Ubuntu 8.04 on an USB external HD as soon i reboot the pc for my first Ubuntu session instead of the normal booting process i get this:

GNU GRUB
Minimal Bash Like
........... etc etc etc

whats wrong? :( Can anyone help me? I really would love to install Ubuntu on this USB External HD. The USB HD its Fujitsu 120G.

Thx in advance

---

### Post by Pumalite on 2008-05-25
Did you set your computer to boot from USB first?

---

### Post by sysope on 2008-05-25
> **Pumalite said:**
> Did you set your computer to boot from USB first?

of course otherwise i couldn't boot from external USB HD and get the error :(

btw .. thx for the quick reply :D

---

### Post by Pumalite on 2008-05-25
Not necessarily. Anyway; can you boot into Windows with your external disconnected?

---

### Post by sysope on 2008-05-25
> **Pumalite said:**
> Not necessarily. Anyway; can you boot into Windows with your external disconnected?

I can boot into windows either with external USB HD connected or not. My problem is just when i try to boot to linux through external USB HD.

once again thx

---

### Post by Pumalite on 2008-05-25
Post your external's menu.lst

---

### Post by sysope on 2008-05-25
> **Pumalite said:**
> Post your external's menu.lst

I would love to. I think I can find that in: /boot/grub/
which I cant access since I get a "GNU GRUB minimal bash".
If you know any way i can access to it please tell me :D

once more .. thx 4 your help :D

---

### Post by EXCiD3 on 2008-05-25
> **sysope said:**
> I would love to. I think I can find that in: /boot/grub/
which I cant access since I get a "GNU GRUB minimal bash".
If you know any way i can access to it please tell me :D

once more .. thx 4 your help :D

Boot into the livecd, mount the external drive and then access your /boot/grub/menu.lst

Btw, you can thank him by clicking the Thanks button (the blue medal) on his posts.:KS

---

### Post by Pumalite on 2008-05-25
Boot your Live CD with your external connected, but unmounted. Post:
sudo fdisk -l

---

### Post by sysope on 2008-05-25
> **Pumalite said:**
> Post your external's menu.lst

dont have that file or the /boot/grub/
snif snif :(
Already tried to install it again and i installed the boot loader on hdb instead of hd0 the result its the same no /boot/grub/

---

### Post by Pumalite on 2008-05-25
Burn a new CD after doing md5sum and burning at 4x or less on CD-R

---

### Post by meierfra. on 2008-05-25
You do have  a grub folder, otherwise you would not get:

GNU GRUB
Minimal Bash Like
........... etc etc etc


Boot from the LiveCD.
Go to Places->Computer and double click the icon for your Ubuntu partition. Then navigate to /boot and then to /boot/grub

If this does not work (and even if it does work), open a terminal (Applications->Acccesories->Terminal) and  post the output of

```
sudo fdisk -l
```

---

### Post by sysope on 2008-05-26
morning to u all and once again thanks a lot 4 your help ...

- Like i said i dont have any folder named /boot/grub i took a picture where u can see that :

[IMG]http://img156.imageshack.us/my.php?image=screenshotdg8.png[/IMG]

(if the pic doesnt show up heres the link: [http://img156.imageshack.us/my.php?image=screenshotdg8.png](http://img156.imageshack.us/my.php?image=screenshotdg8.png)

- About the sudo fdisk -l heres the result:

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytesr
Disk identifier: 0xa49a0717

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14219   114214086   83  Linux
/dev/sdb2           14220       14593     3004155    5  Extended
/dev/sdb5           14220       14593     3004123+  82  Linux swap / Solaris

im starting to think that external USB HD are rubbish :(

---

### Post by Pumalite on 2008-05-26
Mount your partition:
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Post:
cat /media/sdb1/boot/grub/menu.lst

---

### Post by sysope on 2008-05-26
> **Pumalite said:**
> Mount your partition:
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Post:
cat /media/sdb1/boot/grub/menu.lst


sorry if im stubborn but this is the second or third time i say i dont have such folder or file :(

[IMG]http://img365.imageshack.us/my.php?image=screenshotti3.png[/IMG]

pic link: [http://img365.imageshack.us/my.php?image=screenshotti3.png](http://img365.imageshack.us/my.php?image=screenshotti3.png)

---

### Post by meierfra. on 2008-05-26
That is very strange. What's on your internal drive?

 Any chance you created a grub partition on your internal drive?  


And just so that you can say three more times that you have no such file: What are the outputs of

```
sudo grub

```

and at the grub prompt:

```
find /boot/grub/stage1
find /grub/stage1
find /stage1 
```
(the last letter is the number one)

---

### Post by keviniskool on 2008-05-26
I too am having the same problem as sysope, however, my menu.lst is still there. Here is what it says: ```
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
# kopt=root=UUID=5a2455fe-bc1f-4eb7-91bd-8944577520a3 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5a2455fe-bc1f-4eb7-91bd-8944577520a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5a2455fe-bc1f-4eb7-91bd-8944577520a3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by meierfra. on 2008-05-26
keviniskool:  could you post the output of

```
sudo fdisk -l
```
( l is a lower case L)

Also please describe exactly what happens when you try to boot.

---

### Post by meierfra. on 2008-05-26
keviniskool:  Also try  pressing "esc" during boot up and see whether the grub menu appears.

---

### Post by keviniskool on 2008-05-26
Here is the output: ```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc465c465

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        9729    78059835    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19364   155541298+  83  Linux
/dev/sdb2           19365       19457      747022+   5  Extended
/dev/sdb5           19365       19457      746991   82  Linux swap / Solaris

```

When I try booting up, one computer says the boot sector can't be found, while the other mentions something about GRUB like sysope. I am using a 120GB Western Digital Passport.

---

### Post by keviniskool on 2008-05-26
Do I press esc after I choose to boot from USB Drive?

---

### Post by keviniskool on 2008-05-26
Never mind, it doesn't work.

---

### Post by meierfra. on 2008-05-26
Kevinskool: Boot from the LiveCD, open a terminal and type

```
sudo grub
```


and the "grub>" prompt:


```

root (hd1,0)
setup (hd1)
quit
```


Reboot from your Ubuntu drive.
If this works I'll show you how to add Windows to the grub menu.

---

### Post by keviniskool on 2008-05-26
It didn't work. However, I tested it on the one that just said the boot sector couldn't be found.

Note: It can boot other USB Operating systems, like Puppy Linux

---

### Post by meierfra. on 2008-05-26
> It didn't work. 

Any error messages in the terminal?
Anything different during boot up?


> However, I tested it on the one that just said the boot sector couldn't be found

Well, you need to boot  from the drive Ubuntu is on (although I would think  that that is the one who said "boot sector not found"

---

### Post by keviniskool on 2008-05-26
Absolutely nothing different during startup, no error messages, nothing. The "no boot sector" error is the one that pops up when I try the ubuntu drive.

---

### Post by Pumalite on 2008-05-26
Something must be wrong with that installation.

---

### Post by meierfra. on 2008-05-26
Try Supergrub (see my signature)

---

### Post by meierfra. on 2008-05-26
Any chance that your MBR  is "write" protected? It seems that grub is not able to write to the MBR of the ubuntu drive. Check your bios.

---

### Post by keviniskool on 2008-05-26
I think it might be read only. I'm running on a school computer with a locked down bios. That probably explains why Puppy works too, as it uses a read-only MBR I think.

---

### Post by keviniskool on 2008-05-26
I'm probably just going to give up on this. The whole point of this was so I could run Ubuntu at school. If I can only run it on MBR enabled BIOSes, there isn't much reason for me to continue. Thank you for your time and effort though.

---

### Post by meierfra. on 2008-05-26
> I'm running on a school computer with a locked down bios. 

But then, how are you able to select what drive you are booting from?
And how could you get an grub error?  Does  the computer still work if you remove your USB drive?

---

### Post by meierfra. on 2008-05-26
> If I can only run it on MBR enabled BIOSes, 

Do you have computer at home ?

You could try 

sudo grub
root (hd1,0)
setup (hd1)
quit

on you home computer  to  get grub installed on the MBR of your USB drive, and then see that happens in school.

---

### Post by keviniskool on 2008-05-27
The school computers allow a temporary change in boot order, but that's it. The GRUB error is on the non-school computer, and I already tried the

sudo grub
root (hd1,0)
setup (hd1)
quit

I think it can work, but it just wouldn't be effective for me. School policies ruin everything. :(

---

### Post by meierfra. on 2008-05-27
This is pretty darn confusing. Lets stick to one computer at the time. Before you have any chance to get Ubuntu to work on the school computer, you need to be able to boot of the external drive on your non-school computer.  

The "fdisk" data you gave me, was that from the non-school computer?
If not please provide "sudo fdisk -l" from your non-school computer.

Try 

sudo grub
root (hd1,0)
setup (hd1)

again (on your non-school computer) but before "quit" copy the whole terminal  and post it here.

---

### Post by keviniskool on 2008-05-28
I'm just starting all over. I just found out that Wubi installs to other drives, so I'm going to run off of that in Windows.

---

### Post by meierfra. on 2008-05-28
> I just found out that Wubi installs to other drives, so I'm going to run off of that in 
But I'm pretty sure you wouldn't be able to use such a Wubi install on your school computer. All the booting information will be on the Windows drive of your non-school computer. (But I really don't know much about Wubi)

---

