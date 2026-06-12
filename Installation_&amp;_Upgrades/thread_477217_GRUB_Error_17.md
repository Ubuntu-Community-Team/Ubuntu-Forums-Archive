---
title: "GRUB Error 17"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by guitarbeerchocolate on 2007-06-18
I am running ubuntu feisty 7.04
I received some updates through synaptic the other day and since then I haven't been able to load ubuntu. I'm now using the Live CD to send the post.

When I switch my machine on I get
GRUB loading, please wait...
Error 17

I tried following various instructions for re-installing GRUB, but to no avail. My setup seems pretty straight forward. No Windows! See the outputs below:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18748   150593278+  83  Linux
/dev/sda2           18749       19457     5695042+   5  Extended
/dev/sda5           18749       19457     5695011   82  Linux swap / Solaris
----------------------------------------------------------------------------------------------------------
grub> find /boot/grub/stage1

Error 15: File not found

grub> 
----------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type
----------------------------------------------------------------------------------------------------------
Can somebody please help me. I don't want to lose my installation.

---

### Post by Pumalite on 2007-06-18
> **guitarbeerchocolate said:**
> I am running ubuntu feisty 7.04
I received some updates through synaptic the other day and since then I haven't been able to load ubuntu. I'm now using the Live CD to send the post.

When I switch my machine on I get
GRUB loading, please wait...
Error 17

I tried following various instructions for re-installing GRUB, but to no avail. My setup seems pretty straight forward. No Windows! See the outputs below:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18748   150593278+  83  Linux
/dev/sda2           18749       19457     5695042+   5  Extended
/dev/sda5           18749       19457     5695011   82  Linux swap / Solaris
----------------------------------------------------------------------------------------------------------
grub> find /boot/grub/stage1

Error 15: File not found

grub> 
----------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type
----------------------------------------------------------------------------------------------------------
Can somebody please help me. I don't want to lose my installation.

What is your hardware? In particular, what is your graphics card?

---

### Post by merlinus on 2007-06-18
It may be that grub cannot be found because your ubuntu partitions are not mounted when running from the live cd.

Try supergrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by logos34 on 2007-06-18
> grub> find /boot/grub/stage1

Error 15: File not found

> It may be that grub cannot be found because your ubuntu partitions are not mounted when running from the live cd.

Actually, the grub 'find' stage1 command checks all *mountable* (as opposed to mounted) partitions...they don't actually have to be mounted, which is what is so nice about it.  Only the alternative command 'grub-install /dev/hdx' needs to be run from the mounted partition.  

> ...what is your graphics card?

I don't think it's a graphics issue, because you'd likely see the X server error screen. You're not even getting that far in the boot process.

Something in the updates may have altered menu.lst, confusing grub (Often a kernel update is the culprit. Maybe you just decided to accept the 2.6.20-16 update that's been out for a while, not sure exactly what updates you installed).  

You could try Supergrub as merlinus suggested.  Or if you can get as far as the grub menu (and the 'error 17' comes up AFTER you choose to boot the selected kernel), do this:

-hit 'e' key to edit the 'root' line.  Should read 'root (hd0,0)'. You could also try replacing the 'root=UUID...' in the 'kernel' line to read 'root=/dev/sda1'.

Or if 'error 17' appears before the menu, use the live cd to mount root so you can edit menu.lst, as you tried above (you almost had it):

> sudo mkdir /mnt/ubuntu
**sudo mount -t ext3 /dev/sda1 /mnt/ubuntu**
cd /mnt/ubuntu/boot/grub
sudo gedit menu.lst


---

### Post by merlinus on 2007-06-18
> 
Actually, the grub 'find' stage1 command checks all mountable (as opposed to mounted) partitions...they don't actually have to be mounted, which is what is so nice about it. Only the alternative command 'grub-install /dev/hdx' needs to be run from the mounted partition.


Good to know this.  Thanks!

But even with the kernel update changes, why would grub not be found at all?

In my case, the upgrades have changed (hd0,7) -- which is correct -- to something else, which I can edit from the grub screen as you suggested, but /boot/grub/menu.lst still exists.

-merlin

---

### Post by logos34 on 2007-06-18
> But even with the kernel update changes, why would grub not be found at all?

In my case, the upgrades have changed (hd0,7) -- which is correct -- to something else, which I can edit from the grub screen as you suggested, but /boot/grub/menu.lst still exists.

ok, guitarbeerchocolat is not even getting the menu, grub is trying to load but no go.  (had to reread that part).  So, right, it can't even find stage2, menu.lst on root partition.  Not sure how to parse the sentence 'to no avail' concerning  grub reinstall (the reinstall didn't help or couldn't apply the instructions successfully?).  

What I'm wondering is could this have anything to do with the switcheroo from ide to scsi subsystem drive designation in feisty (where hda becomes sda)? This doesn't seem likely as grub uses 'hdx' format and BIOS 'calls' to find root...Partition table on the disk currupted, filesystem errors?  fsck (run from the live cd) and TestDisk (from SystemRescueCD, GParted livecd) might fix that.  not sure what else to suggest short of a reinstall (which would be the easiest way were it not for the fact that doing the updates again may cause the same problems all over again). 

Didn't FleetAdmral something or other get the find error 15's?

---

### Post by merlinus on 2007-06-18
Yeah, someone just the other day got the grub find -- error 15, but don't know if it ever got resolved.  I think it even drove Herman nuts.

The only other thing I can think of is that he is not using UUIDs.  If he were, then the changes from hd's to sd's and then back again would not matter.  That was true in my case.

-merlin

---

### Post by guitarbeerchocolate on 2007-06-19
> **logos34 said:**
> Actually, the grub 'find' stage1 command checks all *mountable* (as opposed to mounted) partitions...they don't actually have to be mounted, which is what is so nice about it.  Only the alternative command 'grub-install /dev/hdx' needs to be run from the mounted partition.  



I don't think it's a graphics issue, because you'd likely see the X server error screen. You're not even getting that far in the boot process.

Something in the updates may have altered menu.lst, confusing grub (Often a kernel update is the culprit. Maybe you just decided to accept the 2.6.20-16 update that's been out for a while, not sure exactly what updates you installed).  

You could try Supergrub as merlinus suggested.  Or if you can get as far as the grub menu (and the 'error 17' comes up AFTER you choose to boot the selected kernel), do this:

-hit 'e' key to edit the 'root' line.  Should read 'root (hd0,0)'. You could also try replacing the 'root=UUID...' in the 'kernel' line to read 'root=/dev/sda1'.

Or if 'error 17' appears before the menu, use the live cd to mount root so you can edit menu.lst, as you tried above (you almost had it):

Thanks for the great response so far.
Sorry to be a pain.  Since my last post I found a command similar to one used by a contributor called Cappy:
sudo e2fsck -f /dev/sda1
It found a lot of errors on my partition and cleared them.  The good thing is that since then, I have been able to do the following:
> 
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
cd /mnt/ubuntu/boot/grub
sudo gedit menu.lst

and I can now get to my partition and backup again.
The bad news is that now I have another error message:
> 
Error 13: Invalid or unsupported executable format.

I've tried looking around, and most things I see are associated with Windows dual boot. I don't have windows dual boot.

---

### Post by confused57 on 2007-06-19
You might want to post the boot entries in your menu.lst...maybe someone will see a small error in the format of the entry.

---

### Post by guitarbeerchocolate on 2007-06-19
OK.  Here is my menu.lst:
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
# kopt=root=UUID=58c5795a-5a67-439e-a2ed-dfcdb9ab13a0 ro
# kopt_2_6=root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro

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
# defoptions=quiet splash noacip

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro quiet noacip
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro quiet splash noacip
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro quiet splash noacip
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by confused57 on 2007-06-19
First you might want to run this from a terminal:
```
blkid
```
compare the UUID with the kernel entry in your menu.lst

I think your Ubuntu entry should be something like this:
```
title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=ecf29eba-a98a-49af-bf00-c767a4bf9a2b ro quiet noapic acpi=off
initrd /boot/initrd.img-2.6.20-16-generic
savedefault
boot
```

I'm not sure which of the kernel boot parameters you need, but noacip probably wasn't recognized.

---

### Post by logos34 on 2007-06-19
yeah nocip is a typo (how did that get screwed up?).  try 'noapic' and or 'nolapic' option.

Also, comment out hiddenmenu and increase the timeout (at least temporarily until everythings sorted):

timeout  [COLOR="Blue"]10[/COLOR]

[COLOR="Blue"]#[/COLOR]hiddenmenu

---

### Post by logos34 on 2007-06-19
you might also take out **quiet** option so that you'll see the output of the boot process.  If it stops somewhere you'll be able to isolate the problem.

---

### Post by guitarbeerchocolate on 2007-06-19
OK. I made the changes to my menu.lst and compared the UUIDs from blkid.
I couldn't see anything other than:
Error 13: Invalid or unsupported executable format
from my default startup, but I did try some of the other options offered by grub.
On option 3 I finally got some information including:
target filesystem doesn't have /sbin/init
BusyBox v1.1.3 (Debian 1:1.1.3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
(initramfs)

I don't know if this helps.

---

### Post by psusi on 2007-06-19
Sounds like your kernel got corrupted as a result of whatever clobbered your filesystem, and fsck wasn't able to repair it.  Reinstall your kernel.  From the livecd, mount the partition in /mnt like you said you got to work before, then:

sudo chroot /mnt
apt-get --reinstall install linux-image-2.6.20-16-generic

---

### Post by guitarbeerchocolate on 2007-06-19
Excuse my ignorance but this was my output :
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu
chroot: cannot run command `/bin/bash': Not a directory

---

### Post by logos34 on 2007-06-19
yes, vmlinuz may be the problem

---

### Post by confused57 on 2007-06-19
> **guitarbeerchocolate said:**
> Excuse my ignorance but this was my output :
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu
chroot: cannot run command `/bin/bash': Not a directory
You might try this to chroot into your root partition(taken from Gentoo handbook):
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu /bin/bash
```

Then you might be able to reinstall the kernel?

---

### Post by guitarbeerchocolate on 2007-06-20
Sorry, same message.
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/ubuntu/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/ubuntu/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu /bin/bash
chroot: cannot run command `/bin/bash': Not a directory

I have to go to France now. I'll pick it up when I get back. Thank you very much for your help thus far.

---

### Post by guitarbeerchocolate on 2007-07-17
Sadly, I lost patience and re-installed ubuntu.  This may or may not be a reflection of ubuntu updates. I do suffer from power cuts and surges here. I have also subsequently realised that there is a fault on my modem which may also have contributed to missing packets on the update download.

In the end I want to sat thanks for the support.  The help which I got provided me the opportunity to save all my data before re-installing. I am now a happy ubuntu user once more.

---

