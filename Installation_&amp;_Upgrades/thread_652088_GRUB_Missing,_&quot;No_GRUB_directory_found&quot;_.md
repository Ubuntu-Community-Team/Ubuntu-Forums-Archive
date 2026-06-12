---
title: "GRUB Missing, &quot;No GRUB directory found&quot; upgrading to Kernel 2.6.22-14"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by rincewind1013 on 2007-12-28
So I'm having this problem with GRUB and updating to 2.6.22-14 in Ubuntu Gutsy

It looks like my GRUB is missing

First Error
```

 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  easytag
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3170kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 288305 files and directories currently installed.)
Removing easytag ...
Setting up linux-image-2.6.22-14-386 (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.22-14-386 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.22-14-386
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I made the change described in 
/usr/share/doc/grub/NEWS.Debian.gz

> 
  ,----[ /etc/kernel-img.conf ]
  | ...
  | postinst_hook = /sbin/update-grub
  | postrm_hook   = /sbin/update-grub
  `----

  Should be change to:
  
  ,----[ /etc/kernel-img.conf ]
  | ...
  | postinst_hook = /usr/sbin/update-grub
  | postrm_hook   = /usr/sbin/update-grub
  `----


Then I re-ran apt-get install -f

```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-386 (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.22-14-386 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.22-14-386
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I made folder /boot/grub and re-ran apt-get install -f

```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-386 (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.22-14-386
Found kernel: /vmlinuz-2.6.22-14-generic
Updating /boot/grub/menu.lst ... done


Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.22-14-386
Found kernel: /vmlinuz-2.6.22-14-generic
Updating /boot/grub/menu.lst ... done

```

So it's fine. But this is troubling, what happened to my /boot/grub folder
A lot of files are missing and I'm worried
```

/boot$ find .
.
./initrd.img-2.6.22-14-386
./System.map-2.6.22-14-386
./vmlinuz-2.6.22-14-386
./config-2.6.22-14-386
./abi-2.6.22-14-386
./System.map-2.6.22-14-generic
./vmlinuz-2.6.22-14-generic
./config-2.6.22-14-generic
./abi-2.6.22-14-generic
./initrd.img-2.6.22-14-generic
./initrd.img-2.6.22-14-386.bak
./grub
./grub/default
./grub/menu.lst
./grub/menu.lst~
./initrd.img-2.6.22-14-generic.bak

```

---

### Post by tech9 on 2007-12-28
you could try yo boot with supergrub disk...

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by meierfra on 2007-12-28
```
sudo grub-install /dev/sda
```
will reinstall all the grub file.  
 This assumes that you are booting from /dev/sda. Otherwise replace /dev/sda by the  drive you are booting from.  Look at the output of "sudo fdisk -l" if you do not know  the name of the drive you are booting from

---

### Post by rincewind1013 on 2007-12-30
It turns out my boot partition was not being mounted.

I checked what was mounted, and it didn't show my boot partition

From my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1 -- converted during upgrade to edgy
UUID=065448c7-0098-4bbe-a6c1-d207b4201a1a /boot ext3 defaults 0 2

```

I tried manually mounting /boot, but it would get error messages like

mount: /dev/sdb1 already mounted or /boot busy

Checking /dev/disk/by-uuid shows that the UUID was correct. 

Then I remembered something. A few months ago I was having trouble mounting a raid drive. I&#8217;m not an expert in Linux, but it looked like mount wasn&#8217;t taking actual device names. For example, /dev/md0 wasn&#8217;t working but /dev/mapper/Ubunut-raid1 was working. So I fixed my fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1 -- converted during upgrade to edgy
# UUID=065448c7-0098-4bbe-a6c1-d207b4201a1a /boot ext3 defaults 0 2
/dev/mapper/sdb1        /boot   ext3    defaults        0       2

```

and reran apt-get install -f, restarted, and sacrificed a goat.

It worked. I don&#8217;t know what happened. I&#8217;m not sure what I did was the correct fix. But it&#8217;s working. 

So can anyone explain why /dev/sdb1 doesn't work and /dev/mapper/sdb1 does? I'm guessing it has something to do with LVM, but I don't have that partition setup under LVM

---

