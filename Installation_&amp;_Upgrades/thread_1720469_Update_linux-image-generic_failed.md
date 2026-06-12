---
title: "Update linux-image-generic failed"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by stonebyte on 2011-04-03
I usually update the system every week thru the normal update process. Nothing problematic occurred up to now.
Two weeks ago I got an error while applying the update. I found out, that the reason is an error during the post-installation process for kernel image 2.6.32.30. The grub update seems not to work.

I tried updating using the shell.
Up to now the 'old' 2.6.32.29 kernel seems to work but there remains a bad feeling. 
Here is the output. Any help is welcome.


> root@gocastle:/home/peter# apt-get install linux-generic                                                                                                                     
Reading package lists... Done                                                                                                                                                            
Building dependency tree                                                                                                                                                                 
Reading state information... Done                                                                                                                                                        
linux-generic is already the newest version.                                                                                                                                             
The following packages were automatically installed and are no longer required:                                                                                                          
  linux-headers-2.6.32-29 linux-headers-2.6.32-29-generic libvpx0                                                                                                                        
Use 'apt-get autoremove' to remove them.                                                                                                                                                 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                                                                                                                           
3 not fully installed or removed.                                                                                                                                                        
After this operation, 0B of additional disk space will be used.                                                                                                                          
Setting up linux-image-2.6.32-30-generic (2.6.32-30.59) ...                                                                                                                              
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-30-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdb1
Found Windows 7 (loader) on /dev/sdb3
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sdb6
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-30-generic; however:
  Package linux-image-2.6.32-30-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.30.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                           Errors were encountered while processing:
 linux-image-2.6.32-30-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@gocastle:/home/peter# 


---

### Post by Dutch70 on 2011-04-03
Try running this in a terminal...
```
sudo dpkg --configure -a
```

and then...
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jcolyn on 2011-04-03
See my post (post #6) here [http://ubuntuforums.org/showthread.php?t=1719681](http://ubuntuforums.org/showthread.php?t=1719681) for kernel upgrades..

Be sure to follow instructions to the letter..

---

### Post by stonebyte on 2011-04-03
> **Dutch70 said:**
> Try running this in a terminal...
```
sudo dpkg --configure -a
```

and then...
```
sudo apt-get update && sudo apt-get upgrade
```
Hi,

Thanks for your advice.
But.
> dpkg --configure -a finds the same 3 pending packages and gives the same error message during post-install updating grub.
Same is true with > apt-get upgrade. And > apt-get update I do every time before installing anything.

---

### Post by stonebyte on 2011-04-03
> **jcolyn said:**
> See my post (post #6) here [http://ubuntuforums.org/showthread.php?t=1719681](http://ubuntuforums.org/showthread.php?t=1719681) for kernel upgrades..

Be sure to follow instructions to the letter..
Hi Colyn,

Thanks, but I don't want to use a newer kernel version. Just this one 2.6.32.30, which is tested with ubuntu 10.04. I think it is only a slight bug with the grub post-install script. Perhaps there is a way to configure grub manually. But then my repository wouldn't be uptodate.

---

### Post by stonebyte on 2011-04-22
At last it seemed, I solved this.
The post install script update-grub seems to read all members of the path /etc/grub.d . The README file is placed there too. This cannot be interpreted. I deleted this file. Then the update worked fine for me.

Thanks to all

---

### Post by Lhooqtoo on 2011-09-07
> **stonebyte said:**
> /etc/grub.d/README file is placed there too. This cannot be interpreted. I deleted this file. Then the update worked fine for me.


Bingo.  Thanks everyone.

---

