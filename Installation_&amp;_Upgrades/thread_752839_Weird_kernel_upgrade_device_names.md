---
title: "Weird kernel upgrade device names"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by lavacano on 2008-04-12
This is solved but [COLOR=Red]_**someone less lazy than I should file a bug report**_[/COLOR] becuase it is pretty major!  naming conventions (post 2.6.15/6.06) move IDE hdd's to sd*!  I fixed my problem by changing my /etc/mdadm/mdadm.conf to
> 
 cat /etc/mdadm/mdadm.conf
DEVICE partitions
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=d9e13672:329c9103:f35e8311:fd6bd579
   devices=/dev/sdb1,/dev/sda2
MAILADDR root
and issuing a update-initramfs -u now im sitting pretty happy ---Linux chadwick 2.6.24-16-386 #1 Thu Apr 10 12:50:06 UTC 2008 i686 GNU/Linux YAY
> 
so in 2.6.15-51-386 i believe is 6.06 my sata is sda.  ALL KERNELS AFTER it is sdb 

My setup i have the soft raid across my 1 ide drive (hdc) and my sata (sda).  

My question is in the kernels after 2.6.15 do ide devices get renamed to sd instead of hd?  what am I missing here?  I'm having to boot into 2.6.15 atm.  I've tried everything, updating initram making sure my uuid is correct....

When I boot into recovery mode on the newer kernels the last print is md0 has stopped.  above that I can clearly see that my sata drive is referenced as sdb so it freaking changes.  

in kernel 2.6.15 I have
[quote]
$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2

$ ls /dev/hd*
/dev/hda  /dev/hdb  /dev/hdc  /dev/hdc1  /dev/hdc2
I cant boot into 2.6.17 or 2.6.24 so I cant even tell what the device names are.  I'm pretty sure my problem is that the kernel is changing the device named on both my hdd.  but I know how people in forums mostly like to pull red herrings across these problems so I'll post everything I got.
> 
# mdadm --detail --scan
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=d9e13672:329c9103:f35e8311:fd6bd579

# cat /etc/mdadm/mdadm.conf
DEVICE partitions
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=d9e13672:329c9103:f35e8311:fd6bd579
   devices=/dev/sda1,/dev/hdc2
MAILADDR root

# cat /proc/mdstat
Personalities : [raid0] 
md0 : active raid0 sda1[0] hdc2[1]
      156207808 blocks 64k chunks
      
unused devices: <none>

# apt-get install udev mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
udev is already the newest version.
mdadm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Maybe if this doesnt get answered in a timely fashion I'll download a newer install CD with a newer kernel so the device names don't change when I upgrade.  pfffffffffft.  

What I really just want to know is if the naming changed from 2.6.15 to 2.6.17 I'm pretty sure it did and the correct device nodes are probably going to be (hdc)--->sda (sda)--->sdb .  In which case all I have to do is update mdadm.conf with that info and do a update-initramfs -u .  

Thanks for your time and cooperation
[/quote]

---

### Post by lavacano on 2008-04-12
so I think I'm right

[http://ubuntuforums.org/archive/index.php/t-390002.html](http://ubuntuforums.org/archive/index.php/t-390002.html)

Maybe the developers could update the mdadm package in respect to kernel upgrades?  Thats a nice thought :-)

---

### Post by jameso on 2008-05-04
I also experienced these problems when upgrading from dapper 6.06 to hardy 8.04.

I use software raid 1, and after upgrading I was unable to boot into the new 2.6.24-16 kernel.

I was able to boot off the previous kernel (2.6.15-51) though.

I think for now I'll just keep running 2.6.15-51.

---

### Post by lavacano on 2008-05-04
well you can always wait for the initramfs busybox and issue a

mdadm --assemble /dev/md(#) /dev/sd(a-z)(#) /dev/sd(a-z)(#)

so mine used to be with the 2.6.15

mdadm --assemble /dev/md0 /dev/hda1 /dev/sda2

now it is

mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb2

so what happened was hda1 -> sda1  and sda2 -> sdb2

but I dont think the dev's were counting on a mixed interface soft raid...

---

