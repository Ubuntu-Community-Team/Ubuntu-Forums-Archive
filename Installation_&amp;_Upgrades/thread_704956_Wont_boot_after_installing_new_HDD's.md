---
title: "Wont boot after installing new HDD's"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by abetterlie on 2008-02-22
Hey all, I had an ubuntu 7 box running fine for ages as our fileserver, with fakeraid and samba...
We needed more space, so I bought some controllers, and 4 more hdd's. after putting the controllers and the drives in, ubuntu wont boot. In a panic, I pulled the drives and the controllers out, and it still wont boot. 
I get kicked into busybox with this being the prompt I see:
[IMG]http://img90.imageshack.us/img90/3751/screenshotan8.jpg[/IMG]

I'm not too worried, because if I boot to a livecd i can still mount the array, and the boot drive. 

I have tried a few things:

checking grub.lst to make sure the uuid is correct, which it is. 
checking fstab
menu.lst

there were some weirdnesses (i think)
my init is a broken symbolic link to boot/initrd.img-2.6.19-7-generic, which when i deleted, it fixed, than still no luck booting, also strange because that file does not exist. the files in /boot are vmlinuz, config, abi, and System.map all ending in the same version number.

---

### Post by abetterlie on 2008-02-22
menu.lst

title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=be715b50-69e2-48ac-8de2-a2fb4862c46c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=be715b50-69e2-48ac-8de2-a2fb4862c46c ro single
initrd          /boot/initrd.img-2.6.22-14-server

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~/roo/boot/grub$            

ubuntu@ubuntu:~/roo$ cat etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=be715b50-69e2-48ac-8de2-a2fb4862c46c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7457f78e-3d6a-4343-a485-efa3b8b1c949 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/md0  /var/swaproot/  ext3  user,suid,dev,exec  0  0
/dev/sda1 /mnt/USB auto noauto,owner,kuzu 0 0



> **abetterlie said:**
> Hey all, I had an ubuntu 7 box running fine for ages as our fileserver, with fakeraid and samba...
We needed more space, so I bought some controllers, and 4 more hdd's. after putting the controllers and the drives in, ubuntu wont boot. In a panic, I pulled the drives and the controllers out, and it still wont boot. 
I get kicked into busybox with this being the prompt I see:
[IMG]http://img90.imageshack.us/img90/3751/screenshotan8.jpg[/IMG]

I'm not too worried, because if I boot to a livecd i can still mount the array, and the boot drive. 

I have tried a few things:

checking grub.lst to make sure the uuid is correct, which it is. 
checking fstab
menu.lst

there were some weirdnesses (i think)
my init is a broken symbolic link to boot/initrd.img-2.6.19-7-generic, which when i deleted, it fixed, than still no luck booting, also strange because that file does not exist. the files in /boot are vmlinuz, config, abi, and System.map all ending in the same version number.

---

