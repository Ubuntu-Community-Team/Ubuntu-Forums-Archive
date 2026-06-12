---
title: "initramfs /dev/disk/by-uuid does not exist"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pilles7104 on 2009-04-09
I have an EEE PC 1000HE that has been running Ubuntu 9.04 with ext4 for a few weeks. This morning, I ran apt-get upgrade and it installed all the new updates. I rebooted and its dropping me to initramfs.

Alert! /dev/disk/by-uuid/xxxxxxxx does not exist. Dropping to a shell!

I have tried adding rootdelay=90 but that didn't change anything. If I cd /dev I do not see any disk directory. I have also tried editing grub to boot from /dev/sda1 instead of uuid=xxxx but I get the same thing.

Any suggestions?

---

### Post by pilles7104 on 2009-04-09
I had a separate /home so I went ahead and installed the new beta release.

---

### Post by patriarch.geek on 2009-04-09
I have exactly the same problem. I have an X-Force XFX 8500 MB with an NVidia 8500 n-force chipset. I'm booting off the IDE controller. When I ran the updates today (9 April 2009) I got the same message from grub, as well as a couple of  

[Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI_PSS objects in a way that Linux understands.

messages.

I can boot to a command prompt via the 2.6.28.9 kernel I had previously installed, by setting the root device to hda1 in the grub boot editor. 

This is very ugly, it looks like a *B A D* kernel build. Anybody got a kernel update that might fix it?

---

### Post by fritz276 on 2009-04-10
Same problem, running Jaunty since some weeks, and after the last update, I get the "/dev/disk/by-uuid/xxxxxxxx does not exist. Dropping to a shell!" problem, too. Only happens with -generic kernel; with -server kernel, this problem does not happen (on the other hand, -server kernel does not really work good for me, e.g. due to some modules like forcedeth are missing).

---

### Post by nebajoth on 2009-04-11
exact same problem, on the same timeline.

---

### Post by patriarch.geek on 2009-04-11
Fixed!

I was able to get in using a previous kernel (see above).
Then I went to /var/cache/apt/archive and executed dpkg --install ./linux-image-2.6.28-11-generic_2.6.28-11.40_i386.deb

I think this may have been caused by a full root file system at the time of install of the new kernel image. Part of the image install is building initrd.img

Rather than throwing an error and aborting the install when it ran out of room, it failed silently and built a truncated initrd.img, rendering the system unable to boot.

The eee user above might be able to boot from a usb key to get to the same place

---

### Post by jejones3141 on 2009-04-12
Thank you, patriarch.geek; I had exactly the same problem, and your solution worked for me (modulo asking for the 64-bit version rather than i386). Something about 2.6.28-11.41 must be the cause of the problem, and dropping back to 2.6.28-11.40 fixes it.

---

### Post by koalaj on 2009-04-12
.raises hand  im a greenie here .  i have same error coming up as this , and yes i updated just yesterday 11th april. i would like to try this solution . only i dont know how to drop back to a previous version (or was it kernel ) ? could i get a little help . it seems like this would help me with this boot error .
there is **no output** after i enter fdisk -l just says could no be found
top line of error is boot from (hdo,4) ext 3 ##########

any help guys ?

---

### Post by patriarch.geek on 2009-04-13
koalaj

It seems you are able to get into the system. To roll back the kernel image version:

1) log into a terminal session:

Press Ctrl-Alt-F2 and log in to the terminal

2) Make sure you have enough space in the /boot directory
[B]
df-k /boot[/B]

This will show you the size, K used, and K available. You should have a number larger than 500,000 in the available column.

3) determine the previous version of the linux-image package.

**cd /var/cache/apt/archive**
[B]
ls linux-image*[/B]

This will give you a list of the linux image packages that are cached by the package manager. Whenever you install a package, it is stored here after it is downloaded. I will give you a list that looks like this:

linux-image-2.6.28-11-generic_2.6.28-11.40_i386.deb
linux-image-2.6.28-11-generic_2.6.28-11.41_i386.deb

Note that the Ubuntu package version is near the end, just before the architecture string (i386). In this case the Ubuntu package version numbers are 40 and 41. 41 is the one that broke your system, so 40 is the one you need to re-install

4) re-install the older package

**sudo dpkg --install ./linux-image-2.6.28-11-generic_2.6.28-11.40_i386.deb**

(note that the webpage may have inserted a line brake there. It's all one line.)

5) reboot and see if it works

**sudo shutdown -r now**

Hope this helps

---

### Post by cowgoeswoof on 2009-04-19
I too have this exact problem after updating to 9.04. Think the updater went wrong or something... anyhoo the above reply seems like it helped others but I cant open a terminal or anything.
Im just stuck on this annoying busybox error screen.
Ah! Any help is much appreciated! :popcorn:

---

### Post by patriarch.geek on 2009-04-20
sorry, but my fix works only if you can get in to the system. If you upgraded, you MAY be able to get in. During the boot up sequence, by default grub on Ubuntu shows a short message for about 3 seconds, just after the bios loads. If you hit ESC during those 3 seconds, it will bring up the boot menu. That should give you the choice of any previous version of the Linux kernel you've installed. Any of the choices besides the top one should get you in, if you have a previously installed kernel.

Otherwise, it's re-install time.

---

### Post by markgilmore1322 on 2009-04-20
Adding rootdelay=60 as a kernel option worked for me.  See this bug for more detail:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349307)

---

