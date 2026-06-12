---
title: "No Grub No Ubuntu ...."
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by testingubuntu on 2005-05-19
Hi all As you can tell from my ID I'm testing out Ubuntu.   I'm a regular Fedora Cora User that wanted to explore different linux OS's.  

Went through the install  I created my own partitions  

/boot 100 mb
/swap 2000 mb
/root  18000 mb 

Install went fine till it came time to install grub  the installer wants to install grub in the mbr.  Nope not gonna happen.   To many issue with the mbr and linux to mess it up.  I wanted to install grub on my /boot patition.  the installer would NOT allow me to do this. It wanted to install to the mbr.  So after fartingaround with it I decided  to let it install to the mbr.  well It wouldn't install Seems you only get 1 chance to install grub only to the mbr.  Not good in my book.  So, I allowed it to finish the install, and rebooted.  Well the grub terminal window came up. So i Go Hmmm, lets try grub-install /dev/hda6 <--- boot patition  nope not gonna happen.  So i have to dig out my XP CD ru nthe fixmbr.  Believe me if I could, I would dump XP all together but my job requires me to have it. Suck yes i know... So this where I'm at ...

running off the Live CD as of now trying to follow these instructions here 

[http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows](http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows) 

Got to this part  

> mount /dev/hda4 /mnt/work  <--- got this far 
mount -o bind /dev /mnt/work/dev <--- doesn't work 
mount -o bind /proc /mnt/work/proc
cp /proc/mounts /mnt/work/etc/mtab 

output from the terminal 

> root@ubuntu:/ # mount /dev/hda6 /mnt/work
root@ubuntu:/ # mount -o bind /dev /mnt/work/dev
mount: mount point /mnt/work/dev does not exist 

I read on a bit further  ...
> Configuring the GRUB Menu

Note: This step does not need to be done if you're just trying to recover your MBR. Installing Windows will not alter the contents of your existing menu.lst, so if everything was working right before, everything will continue to work right now, and you can restart your computer.

Open the GRUB menu file, /boot/grub/menu.lst, with your favourite text editor. An example follows.

nano /boot/grub/menu.lst  

Sorry ther is no menu.list file  i have a device.map file with this in it 
[B]
(hd0)   /dev/hda[/B]
~

out put of fdik -l  
```

root@ubuntu:~ # fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/hda2            1531        4547    24234052+   f  W95 Ext'd (LBA)
/dev/hda5            1531        2104     4610623+   b  W95 FAT32
/dev/hda6            2105        2116       96358+  83  Linux <--boot
/dev/hda7            2117        2359     1951866   83  Linux <-- swap
/dev/hda8            2360        4547    17575078+  83  Linux <--- root

root@ubuntu:~ #
``` 

Other than re-installing Ubuntu and trying the grub deal again, How would one of the ubuntu gurus fix this issue?  

Once again thanks for your time... 

Jim

---

### Post by testingubuntu on 2005-05-19
> 
Now, you have to enter your working environment. The following command will take care of that.

chroot /mnt/work/ /bin/bash 
  

says /bin/bash  no such file or directory    So must be something isn't mounted 


any Ideas

---

### Post by alastair on 2005-05-19
You say :

"mount /dev/hda4 /mnt/work <--- got this far "

But there is no /dev/hda4 in your fdisk list. I am confused.

"chroot /mnt/work/ /bin/bash"

Assuming your new root (/) is mounted on "/mnt/work", try just :

chroot /mnt/work

also :

mount -o bind /dev /mnt/work/dev

won't work because /boot and / (for /dev) are on different partitions for you (/ not mounted).

So ... try :

mkdir /mnt/boot
mkdir /mnt/root

root@ubuntu:/ # mount /dev/hda6 /mnt/boot
root@ubuntu:/ # mount /dev/hda8 /mnt/root
root@ubuntu:/ # mount -o bind /dev /mnt/root/dev
root@ubuntu:/ # mount -o bind /proc /mnt/root/proc

and when you want to chroot :

root@ubuntu:/ # chroot /mnt/root

I have to admit that I have not looked at the docs you reference however ....


On an install (at least "expert"), you can say "no" to installing GRUB and choose to install on a floppy (say) i.e. /dev/fd0

---

