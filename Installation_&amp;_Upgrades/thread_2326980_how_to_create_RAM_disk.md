---
title: "how to create RAM disk"
date: 2016-06-06
forum: Installation &amp; Upgrades
---

### Post by ashok19 on 2016-06-06
hi all,
Can someone please guide me on creating a RAM Disk on Ubuntu 12.04 and run OS from RAM?

Thanks
Ashok

---

### Post by QDR06VV9 on 2016-06-06
Have a look here step by step.
[http://www.hecticgeek.com/2015/12/create-ram-disk-ubuntu-linux/](http://www.hecticgeek.com/2015/12/create-ram-disk-ubuntu-linux/)

---

### Post by ashok19 on 2016-06-06
Thanks for the link but i wan my RAM disk to act as a new root (having said that the new root should contains the file system, right? and i wan to run the Os from new root.

---

### Post by QDR06VV9 on 2016-06-06
> **ashok19 said:**
> Thanks for the link but i wan my RAM disk to act as a new root (having said that the new root should contains the file system, right? and i wan to run the Os from new root.

No, that's why SSDs were created. RAM disks are created by an OS, the firmware that POSTs and boots the PC knows nothing about them. So to do that literally, you would need custom firmware to create the RAM disk and then it would have to load the data from some nonvolatile storage into the RAM disk before booting.

You could skip the custom firmware part and boot from another device (e.g. USB stick, CD, etc) and have that load the OS and data into a RAM disk. Most Linux Live CDs do something similar now. But the boot times are longer than normal because of the need to read everything from the other media into memory.

**(Just in case this is what you want) **Windows is a whole other beast because it wasn't made to run that way. WinPE kinda does this, but it's very limited in functionality because it was only designed for installation onto nonvolatile media. You would have to do a significant amount of hacking to make Win7 run straight from a RAM disk. 
Anyway this is way above my pay grade:)

---

### Post by ashok19 on 2016-06-06
I got it. Actually my point here is creating a RAM disk , creating a new root. unmount the old root. Zap SSD (cleaning up everything), creating a partition and loading the OS from NFS. 
I know zapping , creating new partition and loading Os from NFS but i don;t know the procedure to creating RAM disk which hold kernel and necessary files to boot from NFS till i reload the OS.

1) creating new root  on RAM disk
2) mounting/ copying a necessary files (idk , i know i need bin, sbin, dev, proc, sys...do i need to copy initrd.img from /boot) how to call grub?
3)  pivot_root . oldroot4) umount /oldroot

kill everything from old root (Note: need to send msg on screen "DO NOT REBOOT THE SYSTEM" since we are running on RAMDISK

5)mount nfs
dd if=/dev/zero of=/dev/sda bs=1024 count=1000  zapping
creating partition/FS
loadin OS

Correct me if i ma wrong here

---

### Post by sudodus on 2016-06-06
To run a live system from RAM is very easy: add the boot option **toram**

***Edit:*** Maybe this link is interesting for you

[Making Ubuntu Fast using RAM (updated and simplified)](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by ashok19 on 2016-06-07
Does anyone every boot the Ubuntu through RAM? Creating RAM disk and creating the new root and umounting the oldroot?

---

### Post by deadflowr on 2016-06-07
Probably something along the lines of what your are looking for:
[http://ubuntuforums.org/showthread.php?t=1594694]("http://ubuntuforums.org/showthread.php?t=1594694")

edit: ninja'd.
probably should read through the thread. lol

Somehow, though, it seems like you want a mix of ltsp and ramdisk.
If that makes any sense.

---

### Post by yoshii on 2016-06-07
This is an interesting topic to me.  

I just wanted to point out that Solid State Drives are fast on reads, but slow on writes, as is typical for NAND hardware logic.  Volitile RAM I believe is faster than SSD on both reads and writes.  The downside is that CPU load for RAM drives can sometimes be higher depending upon how they work.  But usually a person can do interesting things with a lot of nice RAM.  

If you guys don't find the right answer from the links you provided above, there might be some insights from the Puppy Linux developers since Puppy Linux can typically be optionally booted and run entirely via RAM.  And there are some versions of Puppy Linux which are very much compatible with Ubuntu.  It just depends upon which type of Puppy.  Others are based upon Arch Linux or Slackware Linux or Debian Linux.   

Anyways, I'd like to know also.  I will try out the "toram" kernel boot option and research that.

---

### Post by ashok19 on 2016-06-14
Thanks Yoshi,
Puppy Linux, i will google more about it. I want to share something. i am trying to create a RAM disk and create a new root copy all the root file on new root and chroot the new root. while doing so i got stuck. can anyone please tell me where i'm doing wrong.



   # Create new root on the ramdisk
   echo "Setting up new root  . . ."
   if [ ! -e /newroot ]; then
           mkdir /newroot
   fi


   mount nodev /newroot -t tmpfs




   cp -a /bin/ /sbin/ /etc/ /lib64/ lib32/ /lib/ /newroot


   mkdir -p /newroot/usr/lib
   cp -a /usr/lib/* /newroot/usr/lib


   mkdir -p /newroot/usr/bin
   cp -a /usr/bin/* /newroot/usr/bin


   mkdir -p /newroot/usr/sbin
   cp -a /usr/sbin/* /newroot/usr/sbin


   cd /newroot
   mkdir proc oldroot sys var writable dev


   mount --bind /proc    /newroot/proc
   mount --bind /dev    /newroot/dev
   mount --bind /sys     /newroot/sys


   mount -t tmpfs none writable
   cp -a /writable/* writable/


   umount /newroot/writable/




   mount -t tmpfs none var
   cp -a /var/* var/
   ln -s var/tmp tmp


 chroot /newroot update-grub
 chroot /newroot grub-install /dev/sda
echo "Checking Grub Installation"
   if  chroot /newroot grub-install --recheck /dev/sda
   then
      echo -e "Leaving Chroot, disk is ready\n"
   else
      echo -e "Leaving Chroot, FAILURE in grub setup detected\n"
   fi
 GOT this ERROR,

Setting up new root  . . .
/usr/sbin/grub-mkconfig: 98: .: Can't open /usr/share/grub/grub-mkconfig_lib
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
Checking Grub Installation
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
Leaving Chroot, FAILURE in grub setup detected

---

