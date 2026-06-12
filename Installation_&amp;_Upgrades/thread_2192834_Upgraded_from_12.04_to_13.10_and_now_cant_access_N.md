---
title: "Upgraded from 12.04 to 13.10 and now cant access NTFS partition"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by chkneater on 2013-12-09
Well the title says it...  I used the live CD and intended to install 13.10 ALONGSIDE 12.04 and instead it overwrote it.  I'm sure that I chose the right partition and chose the option to have both file systems but for some reason it errored.  Anyway, I have 13.10 running and it is good, all my files were kept mostly and my NTFS partion IS still showing up in gparted so it has not been overwrote I just have no way of accessing it, no icon or menu selection.  I checked synaptic and the forums and have not gotten any help so far.  Thanks for any help!

---

### Post by rackit on 2013-12-09
Is it still in your fstab (/etc/fstab)? It's not being mounted automatically, is my first thought. Here are [some great fstab docs]("https://help.ubuntu.com/community/Fstab") to get you moving in the right direction.

---

### Post by chkneater on 2013-12-10
I added the UUID to the fstab manually and ran 'mount -a' and got this result:

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.


I don't know what fuser is but does this make any sense?

BTW I'm not sure if I added the fstab entry correctly, here's what I added:

#NTFS partition
UUID=0F7E28FD4094875B none ntfs                         

I couldn't think of a mount point so i just put none and the UUID's of NTFS are different than ext4 filesystems?

---

### Post by rackit on 2013-12-10
An example that might work: 
UUID=0F7E28FD4094875B /media/windows ntfs defaults,locale=en_US.utf8 0 0 this will mount it in /media/windows ad it and reboot.

---

### Post by Mark Phelps on 2013-12-10
What version of Windows are you running? If it's Win8, that message means that your Windows partition is hibernated -- and since, under Win8, that means it remains mounted, Linux won't let you mount it again. You have to disable hibernation in order to mount that partition in Linux.

---

### Post by chkneater on 2013-12-10
I am not using windows at all and have not had windows on this comp in 7 years so I doubt it is related to that...  I noticed after editing the fstab I started getting "mount denied" whereeas before 'mount -a' wouldn't give anything back.  overnight I used gparted to clone the ntfs partition, here's the weirder part... while the partions were being cloned, the NEW NTFS showed up on the desktop UNTIL the operation was complete, then it went away, now I get TWO "mount denied" messages since I now have two NTFS's.  I'm going to delete one, but I think this shows fsab may be the prob, I would re-edit with those commands but I don't like having windows as a mount point, is that my only choice? thanx again for the help!!

I changed one NTFS partition the way Jerry suggested and left the other alone, this is the result with 'mount -a':fuse:

 failed to access mountpoint none: No such file or directory
mount: mount point 0 does not exist
fuse: failed to access mountpoint /media/windows: No such file or directory
mount: mount point 0 does not exist

I guess fstab is not the problem maybe?

---

### Post by Morbius1 on 2013-12-10
If you did this:
> UUID=0F7E28FD4094875B /media/windows ntfs defaults,locale=en_US.utf8 0 0
*** Run the following command to get the correct UUID number for your partition:
```
sudo blkid -c /dev/null
```
**** And based on the error message you got make sure the mount point exists:
```
sudo mkdir /media/windows
```

---

### Post by chkneater on 2013-12-10
Thanks Morbius, I did have the correct UUID but after making the media/windows directory I now get only this:

mount: mount point 0 does not exist
mount: mount point 0 does not exist

I guess that is some progress

---

### Post by Morbius1 on 2013-12-10
please post the output of the following command:
```
cat /etc/fstab
```

---

### Post by chkneater on 2013-12-10
The NTFS partitions show up in gparted but I can't unmount either of them and I need to delete one of them so I can repartition it...  I still can;t access either file system though they are both mounted as /media/windows

Here's that output Morbius (note: sda4 is the NTFS I cloned which is sda3, I manually changed the mount point of sda4 to none myself, but it was mounted as /windows before i changed it)

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=b3d209ef-b581-43a5-bade-ede9b88fde61 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
#UUID=8f71f24f-6950-48fd-a6be-5da054b2cfff /boot           ext4    defaults        0       2
# /windows was on /dev/sda4 during installation
UUID=0F7E28FD4094875B none        ntfs    
defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=06ffce0d-c058-4928-8ea1-17968c8aa3cf none            swap    sw              0       0
#NTFS partition
UUID=0F7E28FD4094875B /media/windows ntfs         
defaults,locale=en_US.utf8 0 0

So I changed fstab so sda4 was mounted /media/windows and now it mounts at boot, but it won't unmount and now sda3 has unallocated space and is preventing it from being used or unmounted, thus I can't resize it to fix it? 

UUID=b3d209ef-b581-43a5-bade-ede9b88fde61 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
#UUID=8f71f24f-6950-48fd-a6be-5da054b2cfff /boot           ext4    defaults        0       2
# /windows was on /dev/sda4 during installation
UUID=0F7E28FD4094875B /media/windows       ntfs    
defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=06ffce0d-c058-4928-8ea1-17968c8aa3cf none            swap    sw              0       0
#NTFS partition
UUID=0F7E28FD4094875B /media/windows ntfs         
defaults,locale=en_US.utf8 0 0

Ok, I just edited the fstab for the second line on sda3 to copy sda4 and now they both are mounting and unmounting and I am able to delete and move the partitions I need to.

Thanks for the help everyone, much appreciation!!

---

