---
title: "/var/run/grub/menu.;st"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by owen_cook on 2008-10-28
8.04

Just did an new update today which included a new kernel (sorry, I didn't note the version)

It took ages, top showed sed was running 99%

Eventually it all seemed to die with this message

Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-server
Found kernel: /boot/vmlinuz-2.6.24-19-rt
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
sed: couldn't write 35 items to stdout: No space left on device
User postinst hook script [/sbin/update-grub] exited with value 4
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 linux-image-2.6.24-21-generic

Looking at /var/run/grub/menu.lst I got this

owen@owens:/var/run$ ls -la grub/menu.lst
-rw-r--r-- 1 root root 529465344 2008-10-29 11:24 grub/menu.lst

Mind boggling!

So I am not sure what all that is about. Guess I should have kept the file, it may have be in an infinite loop

I couldn't kill sed, it just kept on rolling along.

FWIW

---

### Post by oldos2er on 2008-10-29
"No space left on device" means your partition is full.

---

### Post by caljohnsmith on 2008-10-29
I believe that error you got is from the "update-grub" command that is run after you install a new kernel so that your menu.lst gets updated. But according to that command you have at least 7 kernels installed:
```
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-server
Found kernel: /boot/vmlinuz-2.6.24-19-rt
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
```
I would highly recommend uninstalling some of the older kernels, because really only need maybe two kernels: one that you know works, and a newer one that you installed and aren't sure about yet. And as oldos2er said, you might have problems with disk space. You can uninstall the kernels in Synaptic Package Manager, just make sure the following packages get uninstalled for each kernel (just as an example):
```
linux-headers-2.6.24-16-generic
linux-image-2.6.24.16-generic
linux-restricted-modules-2.6.24-16-generic
linux-ubuntu-modules-2.6.24-16-generic
```
Probably just uninstalling the linux-image will cause the other to be uninstalled too, but I don't remember. Let us know how it goes. :)

---

### Post by owen_cook on 2008-10-30
Thank you for you comments. I will have to clean up all my images.

the 8.04 /boot/grub/menu.lst showed 

-rw-r--r-- 1 root root 774379478 2008-10-17 08:29 menu.lst
-rw-r--r-- 1 root root 774379478 2008-10-30 16:39 menu.lst~

Mmmmm

Then I remembered that I did grub install from another distro on another partition.

Removed the 1.5 gbytes of menu.lst and did a

dpkg --configure -a

------------------------------------------------
Testing for an existing GRUB menu.lst file ...

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-server
Found kernel: /boot/vmlinuz-2.6.24-19-rt
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
------------------------------------------------

Hooray, thank you

I am simply delaying any clean up till 8.10 comes out and will probably abandon this installation


Many thanks for your interest


Owen

---

### Post by caljohnsmith on 2008-10-30
Glad you got the problem sorted out; cheers and have fun Ubuntu-ing. :)

---

