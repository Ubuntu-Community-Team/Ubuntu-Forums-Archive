---
title: "E: dpkg was interrupted................ 'dpkg --configure -a'"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Denny Johnson on 2010-04-11
I have tried searching for a solution, but, no joy.
When I try to install updates, I get the following
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

In the terminal, if I run
> sudo dpkg --configure -a

I get
> denjohn@dell:~$ sudo dpkg --configure -a
[sudo] password for denjohn: 
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-27-generic (2.6.24-27.45) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-27-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-27-generic (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-ubuntu-modules-2.6.24-26-generic (2.6.24-26.44) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-26-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-26-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-26-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-27-generic; however:
  Package linux-ubuntu-modules-2.6.24-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-backports-modules-2.6.24-27-generic (2.6.24-27.36) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-27-generic
dpkg: error processing linux-backports-modules-2.6.24-27-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.27.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-hardy-generic:
 linux-backports-modules-hardy-generic depends on linux-backports-modules-2.6.24-27-generic; however:
  Package linux-backports-modules-2.6.24-27-generic is not configured yet.
dpkg: error processing linux-backports-modules-hardy-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-hardy:
 linux-backports-modules-hardy depends on linux-backports-modules-hardy-generic (= 2.6.24.27.29); however:
  Package linux-backports-modules-hardy-generic is not configured yet.
dpkg: error processing linux-backports-modules-hardy (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-27-generic
dpkg: subprocess post-installation script returned error exit status 1
denjohn@dell:~$ 


I'm sorta new to this, any help appreciated.

---

### Post by whoop on 2010-04-11
Is your hard-disk (nearly) full?
```

df -h

```

---

### Post by Denny Johnson on 2010-04-11
Thanks for the comeback.
Looks like maybe /dev/sda3 is.
If that is the problem, I don't know what to do, any help appreciated.

> denjohn@dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             143G   24G  112G  18% /
varrun               1009M  232K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M   44K 1009M   1% /dev/shm
/dev/sda3             193M  189M     0 100% /boot
tmpfs                1009M   40M  970M   4% /lib/modules/2.6.24-27-generic/volatile


---

### Post by whoop on 2010-04-11
remove some old kernels. your boot partition probably has a few, and your probably only using the latest one.

Note: I always leave two working kernels on /boot (just to be safe)...

use:
```

sudo aptitude search linux-image | grep "i "

```
To see the kernels you have installed...
Keep the last 2 working kernels, also keep "linux-image-generic", remove all older kernels.
You need to repeat this process after you or updates install new kernels.

If you don't like the command line you can start up synaptic search for linux-image and remove the old kernels from there...

---

### Post by Denny Johnson on 2010-04-11
Thanks whoop, and special thanks for giving the commands.
This is what I got w your last command, but I don't see how to remove the older kernels??

> denjohn@dell:~$ sudo aptitude search linux-image | grep "i "
[sudo] password for denjohn: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
i   linux-image-2.6.20-16-generic   - Linux kernel image for version 2.6.20 on x
i A linux-image-2.6.20-17-generic   - Linux kernel image for version 2.6.20 on x
i   linux-image-2.6.22-15-generic   - Linux kernel image for version 2.6.22 on x
i   linux-image-2.6.24-19-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-21-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-22-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-23-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-24-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-25-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-26-generic   - Linux kernel image for version 2.6.24 on x
i   linux-image-2.6.24-27-generic   - Linux kernel image for version 2.6.24 on x
denjohn@dell:~$ 


---

### Post by whoop on 2010-04-11
Example:
```

sudo aptitude remove linux-image-2.6.20-16-generic

```
will remove linux-image-2.6.20-16-generic

You could also use synaptic and search for linux-image and rightclick, select "mark for removal" and then apply changes, if you don't like cli.

You could leave these for instance:
linux-image-2.6.24-25-generic
linux-image-2.6.24-26-generic
linux-image-2.6.24-27-generic

---

### Post by Denny Johnson on 2010-04-11
Re your last edit in post 4......when I try to open the synaptic package mgr, I get the same

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any suggestion re how to remove old kernels?

Edit....we are talking over each other, give me a sec to try your last suggestion, thanks,

---

### Post by jflaker on 2010-04-11
purge /tmp probably wouldn't be a bad idea either.

Another thing to purge unnecessary packages and dependencies...

```
sudo apt-get purge&&sudo apt-get autoremove
```

---

### Post by Denny Johnson on 2010-04-11
whoop
I ran
> sudo aptitude remove linux-image-2.6.20-16-generic
and got
> 
denjohn@dell:~$ sudo aptitude remove linux-image-2.6.20-16-generic
[sudo] password for denjohn: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
denjohn@dell:~$ 


I then re ran
> $ sudo aptitude search linux-image | grep "i "

The 2.6.20-16-generic kernel is still there

> denjohn@dell:~$ sudo aptitude search linux-image | grep "i "
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
i   linux-image-2.6.20-16-generic   - Linux kernel image for version 2.6.20 on x
i A linux-image-2.6.20-17-generic   - Linux kernel image for version 2.6.20 on x
i   linux-image-2.6.22-15-generic   - Linux kernel image for version 2.6.22 on x
i   linux-image-2.6.24-19-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-21-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-22-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-23-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-24-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-25-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-26-generic   - Linux kernel image for version 2.6.24 on x
i   linux-image-2.6.24-27-generic   - Linux kernel image for version 2.6.24 on x

---

### Post by whoop on 2010-04-11
> **Denny Johnson said:**
> Re your last edit in post 4......when I try to open the synaptic package mgr, I get the same


Ah, yes, because there are problems, synaptic will complain.
Hhm, don't remember ever having to force a removal..
maybe:
sudo aptitude remove -f linux-image-2.6.20-16-generic

never ran this before though...

---

### Post by Denny Johnson on 2010-04-11
Thanks jflaker, but no joy.
> denjohn@dell:~$ sudo apt-get purge&&sudo apt-get autoremove
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
denjohn@dell:~$ 


---

### Post by whoop on 2010-04-11
> **Denny Johnson said:**
> Thanks jflaker, but no joy.

And sudo aptitude remove -f linux-image-2.6.20-16-generic?

---

### Post by Denny Johnson on 2010-04-11
whoop....still no joy
> denjohn@dell:~$ sudo aptitude remove -f linux-image-2.6.20-16-generic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
denjohn@dell:~$ 

---

### Post by lisati on 2010-04-11
If it's a disk space problem, it might be an idea to reboot to clear out /tmp and then trying again.

---

### Post by whoop on 2010-04-11
> **lisati said:**
> If it's a disk space problem, it might be an idea to reboot to clear out /tmp and then trying again.

Will this also make a difference if the /boot partition is the cause of the problem (this partitions seems to be full)?

---

### Post by Denny Johnson on 2010-04-11
Lisati.........I've rebooted a few times during the past few days,,,,,,nothing changed

---

### Post by lisati on 2010-04-11
> **Denny Johnson said:**
> Lisati.........I've rebooted a few times during the past few days,,,,,,nothing changed

OK, so it seems like my idea was little more than a shot in the dark. :) No worries - anyone else?

---

### Post by whoop on 2010-04-11
Blech, this is a real bugger, check this:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/289560](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/289560)

Only thing I can think of is forcefully removing stuff, which off course is stupid.

---

### Post by Denny Johnson on 2010-04-11
Thanks whoop.............these quotes from that bug pg sound like my problem, but I'm not clued in enuf to detect a solution there.
Anyone w any more suggestions to manually delete the older kernel images???

> Philip Muškovac  wrote on 2010-02-12:  	  #18

@Chevalier: Yes, you ran out of space on /boot so the initrd cannot be created and fails with an out of space error. You first need to free some space there (by removing unused older kernel images) before you can install new ones.
Chevalier wrote on 2010-02-13: 	#19

Thanks Philip Muškovac for your answer. You was right : I manually deleted the older kernel images and now everything is fine.

---

### Post by whoop on 2010-04-11
Well this seems like the solution of a madman:

```

sudo rm /boot/vmlinuz-2.6.20-16-generic
sudo dpkg --configure -a
sudo aptitude purge linux-image-2.6.20-16-generic

```
Then remove some other old kernels with "sudo aptitude purge"
Then updating might work again:
```

sudo aptitude update
sudo aptitude safe-upgrade

```

Also removing one kernel might not be enough (maybe the new data is larger than the old one). So you might even have to remove two to be on the safe(r) side. So then it would be like:
```

sudo rm /boot/vmlinuz-2.6.20-16-generic
sudo rm /boot/vmlinuz-2.6.20-17-generic 
sudo dpkg --configure -a
sudo aptitude purge linux-image-2.6.20-16-generic
sudo aptitude purge linux-image-2.6.20-17-generic 

```
Then remove some other old kernels with "sudo aptitude purge"
Then updating might work again:
```

sudo aptitude update
sudo aptitude safe-upgrade

```

Just be sure you are not removing a kernel you are running, so 
```

uname -r

```
should not say 2.6.20-16-generic or 2.6.20-17-generic (or any of the other kernels you are purging) in this example...

This is possibly very stupid, so if nobody knows a "good" solution and if nobody says this is indeed insane you could try it. So I would wait a while, and then contemplate before attempting this...
In my mind this works, it's in my mind though:lolflag:

---

### Post by Denny Johnson on 2010-04-11
> if nobody knows a "good" solution and if nobody says this is indeed insane you could try it. So I would wait a while, and then contemplate before attempting this...

thanks whoop.....think I'll give it overnite til I try anything potentially stupid.........I really am in over my head w this.

---

### Post by Denny Johnson on 2010-04-11
EDITED for clarification

am I on to something here........I've been searching results for 'delete kernel', most of them lead to a terminal response of

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

but, I found this

> Re: How to delete old kernel from boot menu
Open the Terminal and type:

Code:

gksudo gedit /boot/grub/menu.lst

Now comment out, or remove the relevant entries for the kernels you have removed, save the file, and you're done.

It brings up the following which looks to be editable???

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro

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
# defoptions=splash vga=773

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
root		(hd0,2)
kernel		/vmlinuz-2.6.24-27-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-27-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-26-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-26-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-25-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-25-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-24-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-24-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.22-15-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.22-15-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.22-15-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.20-17-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-17-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.20-17-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-17-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.20-17-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro splash vga=773
initrd		/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=359a8208-cd4c-4e44-8091-6cb72b8f95fc ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz[

---

### Post by whoop on 2010-04-11
> **Denny Johnson said:**
> am I on to something here........I've been searching results for 'delete kernel', most of them lead to a terminal response of

but, I found this
Nope, that's not useful, it removes a kernel line from the boot (grub) list... it does not remove it from disk, which is what we want.

---

### Post by Denny Johnson on 2010-04-11
:sad:

---

### Post by Denny Johnson on 2010-04-11
How about this /boot and /lib/modules idea???

>  Re: how can i delete a kernel
edit your /boot/grub/menu.lst and remove the entries you don't want, additonally you can delete the kernel image in /boot and the corresponding modules in /lib/modules, should be pretty selfexplanatory.

---

### Post by whoop on 2010-04-11
> **Denny Johnson said:**
> How about this /lib/modules idea???
It shows 12 kernels

Deleting the kernel itself is usually done by a package manager (like aptitude or apt), this does not work in our case, we can not fix it with --configure as that requires space as well.
/lib/modules does not reside on /boot so it is not the direct cause of the problem, neither can it solve it.

In the "solution" I gave we manually remove a kernel with the rm command. Although I am not really hesitant of using this command myself, it's not really code of conduct to advise other users to rm all over the place (just to bypass a package manager), especially in such a crucial location as /boot. Furthermore I have never tried my own advise in this case. Hence my reservation.

---

### Post by Denny Johnson on 2010-04-11
Thank you very much for the help..........I've got a busy, early day tomorrow so I'll be getting horizontal soon.
Tomorrow, when I have time and a clear head I'll proceed cautiously w your rm solution, unless something more conventional shows before then.
Best wishes
Denny

---

### Post by whoop on 2010-04-12
I've been thinking about it and I think the following solution has a higher success rate. 
As I have not run these commands (but in my mind they work just fine :lolflag:), there is always a possibility of typos, so I also tried to explain what I am attempting to do.

So here it is:

1:make sure you are not removing a running kernel, so if 
```

uname -r

```
returns 2.6.20-16-generic or 2.6.20-17-generic, don't continue, else
go to step 2.

2: We need to make some space in /boot so we want to move some files, first we must check if the files we want to move are present.
The command:
```

ls /boot

```
should return: 
vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic
vmlinuz-2.6.20-17-generic
initrd.img-2.6.20-17-generic
and allot of other stuff off course.
If these files are returned go to step 3, if not we are stuck so you need to post the output of "ls /boot" so we can continue.

3: Move some large files from boot to root, try to fix package management
and then try to properly remove old kernels:
```

sudo mv /boot/vmlinuz-2.6.20-16-generic /root
sudo mv /boot/initrd.img-2.6.20-16-generic /root
sudo mv /boot/vmlinuz-2.6.20-17-generic /root
sudo mv /boot/initrd.img-2.6.20-17-generic /root
sudo dpkg --configure -a
sudo aptitude purge linux-image-2.6.20-16-generic
sudo aptitude purge linux-image-2.6.20-17-generic

```
If the above works go to 4, else go to 5

4: Remove files we moved to root
```

sudo rm /root/vmlinuz-2.6.20-16-generic
sudo rm /root/initrd.img-2.6.20-16-generic
sudo rm /root/vmlinuz-2.6.20-17-generic
sudo rm /root/initrd.img-2.6.20-17-generic

```
If this worked you are out of trouble, It is advisable to look at all kernels you have installed. I recommend keeping two of the latest working kernels and purging the rest before updating the system. Off course make sure you are not purging a running kernel. Future updates might install new kernels, so you now know you have to keep track of the amount of kernels you have installed to keep the system on track...

5: It didn't work, so we put back the files and wait for a better solution
```

sudo mv /root/vmlinuz-2.6.20-16-generic /boot
sudo mv /root/initrd.img-2.6.20-16-generic /boot
sudo mv /root/vmlinuz-2.6.20-17-generic /boot
sudo mv /root/initrd.img-2.6.20-17-generic /boot

```

---

### Post by Denny Johnson on 2010-04-12
Thanks whoop
Steps 1 and 2 went as planned.
For step 3, I copied and pasted the 7 lines of your code, looks like some action started after the 5th of the 7 lines, then the 6th line appears later, but the 7th line doesn't appear.
Perhaps I have to accept the solution for the 6th line first?
Thought I'd let you have a look before I 'Y' to accept the solution.
> denjohn@dell:~$ uname -r
2.6.24-27-generic
denjohn@dell:~$ ls /boot
abi-2.6.20-16-generic             initrd.img-2.6.24-22-generic.bak
abi-2.6.20-17-generic             initrd.img-2.6.24-23-generic
abi-2.6.22-15-generic             initrd.img-2.6.24-23-generic.bak
abi-2.6.24-19-generic             initrd.img-2.6.24-24-generic
abi-2.6.24-21-generic             initrd.img-2.6.24-24-generic.bak
abi-2.6.24-22-generic             initrd.img-2.6.24-25-generic
abi-2.6.24-23-generic             initrd.img-2.6.24-25-generic.bak
abi-2.6.24-24-generic             initrd.img-2.6.24-26-generic
abi-2.6.24-25-generic             initrd.img-2.6.24-26-generic.bak
abi-2.6.24-26-generic             initrd.img-2.6.24-27-generic
abi-2.6.24-27-generic             lost+found
config-2.6.20-16-generic          memtest86+.bin
config-2.6.20-17-generic          System.map-2.6.20-16-generic
config-2.6.22-15-generic          System.map-2.6.20-17-generic
config-2.6.24-19-generic          System.map-2.6.22-15-generic
config-2.6.24-21-generic          System.map-2.6.24-19-generic
config-2.6.24-22-generic          System.map-2.6.24-21-generic
config-2.6.24-23-generic          System.map-2.6.24-22-generic
config-2.6.24-24-generic          System.map-2.6.24-23-generic
config-2.6.24-25-generic          System.map-2.6.24-24-generic
config-2.6.24-26-generic          System.map-2.6.24-25-generic
config-2.6.24-27-generic          System.map-2.6.24-26-generic
grub                              System.map-2.6.24-27-generic
initrd.img-2.6.20-16-generic      vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.20-17-generic
initrd.img-2.6.20-17-generic      vmlinuz-2.6.22-15-generic
initrd.img-2.6.20-17-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.22-15-generic      vmlinuz-2.6.24-21-generic
initrd.img-2.6.22-15-generic.bak  vmlinuz-2.6.24-22-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-23-generic
initrd.img-2.6.24-19-generic.bak  vmlinuz-2.6.24-24-generic
initrd.img-2.6.24-21-generic      vmlinuz-2.6.24-25-generic
initrd.img-2.6.24-21-generic.bak  vmlinuz-2.6.24-26-generic
initrd.img-2.6.24-22-generic      vmlinuz-2.6.24-27-generic
denjohn@dell:~$ sudo mv /boot/vmlinuz-2.6.20-16-generic /root
[sudo] password for denjohn: 
denjohn@dell:~$ sudo mv /boot/vmlinuz-2.6.20-16-generic /root
mv: cannot stat `/boot/vmlinuz-2.6.20-16-generic': No such file or directory
denjohn@dell:~$ sudo mv /boot/initrd.img-2.6.20-16-generic /root
denjohn@dell:~$ sudo mv /boot/vmlinuz-2.6.20-17-generic /root
denjohn@dell:~$ sudo mv /boot/initrd.img-2.6.20-17-generic /root
denjohn@dell:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-27-generic (2.6.24-27.45) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

Setting up linux-ubuntu-modules-2.6.24-26-generic (2.6.24-26.44) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-26-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

Setting up linux-image-generic (2.6.24.27.29) ...
Setting up linux-backports-modules-2.6.24-27-generic (2.6.24-27.36) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

Setting up linux-generic (2.6.24.27.29) ...
Setting up linux-backports-modules-hardy-generic (2.6.24.27.29) ...
Setting up linux-backports-modules-hardy (2.6.24.27.29) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-27-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
denjohn@dell:~$ sudo aptitude purge linux-image-2.6.20-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  linux-backports-modules-2.6.20-16-generic 
The following packages are unused and will be REMOVED:
  libdns35 linux-backports-modules-2.6.24-25-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.20-16-generic{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 75.8MB will be freed.
The following packages have unmet dependencies:
  linux-backports-modules-2.6.20-16-generic: Depends: linux-image-2.6.20-16-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-2.6.20-16-generic

Score is 119

Accept this solution? [Y/n/q/?] 


---

### Post by whoop on 2010-04-12
I don't see anything crucial that the package manager wants to remove, it looks quite safe to me. It also wants to remove libdns35, don't know why, that's for dns service. So if you are using the system as a dns server you might experience problems with resolving domain names (for other machines in your network), but that should be easier to fix afterwards than this.
I was expecting dpkg would fix everything now, maybe the purge will..

Also, I don't know if I understand you correctly but if I do I can tell you: it is better to execute the commands one line at a time (and stop and think if one fails). In this case it doesn't matter that much, but in other cases it could prove hazardous.
As an example I can see in you output that "sudo mv /boot/vmlinuz-2.6.20-16-generic /root" was executed twice, this is not a problem because you cannot move something twice, but in other cases (like adding a single line to a file for example), you will end up with incorrect data.

---

### Post by Denny Johnson on 2010-04-12
Thanks for the 'one line at a time' tip.
This laptop is a stand alone unit, other than a printer, router, and modem.
Look OK to y?
Thanks

Here's the latest:
> Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  libdns35 linux-backports-modules-2.6.24-25-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-backports-modules-2.6.20-16-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-backports-modules-2.6.20-16-generic 
  linux-image-2.6.20-16-generic{p} 
0 packages upgraded, 0 newly installed, 4 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 76.1MB will be freed.
Do you want to continue? [Y/n/?] ^[[  


EDIT: If that works, I should then run 'sudo aptitude purge linux-image-2.6.20-17-generic', and if that goes well, then run step 4 [one line at a time]?

---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> Thanks for the 'one line at a time' tip.
This laptop is a stand alone unit, other than a printer, router, and modem.
Look OK to y?
Thanks

Here's the latest:


EDIT: If that works, I should then run 'sudo aptitude purge linux-image-2.6.20-17-generic', and if that goes well, then run step 4 [one line at a time]?

I would say, yes to all questions...

---

### Post by Denny Johnson on 2010-04-12
Here's the result of entering y.
> Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 267001 files and directories currently installed.)
Removing libdns35 ...
Removing linux-backports-modules-2.6.20-16-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-backports-modules-2.6.24-25-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-25-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-25-generic
dpkg: error processing linux-backports-modules-2.6.24-25-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.24-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 



thought you better have a look before I proceed w 'sudo aptitude purge linux-image-2.6.20-17-generic' this  last action also generated a crash report, attached.
thanks

---

### Post by whoop on 2010-04-12
can you post output of
```

df -h

```
and
```

ls /boot

```

Cause it's still complaining about problems with space..
Maybe you could also try:
```

sudo aptitude clean

```

---

### Post by Denny Johnson on 2010-04-12
Here:
> denjohn@dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             143G   24G  112G  18% /
varrun               1009M  224K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M   44K 1009M   1% /dev/shm
/dev/sda3             193M  187M     0 100% /boot
tmpfs                1009M   40M  970M   4% /lib/modules/2.6.24-27-generic/volatile
/dev/sda2             2.0G  1.2G  891M  57% /media/OS
denjohn@dell:~$ ls /boot
abi-2.6.20-16-generic             initrd.img-2.6.24-22-generic.bak
abi-2.6.20-17-generic             initrd.img-2.6.24-23-generic
abi-2.6.22-15-generic             initrd.img-2.6.24-23-generic.bak
abi-2.6.24-19-generic             initrd.img-2.6.24-24-generic
abi-2.6.24-21-generic             initrd.img-2.6.24-24-generic.bak
abi-2.6.24-22-generic             initrd.img-2.6.24-25-generic
abi-2.6.24-23-generic             initrd.img-2.6.24-25-generic.bak
abi-2.6.24-24-generic             initrd.img-2.6.24-26-generic
abi-2.6.24-25-generic             initrd.img-2.6.24-26-generic.bak
abi-2.6.24-26-generic             initrd.img-2.6.24-27-generic
abi-2.6.24-27-generic             initrd.img-2.6.24-27-generic.bak
config-2.6.20-16-generic          lost+found
config-2.6.20-17-generic          memtest86+.bin
config-2.6.22-15-generic          System.map-2.6.20-16-generic
config-2.6.24-19-generic          System.map-2.6.20-17-generic
config-2.6.24-21-generic          System.map-2.6.22-15-generic
config-2.6.24-22-generic          System.map-2.6.24-19-generic
config-2.6.24-23-generic          System.map-2.6.24-21-generic
config-2.6.24-24-generic          System.map-2.6.24-22-generic
config-2.6.24-25-generic          System.map-2.6.24-23-generic
config-2.6.24-26-generic          System.map-2.6.24-24-generic
config-2.6.24-27-generic          System.map-2.6.24-25-generic
grub                              System.map-2.6.24-26-generic
initrd.img-2.6.20-16-generic      System.map-2.6.24-27-generic
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.22-15-generic
initrd.img-2.6.20-17-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.22-15-generic      vmlinuz-2.6.24-21-generic
initrd.img-2.6.22-15-generic.bak  vmlinuz-2.6.24-22-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-23-generic
initrd.img-2.6.24-19-generic.bak  vmlinuz-2.6.24-24-generic
initrd.img-2.6.24-21-generic      vmlinuz-2.6.24-25-generic
initrd.img-2.6.24-21-generic.bak  vmlinuz-2.6.24-26-generic
initrd.img-2.6.24-22-generic      vmlinuz-2.6.24-27-generic
denjohn@dell:~$ 


---

### Post by Denny Johnson on 2010-04-12
and
> denjohn@dell:~$ sudo aptitude clean
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
denjohn@dell:~$ 



---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> Here:

Huh? /boot is still full and some files we moved are still there.


try
```

sudo mv /boot/initrd.img-2.6.20-16-generic /root
sudo mv /boot/initrd.img-2.6.20-16-generic.bak /root
sudo mv /boot/initrd.img-2.6.20-17-generic.bak /root
df -h
sudo ls /boot/lost+found

```

---

### Post by Denny Johnson on 2010-04-12
the first 2 lines you asked for in post 34 are attached in perhaps easier to read format

---

### Post by Denny Johnson on 2010-04-12
want to be sure, should I run those 5 lines in your last post?

aaa...I see your edit, will do

---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> the first 2 lines you asked for are attached in perhaps easier to read format

Muah, I can read them just fine.
try:
```

sudo mv /boot/initrd.img-2.6.20-16-generic /root
sudo mv /boot/initrd.img-2.6.20-16-generic.bak /root
sudo mv /boot/initrd.img-2.6.20-17-generic.bak /root
df -h
sudo ls /boot/lost+found

```

---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> want to be sure, should I run those 5 lines in your last post?

Yep, they look like backups for old kernels...

---

### Post by Denny Johnson on 2010-04-12
attached

---

### Post by Denny Johnson on 2010-04-12
I think we like that 91%

---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> I think we like that 91%

Yes, we have some space (maybe we need more, we might need 25MB or so), try
```

sudo aptitude purge linux-image-2.6.20-16-generic

```
again.

---

### Post by Denny Johnson on 2010-04-12
ok
> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.20-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  linux-backports-modules-2.6.24-25-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-image-2.6.20-16-generic{p} 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.20-16-generic{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 75.7MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 266934 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-25-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-25-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
(Reading database ... 266934 files and directories currently installed.)
Removing linux-image-2.6.20-16-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /vmlinuz-2.6.22-15-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.20-16-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /vmlinuz-2.6.22-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.20-16-generic': Directory not empty
dpkg - warning: while removing linux-image-2.6.20-16-generic, directory `/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-16-generic, directory `/lib/modules/2.6.20-16-generic/kernel/sound/pci' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-16-generic, directory `/lib/modules/2.6.20-16-generic/kernel/sound' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-16-generic, directory `/lib/modules/2.6.20-16-generic/kernel' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-16-generic, directory `/lib/modules/2.6.20-16-generic' not empty so not removed.
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
denjohn@dell:~$ 


---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> ok

ok, it looks promissing.
do:
```

sudo aptitude search linux-image | grep "i "

```

---

### Post by Denny Johnson on 2010-04-12
here
> denjohn@dell:~$ sudo aptitude search linux-image | grep "i "
[sudo] password for denjohn: 
i A linux-image-2.6.20-17-generic   - Linux kernel image for version 2.6.20 on x
i   linux-image-2.6.22-15-generic   - Linux kernel image for version 2.6.22 on x
i   linux-image-2.6.24-19-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-21-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-22-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-23-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-24-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-25-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-2.6.24-26-generic   - Linux kernel image for version 2.6.24 on x
i   linux-image-2.6.24-27-generic   - Linux kernel image for version 2.6.24 on x
i A linux-image-generic             - Generic Linux kernel image                
denjohn@dell:~$ 




---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> here

Remove more kernels (-25 is still complaining, so we remove that too)
If I am not mistaken after this you will have two of the latest kernels installed (please check if this makes sense: 2.6.24-27-generic and 2.6.24-26-generic is what we want to keep):
```

sudo aptitude purge linux-image-2.6.20-17-generic
sudo aptitude purge linux-image-2.6.22-15-generic
sudo aptitude purge linux-image-2.6.24-19-generic
sudo aptitude purge linux-image-2.6.24-21-generic
sudo aptitude purge linux-image-2.6.24-22-generic
sudo aptitude purge linux-image-2.6.24-23-generic
sudo aptitude purge linux-image-2.6.24-24-generic
sudo aptitude purge linux-image-2.6.24-25-generic

```

---

### Post by Denny Johnson on 2010-04-12
here's the first, doing the others now> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.20-17-generic
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-restricted-modules-2.6.20-17-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.20-17-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 71.3MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.20-17-generic: Depends: linux-image-2.6.20-17-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-restricted-modules-2.6.20-17-generic

Score is -241

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-restricted-modules-2.6.20-17-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.20-17-generic{p} linux-restricted-modules-2.6.20-17-generic 
0 packages upgraded, 0 newly installed, 2 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 114MB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 264474 files and directories currently installed.)
Removing linux-restricted-modules-2.6.20-17-generic ...
(Reading database ... 264256 files and directories currently installed.)
Removing linux-image-2.6.20-17-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /vmlinuz-2.6.22-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.20-17-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /vmlinuz-2.6.22-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.20-17-generic': Directory not empty
dpkg - warning: while removing linux-image-2.6.20-17-generic, directory `/lib/modules/2.6.20-17-generic/kernel/sound/pci/hda' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-17-generic, directory `/lib/modules/2.6.20-17-generic/kernel/sound/pci' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-17-generic, directory `/lib/modules/2.6.20-17-generic/kernel/sound' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-17-generic, directory `/lib/modules/2.6.20-17-generic/kernel' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.20-17-generic, directory `/lib/modules/2.6.20-17-generic' not empty so not removed.
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by Denny Johnson on 2010-04-12
second
> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.22-15-generic
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-restricted-modules-2.6.22-15-generic 
  linux-ubuntu-modules-2.6.22-15-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.22-15-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 63.8MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.22-15-generic: Depends: linux-image-2.6.22-15-generic but it is not installable
  linux-ubuntu-modules-2.6.22-15-generic: Depends: linux-image-2.6.22-15-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-restricted-modules-2.6.22-15-generic
linux-ubuntu-modules-2.6.22-15-generic

Score is -172

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-restricted-modules-2.6.22-15-generic 
  linux-ubuntu-modules-2.6.22-15-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.22-15-generic{p} 
  linux-restricted-modules-2.6.22-15-generic 
  linux-ubuntu-modules-2.6.22-15-generic 
0 packages upgraded, 0 newly installed, 3 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 117MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 261796 files and directories currently installed.)
Removing linux-restricted-modules-2.6.22-15-generic ...
Removing linux-ubuntu-modules-2.6.22-15-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
(Reading database ... 261347 files and directories currently installed.)
Removing linux-image-2.6.22-15-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.22-15-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.22-15-generic': Directory not empty
dpkg - warning: while removing linux-image-2.6.22-15-generic, directory `/lib/modules/2.6.22-15-generic' not empty so not removed.
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> here's the first, doing the others now

looks good, only thing is that it seems to be leaving some crap in /lib/modules. That's not too bad (it won't clutter /boot). You can leave that or carefully remove it if you value your disk space.

---

### Post by Denny Johnson on 2010-04-12
third
> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.24-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-2.6.24-19-generic 
  linux-restricted-modules-2.6.24-19-generic 
  linux-ubuntu-modules-2.6.24-19-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.24-19-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 61.8MB will be freed.
The following packages have unmet dependencies:
  linux-backports-modules-2.6.24-19-generic: Depends: linux-image-2.6.24-19-generic but it is not installable
  linux-restricted-modules-2.6.24-19-generic: Depends: linux-image-2.6.24-19-generic but it is not installable
  linux-ubuntu-modules-2.6.24-19-generic: Depends: linux-image-2.6.24-19-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-2.6.24-19-generic
linux-restricted-modules-2.6.24-19-generic
linux-ubuntu-modules-2.6.24-19-generic

Score is 257

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-backports-modules-2.6.24-19-generic 
  linux-restricted-modules-2.6.24-19-generic 
  linux-ubuntu-modules-2.6.24-19-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-backports-modules-2.6.24-19-generic 
  linux-image-2.6.24-19-generic{p} 
  linux-restricted-modules-2.6.24-19-generic 
  linux-ubuntu-modules-2.6.24-19-generic 
0 packages upgraded, 0 newly installed, 4 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 128MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 259014 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-19-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-ubuntu-modules-2.6.24-19-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-restricted-modules-2.6.24-19-generic ...
(Reading database ... 258319 files and directories currently installed.)
Removing linux-image-2.6.24-19-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-19-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-19-generic': Directory not empty
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by Denny Johnson on 2010-04-12
no worries re disk space
Fourth:> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.24-21-generic
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-2.6.24-21-generic 
  linux-restricted-modules-2.6.24-21-generic 
  linux-ubuntu-modules-2.6.24-21-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.24-21-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 61.9MB will be freed.
The following packages have unmet dependencies:
  linux-backports-modules-2.6.24-21-generic: Depends: linux-image-2.6.24-21-generic but it is not installable
  linux-restricted-modules-2.6.24-21-generic: Depends: linux-image-2.6.24-21-generic but it is not installable
  linux-ubuntu-modules-2.6.24-21-generic: Depends: linux-image-2.6.24-21-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-2.6.24-21-generic
linux-restricted-modules-2.6.24-21-generic
linux-ubuntu-modules-2.6.24-21-generic

Score is 257

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-backports-modules-2.6.24-21-generic 
  linux-restricted-modules-2.6.24-21-generic 
  linux-ubuntu-modules-2.6.24-21-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-backports-modules-2.6.24-21-generic 
  linux-image-2.6.24-21-generic{p} 
  linux-restricted-modules-2.6.24-21-generic 
  linux-ubuntu-modules-2.6.24-21-generic 
0 packages upgraded, 0 newly installed, 4 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 132MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 256047 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-21-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-ubuntu-modules-2.6.24-21-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-restricted-modules-2.6.24-21-generic ...
(Reading database ... 255308 files and directories currently installed.)
Removing linux-image-2.6.24-21-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-21-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-21-generic': Directory not empty
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by Denny Johnson on 2010-04-12
fifth:
> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.24-22-generic
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-2.6.24-22-generic 
  linux-restricted-modules-2.6.24-22-generic 
  linux-ubuntu-modules-2.6.24-22-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.24-22-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 61.9MB will be freed.
The following packages have unmet dependencies:
  linux-backports-modules-2.6.24-22-generic: Depends: linux-image-2.6.24-22-generic but it is not installable
  linux-restricted-modules-2.6.24-22-generic: Depends: linux-image-2.6.24-22-generic but it is not installable
  linux-ubuntu-modules-2.6.24-22-generic: Depends: linux-image-2.6.24-22-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-2.6.24-22-generic
linux-restricted-modules-2.6.24-22-generic
linux-ubuntu-modules-2.6.24-22-generic

Score is 257

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-backports-modules-2.6.24-22-generic 
  linux-restricted-modules-2.6.24-22-generic 
  linux-ubuntu-modules-2.6.24-22-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-backports-modules-2.6.24-22-generic 
  linux-image-2.6.24-22-generic{p} 
  linux-restricted-modules-2.6.24-22-generic 
  linux-ubuntu-modules-2.6.24-22-generic 
0 packages upgraded, 0 newly installed, 4 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 132MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 253035 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-22-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-ubuntu-modules-2.6.24-22-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-restricted-modules-2.6.24-22-generic ...
(Reading database ... 252296 files and directories currently installed.)
Removing linux-image-2.6.24-22-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-22-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-22-generic': Directory not empty
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by Denny Johnson on 2010-04-12
sixth:
> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.24-23-generic
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-2.6.24-23-generic 
  linux-restricted-modules-2.6.24-23-generic 
  linux-ubuntu-modules-2.6.24-23-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.24-23-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 61.9MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.24-23-generic: Depends: linux-image-2.6.24-23-generic but it is not installable
  linux-ubuntu-modules-2.6.24-23-generic: Depends: linux-image-2.6.24-23-generic but it is not installable
  linux-backports-modules-2.6.24-23-generic: Depends: linux-image-2.6.24-23-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-2.6.24-23-generic
linux-restricted-modules-2.6.24-23-generic
linux-ubuntu-modules-2.6.24-23-generic

Score is 257

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-backports-modules-2.6.24-23-generic 
  linux-restricted-modules-2.6.24-23-generic 
  linux-ubuntu-modules-2.6.24-23-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-backports-modules-2.6.24-23-generic 
  linux-image-2.6.24-23-generic{p} 
  linux-restricted-modules-2.6.24-23-generic 
  linux-ubuntu-modules-2.6.24-23-generic 
0 packages upgraded, 0 newly installed, 4 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 133MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 250023 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-23-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-ubuntu-modules-2.6.24-23-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-restricted-modules-2.6.24-23-generic ...
(Reading database ... 249270 files and directories currently installed.)
Removing linux-image-2.6.24-23-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-23-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /vmlinuz-2.6.24-24-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-23-generic': Directory not empty
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by Denny Johnson on 2010-04-12
seven:
> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.24-24-generic
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-2.6.24-24-generic 
  linux-restricted-modules-2.6.24-24-generic 
  linux-ubuntu-modules-2.6.24-24-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.24-24-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 61.9MB will be freed.
The following packages have unmet dependencies:
  linux-backports-modules-2.6.24-24-generic: Depends: linux-image-2.6.24-24-generic but it is not installable
  linux-restricted-modules-2.6.24-24-generic: Depends: linux-image-2.6.24-24-generic but it is not installable
  linux-ubuntu-modules-2.6.24-24-generic: Depends: linux-image-2.6.24-24-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-2.6.24-24-generic
linux-restricted-modules-2.6.24-24-generic
linux-ubuntu-modules-2.6.24-24-generic

Score is 257

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-backports-modules-2.6.24-24-generic 
  linux-restricted-modules-2.6.24-24-generic 
  linux-ubuntu-modules-2.6.24-24-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-backports-modules-2.6.24-24-generic 
  linux-image-2.6.24-24-generic{p} 
  linux-restricted-modules-2.6.24-24-generic 
  linux-ubuntu-modules-2.6.24-24-generic 
0 packages upgraded, 0 newly installed, 4 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 134MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 246997 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-24-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-24-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-ubuntu-modules-2.6.24-24-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-24-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-restricted-modules-2.6.24-24-generic ...
(Reading database ... 246240 files and directories currently installed.)
Removing linux-image-2.6.24-24-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-24-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /vmlinuz-2.6.24-25-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-24-generic': Directory not empty
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by Denny Johnson on 2010-04-12
eight:
> denjohn@dell:~$ sudo aptitude purge linux-image-2.6.24-25-generic
[sudo] password for denjohn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-restricted-modules-2.6.24-25-generic 
  linux-ubuntu-modules-2.6.24-25-generic 
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.24-25-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 61.9MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.24-25-generic: Depends: linux-image-2.6.24-25-generic but it is not installable
  linux-ubuntu-modules-2.6.24-25-generic: Depends: linux-image-2.6.24-25-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-restricted-modules-2.6.24-25-generic
linux-ubuntu-modules-2.6.24-25-generic

Score is -172

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be automatically REMOVED:
  linux-restricted-modules-2.6.24-25-generic 
  linux-ubuntu-modules-2.6.24-25-generic 
The following packages have been kept back:
  firefox firefox-gnome-support libkrb53 tzdata 
The following packages will be REMOVED:
  linux-image-2.6.24-25-generic{p} 
  linux-restricted-modules-2.6.24-25-generic 
  linux-ubuntu-modules-2.6.24-25-generic 
0 packages upgraded, 0 newly installed, 3 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 130MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 243967 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-25-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-25-generic
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
eval: 1: array_udev.orig=: not found
eval: 1: Bad substitution
Removing linux-restricted-modules-2.6.24-25-generic ...
(Reading database ... 243269 files and directories currently installed.)
Removing linux-image-2.6.24-25-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-25-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-27-generic
Found kernel: /vmlinuz-2.6.24-26-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-25-generic': Directory not empty
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
denjohn@dell:~$ 


---

### Post by whoop on 2010-04-12
OK, that was that right?
now:
```

sudo dpkg --configure -a
ls /boot
ls /root
df -h

```

---

### Post by Denny Johnson on 2010-04-12
and
> denjohn@dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             143G   22G  113G  17% /
varrun               1009M  224K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M   44K 1009M   1% /dev/shm
/dev/sda3             193M   40M  144M  22% /boot
tmpfs                1009M   40M  970M   4% /lib/modules/2.6.24-27-generic/volatile
/dev/sda2             2.0G  1.2G  891M  57% /media/OS
denjohn@dell:~$ ls /boot
abi-2.6.24-26-generic             initrd.img-2.6.24-27-generic.bak
abi-2.6.24-27-generic             lost+found
config-2.6.24-26-generic          memtest86+.bin
config-2.6.24-27-generic          System.map-2.6.24-26-generic
grub                              System.map-2.6.24-27-generic
initrd.img-2.6.24-26-generic      vmlinuz-2.6.24-26-generic
initrd.img-2.6.24-26-generic.bak  vmlinuz-2.6.24-27-generic
initrd.img-2.6.24-27-generic
denjohn@dell:~$ 



---

### Post by Denny Johnson on 2010-04-12
> denjohn@dell:~$ sudo dpkg --configure -a
[sudo] password for denjohn: 
denjohn@dell:~$ ls /boot
abi-2.6.24-26-generic             initrd.img-2.6.24-27-generic.bak
abi-2.6.24-27-generic             lost+found
config-2.6.24-26-generic          memtest86+.bin
config-2.6.24-27-generic          System.map-2.6.24-26-generic
grub                              System.map-2.6.24-27-generic
initrd.img-2.6.24-26-generic      vmlinuz-2.6.24-26-generic
initrd.img-2.6.24-26-generic.bak  vmlinuz-2.6.24-27-generic
initrd.img-2.6.24-27-generic
denjohn@dell:~$ ls /root
initrd.img-2.6.20-16-generic      initrd.img-2.6.20-17-generic.bak
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-17-generic      vmlinuz-2.6.20-17-generic
denjohn@dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             143G   22G  113G  17% /
varrun               1009M  224K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M   44K 1009M   1% /dev/shm
/dev/sda3             193M   40M  144M  22% /boot
tmpfs                1009M   40M  970M   4% /lib/modules/2.6.24-27-generic/volatile
/dev/sda2             2.0G  1.2G  891M  57% /media/OS
denjohn@dell:~$ 

?

---

### Post by Denny Johnson on 2010-04-12
I hope that was that......but am unclear what next.......try to install upgrades that I could not install before?

---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> ?

OK, /boot looks peachy
Now remove those files from root:
```

sudo rm /root/initrd.img-*
sudo rm /root/vmlinuz-*

```

Then try if updating works again...
```

sudo aptitude update && sudo aptitude safe-upgrade

```

---

### Post by Denny Johnson on 2010-04-12
> denjohn@dell:~$ sudo rm /root/initrd.img-*
[sudo] password for denjohn: 
denjohn@dell:~$ sudo rm /root/vmlinuz-*
denjohn@dell:~$ 


will try install now

---

### Post by Denny Johnson on 2010-04-12
B-I-N-G-O....................................we've got a winner, updates installed.

---

### Post by whoop on 2010-04-12
:guitar: It's been fun :lolflag:

---

### Post by Denny Johnson on 2010-04-12
Well, whoop, I want to extend a very sincere THANK YOU for walking me thru all of that.
It's the kindness, generosity, and persistence of the more knowledgeable here that help keep the spirit of Ubuntu alive.
Best wishes
Denny

---

### Post by Denny Johnson on 2010-04-12
Just re booted, all seems well.
thanks again

---

### Post by whoop on 2010-04-12
> **Denny Johnson said:**
> Well, whoop, I want to extend a very sincere THANK YOU for walking me thru all of that.
It's the kindness, generosity, and persistence of the more knowledgeable here that help keep the spirit of Ubuntu alive.
Best wishes
Denny

No problem...

---

