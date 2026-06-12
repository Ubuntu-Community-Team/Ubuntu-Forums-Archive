---
title: "andlinux version 10"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by achnö on 2010-09-28
Hi,

I wanna use andlinux, so I installed. But in the original is ubuntu 8 so I upgraded to 10. It works well, but after a reboot from windows I get the following Error. So I need your help.

[ATTACH]170719[/ATTACH]

greets achnö

---

### Post by Rubi1200 on 2010-09-28
Hi and welcome to the forums :)

Honestly, you might be better asking this question on the andLinux forums.

That said, do you have a LiveCD or can you get one?

If so, post the results of the bootscript linked at the bottom of my post.

Thanks.

---

### Post by achnö on 2010-09-28
hi,

I've get the script running. So hopefully you can help.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/cobd0       7991934f-41f3-41dc-bba3-e2ad5b9e41aa   ext3                                     
error: /dev/hda: No such device or address
error: /dev/hdb: No such device or address
error: /dev/hdc: No such device or address
error: /dev/hdd: No such device or address
error: /dev/hde: No such device or address
error: /dev/hdf: No such device or address
error: /dev/hdg: No such device or address
error: /dev/hdh: No such device or address
error: /dev/sda: No such device or address
error: /dev/sdb: No such device or address
error: /dev/sdc: No such device or address
error: /dev/sdd: No such device or address
error: /dev/sde: No such device or address
error: /dev/sdf: No such device or address
error: /dev/sdg: No such device or address
error: /dev/sdh: No such device or address

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/cobd0       /                        ext3       (rw)
/dev/cofs0       /mnt/win                 unknown    (rw)

=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd hde hdf hdg hdh sda sdb sdc sdd sde sdf sdg sdh 

```

greets achnö

---

### Post by Rubi1200 on 2010-09-28
I must admit I am a bit surprised by the results. Although I have no experience with andLinux, I expected Windows to show up in the results at the very least.

Can you boot into Windows?

---

### Post by achnö on 2010-09-28
hi,

I looked before in the forum for a resolution and find a problem like mine. 

[http://ubuntuforums.org/showthread.php?t=1485990&highlight=797+mountall](http://ubuntuforums.org/showthread.php?t=1485990&highlight=797+mountall)

So I get this from the other forum.

```
I had the same problem. I think it is either wrong kernel installed or a wrong initrd. 
 
1. log in to rescue shell 
 
2. mount -o remount,rw / 
 
3. mkdir /var/run/network 
     ifup eth0 
 
Networking required for apt-get. I was missing /var/run/network after upgrade, not sure why. 
 
4. apt-get install linux-image-virtual 
 
This will provide the right kernel and run update-initramfs. It will fail but that's enough to get a normal boot. 
 
5. reboot 
 
6. apt-get -f install 
 
To complete the kernel installation. 
 
```

So I get network and transferd through ftp the files. But isn't the solution of my problem the things didn't work. But I think is the same problem but I haven't any grub. And didn't understand mbernstein wrote.

greets achnö

---

