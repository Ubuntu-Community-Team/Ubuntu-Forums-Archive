---
title: "mounting none on /dev failed"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by ace_ventura on 2010-05-01
I updated from 9.10 karmic to 10.04 LTS. Everything worked fine until, I  restarted. when i go into grub loader the screen says 
mount mounted none on/dev failed.
after that lots of text shows up then the login screen comes up.
i am pretty new to linux, so have no idea what's wrong.
found in different forum to check for 
cat /etc/fstab

and
sudo fdisk -l 

i am posting the results for both below. any help?

faisal@FAISAL:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1449099b-b62c-48ea-8031-a66ab724314c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=79ce4aac-d3f6-48bc-a9d8-0623ac41c012 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
faisal@FAISAL:~$ 

faisal@FAISAL:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xafedd08a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc35cd64f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       61590   494714880    7  HPFS/NTFS
/dev/sdb2           61590       85905   195312500    7  HPFS/NTFS
/dev/sdb3           85906      121601   286728120    5  Extended
/dev/sdb5           85906      120150   275072931   83  Linux
/dev/sdb6          120151      121601    11655126   82  Linux swap / Solaris
faisal@FAISAL:~$ 

can you explain pls?
is there any way to get rid of this?

---

### Post by squeakusmaximus on 2010-05-02
Hey, the entry in menu.lst is pointing at the wrong kernel. you can fix it by editing it (sudo nano /boot/grub/menu.lst) and replacing any entries for 2.6.31-21 (or whatever your previous kernel was) with 2.6.32-21. Hope that works for you!

---

### Post by bouncingmolar on 2010-05-02
> **squeakusmaximus said:**
> Hey, the entry in menu.lst is pointing at the wrong kernel. you can fix it by editing it (sudo nano /boot/grub/menu.lst) and replacing any entries for 2.6.31-21 (or whatever your previous kernel was) with 2.6.32-21. Hope that works for you!

Hi, I'm having exactly the same problem after upgrading. That solution doesn't work. It just stops my ubuntu from loading at all, so I had to edit in grub back to 31 and push b to boot and then edit in nano again to save the changes. 

My problem is the same as the other guys: 

I get that message and no boot screen picture. it goes red and has ubuntu in normal text with four fullstops under which turn red as it loads and then ubuntu loads as normal.

exerpt from grub: 

title Kubuntu
root (hd0,0)
kernel /boot/vmlinuz-2.6.31-16-generic root=UUID=ebbb15ea-b592-413b-b9bf-dfd02bdf88b7 ro quiet splash
initrd /boot/initrd.img-2.6.31-16-generic

---

### Post by ace_ventura on 2010-05-02
GNU nano 2.2.2           File: /boot/grub/menu.lst                            




















                                  [ New File ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


this happens when i type the above mentioned command.

i have no idea what that means. i am very new to linux.

---

### Post by squeakusmaximus on 2010-05-03
hey,
bouncingmolar, could you show me what config files are in your boot folder? (from the terminal: ls /boot), if nothing is happening it might be pointing at the wrong kernel
aceventura, normally that file is where it lists the options at startup (ubuntu, ubuntu memTest, windows, etc...). In your case it looks like its empty. Do you get an option when you start up your machine? Could you check the /boot/grub folder to make sure it exists?

---

### Post by ace_ventura on 2010-05-03
> **squeakusmaximus said:**
> hey,
aceventura, normally that file is where it lists the options at startup (ubuntu, ubuntu memTest, windows, etc...). In your case it looks like its empty. Do you get an option when you start up your machine? Could you check the /boot/grub folder to make sure it exists?
hey Maximus, i checked in file browser there is a boot/grub folder.
i have attached the screenshot of the folder.
can you tell me if i did the right thing or ur asking for different boot/grub folder?

---

### Post by squeakusmaximus on 2010-05-04
Well it turns out i'm a bit behind the times, they have moved the menu.lst:

[http://ubuntuforums.org/showthread.php?t=1340487](http://ubuntuforums.org/showthread.php?t=1340487)

check that file and make sure its pointing to the right kernel

---

### Post by bouncingmolar on 2010-05-04
> **squeakusmaximus said:**
> hey,
bouncingmolar, could you show me what config files are in your boot folder? (from the terminal: ls /boot), if nothing is happening it might be pointing at the wrong kernel


I must have loads of useless kernels here from previous linux distributions.

abi-2.6.22-14-generic
initrd.img-2.6.22-14-generic      
System.map-2.6.31-16-generic
abi-2.6.24-19-generic     
initrd.img-2.6.22-14-generic.bak  
System.map-2.6.32-21-generic
abi-2.6.31-16-generic     
initrd.img-2.6.24-19-generic      
vmcoreinfo-2.6.31-16-generic
abi-2.6.32-21-generic     
initrd.img-2.6.24-19-generic.bak  
vmcoreinfo-2.6.32-21-generic
config-2.6.22-14-generic  
initrd.img-2.6.31-16-generic      
vmlinuz-2.6.22-14-generic
config-2.6.24-19-generic  
initrd.img-2.6.32-21-generic      
vmlinuz-2.6.24-19-generic
config-2.6.31-16-generic  
memtest86+.bin                    
vmlinuz-2.6.31-16-generic
config-2.6.32-21-generic  
System.map-2.6.22-14-generic      
vmlinuz-2.6.32-21-generic                  
System.map-2.6.24-19-generic

---

### Post by bouncingmolar on 2010-05-04
:oops:

ha... I didn't follow the original instructions. I only changed the 31 to 32 but not the 16 to 21. 

thanks for the tip squeakus.#-o

I will try it out now.

---

### Post by bouncingmolar on 2010-05-04
title Kubuntu
root (hd0,0)
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=ebbb15ea-b592-413b-b9bf-dfd02bdf88b7 ro quiet splash
initrd /boot/initrd.img-2.32.21-16-generic

Now when I boot,  I get a 16 colour boot screen, with:
An error occurred when mounting /proc/bus/usb

I fixed this error by following [http://ubuntuforums.org/showpost.php?p=9232980&postcount=20](http://ubuntuforums.org/showpost.php?p=9232980&postcount=20)
I edited fstab to remove the line #usbfs /proc/bus/usb usbfs auto 0 0


I can push s to skip and kubuntu loads normally, or m to enter the maintenance shell. 

In the maintenance shell it says: 

Filesystem or mount failed. A maintenance shell will now be started. 

I quit that and it boots again, probalby not how the creaters intended.

---

### Post by meroman on 2010-05-05
Hi!

it is my first post to this forum, the first of a long contribution, I hope!

I am having exactly the same pb myself. I was running ubuntu 9.04 when the upgrade manager asked me to upgrade... and I accepted, because I was finding some problems with that version. One of these problems is that the computer hanged in the middle of nowhere, with no specific reason. And this is what happened during the upgrade... :(

Now I am getting this message when booting (mounting none on /dev failed) and the computer is not booting at all. I am using the Live CD right now to access my disk...

What should I do to solve this problem... I already checked the grub.cnf file in my computer and it points to the old kernel

[I]menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set be82c92b-6e7b-4d11-aa38-ced4e1a2731e
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=be82c92b-6e7b-4d11-aa38-ced4e1a2731e ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-14-generic
}
[/I]
And this is the only one I can find in the boot folder.

Thanks for your help!

---

### Post by bouncingmolar on 2010-05-06
> **meroman said:**
> Hi!


computer hanged in the middle of nowhere, ... during the upgrade... :(

...when booting (mounting none on /dev failed) and the computer is not booting at all. I am using the Live CD right now to access my disk...

What should I do to solve this problem... I already checked the grub.cnf file 

What is in your /boot/grub/menu.lst? You're probably looking in the right place, butmake sure you're looking at the right /boot menu and not the livecd one.

---

### Post by ace_ventura on 2010-05-09
hey guys, i followed the following link, it worked fine for me. my linux boots now without the warning mounting none on/dev failed.
[http://ubuntuforums.org/showthread.php?t=1470264](http://ubuntuforums.org/showthread.php?t=1470264)

hope this one helps others too.

thnx for the support.

---

### Post by gregorvm on 2010-05-30
i have the same problem with  kernel 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT  installed. 
I looked at the tread [http://ubuntuforums.org/showthread.php?t=1470264](http://ubuntuforums.org/showthread.php?t=1470264)
but i don't feel like manually rebuilding the kernel. Is there no easier solution?:confused:

---

