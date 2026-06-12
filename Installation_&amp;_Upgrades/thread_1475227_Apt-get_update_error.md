---
title: "Apt-get update error"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Ernie S. on 2010-05-06
```
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up ndiswrapper-common (1.54-2ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-2.6.32-22-generic
 grub-pc
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone know what this means? I just started getting it when I run Apt-get update. I know it has something to do with my sources, but I don't know how to fix it. Thanks in advance! ;)

---

### Post by mikewhatever on 2010-05-06
Try *sudo dpkg --configure -a*.

---

### Post by Ernie S. on 2010-05-06
Thanks mikewhatever, I ran: sudo dpkg --configure -a and this was the resulting output: 
```
Setting up grub-pc (1.98-1ubuntu6) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/20_memtest86+: 37: EOF: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-22-generic (2.6.32-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/20_memtest86+: 37: EOF: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-pc
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic

```

What was suppose to happen? I don't usually like asking the same stupid question and looking like the noob who won't do any research on his own, but I'm in way over my head here and appreciate the help!

---

### Post by mikewhatever on 2010-05-07
Odd, wish I'd know what's wrong.:(

Edit: Stumbled upon this [http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html).
Not sure if it's helpful at all, but for the lack of better suggestions, you could try the following:
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.32-22-generic
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.32-23-generic

---

### Post by dino99 on 2010-05-07
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo update-initramfs -u
sudo grub-mkconfig && update-grub
sudo shutdown -F -r now

if still errors, then into synaptic: remove/purge (right click) all the grub packages then reinstall grub-pc and grub-common

note: the problem is about kernel 22, so if no other solutions work, uninstall it (purging), you will reinstall it on next reboot

---

### Post by bubaliba on 2010-05-07
> **dino99 said:**
> note: the problem is about kernel 22, so if no other solutions work, uninstall it (purging), you will reinstall it on next reboot

Having a similar problem I've purged this kernel version, but I don't know how to re-update and reinstall it.
Running sudo apt-get update && sudo apt-get upgrade does not return any kernel updates.
What I mean, is should I find it via KPackageKit (Synaptic) or should I wait for another notification?

---

### Post by Ernie S. on 2010-05-10
@ bubaliba - I found this [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/). Should help with the whole kernel removal business.

@ everyone else- I ended up removing kernel 22 since I'm running 21 anyway. And the grub error turned out to be a section 
of /etc/grub.d/20_memtest86+ I had commented out incorrectly. You can see it right there where it says 
```
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/20_memtest86+: 37: EOF: not found,
```
I missed to putting a # in front of EOF when commenting out the memtest86 menu entries.
Thank you for the help. I never would have figured this out without you guys :guitar:

---

