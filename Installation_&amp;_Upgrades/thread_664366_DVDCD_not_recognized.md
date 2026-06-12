---
title: "DVD/CD not recognized"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by pclark36 on 2008-01-11
I just installed 7.10 from 7.04 on my Averatec 4100.  I had to do an upgrade because something in the 7.10 install does not like my CD drive.  My dvd/cdrw drive worked great in 7.04, but now to 7.10, it's gone.  My hard drive shows up as a SCSI drive and is relatively slow.  But my biggest problem is the dvd drive, it will boot a livecd of 7.04 from the DVD drive, but when 7.10 loads from the hard drive, I can't find the dvd...anyone have a similar experience that they could possibly lead me in the right direction?


Thanks,

---

### Post by pclark36 on 2008-01-13
I'm gonna bump this...The laptop will boot a liveCD, so it's connected, and the computer knows it's there.  I'm just thinking it has something to do with everything showing up as SATA now.  I fixed this one time by adding hwprobe=-modules.pata to my commands in the kernel at boot, but with 7.10, it won't keep the commands that I put in it...

Here's the output from cat /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c3e3783a-b38d-40b1-87a5-73392daeef43 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=68085da8-8889-471c-98fd-ac2b97e0d2ee none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



output from lshw -C dsk
>   *-disk                  
       description: SCSI Disk
       product: IC25N020ATCS04-0
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: CA2O
       serial: CSH204DMGNM29F
       size: 18GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5


---

### Post by Partyboi2 on 2008-01-13
> I fixed this one time by adding hwprobe=-modules.pata to my commands in the kernel at boot, but with 7.10, it won't keep the commands that I put in it...When ever you add a boot option to the kernel at boot time, it is only valid for that one boot. For a kernel boot option to be used all the time, you need to add it to grub menu.lst so that it will always use that option.
Open up /boot/grub/menu.lst
In a terminal
```
gksudo  gedit /boot/grub/menu.lst
```look for something like this:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Blue]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro[/COLOR]add your boot option to the end after ro
so
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Blue]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro [COLOR=Red]hwprobe=-modules.pata
[/COLOR][/COLOR]save
then update grub
```
sudo update-grub
```

---

### Post by pclark36 on 2008-01-13
Ok,

Now it's wierd.  If I boot into the 2.6.20-16 generic kernel, it finds my CD drive fine.  Again, something to do with the embedded SATA drivers I'm sure.  

Is there any way to find the UUID of my CDRW/DVDRW drive so I can edit my /etc/fstab accordingly?

---

### Post by pclark36 on 2008-01-14
> **Partyboi2 said:**
> When ever you add a boot option to the kernel at boot time, it is only valid for that one boot. For a kernel boot option to be used all the time, you need to add it to grub menu.lst so that it will always use that option.
Open up /boot/grub/menu.lst
In a terminal
```
gksudo  gedit /boot/grub/menu.lst
```look for something like this:
add your boot option to the end after ro
so
save
then update grub
```
sudo update grub
```

The update grub command does not exist, would restarting have the same effect?  

Nevermind, the command is > update-grub

---

### Post by smittymoo on 2008-04-06
I'm having the same issue. I upgraded from 7.04 (feisty) to 7.10 (gutsy). Previously CD/DVD worked great. now disks are not recognized.

/etc$ sudo lshw

*-cdrom
                description: DVD writer
                product: DVD+-RW AD-5540A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 102C
                serial: [Optiarc DVD+-RW AD-5540A102C Jul04,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom


/etc$ gedit fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0

Bear in mind I'm a complete n00b when it comes to Linux...

thanks
Smitty

---

### Post by smittymoo on 2008-04-06
ok I'm now farther along..... I made the following changes
I added 

/dev/scd0       /media/cdrom    udf,iso9660     user,auto       0       0

to my fstab file, and I had to create the cdrom directory by command

sudo mkdir /media/cdrom

I can now manually mount the cdrom/dvd and get it to work... unfortunately it doesn't auto mount at this time.....

****** EDIT *******
Disregard. I found out the version of Wubi I was using is not upgradeable.
I downloaded a newer version of Wubi and deleleted and re-installed Ubuntu to the 8.04 Hardy and all is well...

---

