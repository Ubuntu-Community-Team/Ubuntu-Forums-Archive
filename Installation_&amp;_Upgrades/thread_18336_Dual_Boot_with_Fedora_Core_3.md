---
title: "Dual Boot with Fedora Core 3"
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by Peter Mount on 2005-03-06
Hello

I've loaded Fedora Core 3 on one of my hard drives. How can I load Ubuntu 4.10 onto the same hard drive so I can dual boot between them? The other hard drive has Windows and is too full for dual boot. I haven't made any files on the Fedora drive so I can wipe that if I have to in order to set up dual boot. The "Linux hard drive" is 8.4 gig in size.

I want to compare the two of them so I can decide which to keep. I was originally drawn to Red Hat/Fedora but I'm very interested in Ubuntu. I really just need something stable especially if I use Linux for my PHP development stuff.

Thanks

Peter Mount

---

### Post by alastair on 2005-03-06
No problem. Just whichever distribution ends up having written the grub bootloader, you will have to boot it and edit the /boot/grub/menu.lst file to make sure you can boot the other.

Take a note of the partitions you have (fdisk -l /dev/hdX) before. You can share swap between Fedora and Ubuntu.

---

### Post by Peter Mount on 2005-03-07
Hi

Thanks for that.

Have a good day

Peter Mount

---

### Post by valourama on 2007-02-14
Hiya, first time Ubuntu user.  old time Fedora Core 2 user (but a long time ago).

I've upgraded a bit.  I've loaded Unbuntu 6.10 on my main hda and loaded Fedora Core 6 on my second hdb.  However, I can't get FC6 to boot from Grub.  Based on some advise in other forums ( [http://www.linuxquestions.org/questions/showthread.php?t=384994](http://www.linuxquestions.org/questions/showthread.php?t=384994) ) I got FC6 listed in GRUB, but I can't get it to boot up when I choose it from the GRUB list.

I mounted my second drive under a directory called:   /fedora6


My menu.lst is currently written as such:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

title		Fedora Core 6, kernel 2.6.18-1.2798.fc6
root		(hd0,0)
kernel		/fedora6/vmlinuz-2.6.18-1.2798.fc6 root=/dev/hdb2 ro quiet splash
initrd		/fedora6/initrd-2.6.18-1.2798.fc6.img
quiet
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

this last part is the Fedora Core 6 listing I made.  Everytime I choose it, it says file not found. Can anyone spot what I'm doing wrong?

V

---

### Post by confused57 on 2007-02-15
Try root (hd1,1)
or if you have a separate boot partition
root (hd1,0)

---

### Post by valourama on 2007-02-15
title Fedora Core 6, kernel 2.6.18-1.2798.fc6
root (hd1,1)
kernel /fedora6/vmlinuz-2.6.18-1.2798.fc6 root=/dev/hdb2 ro quiet splash
initrd /fedora6/initrd-2.6.18-1.2798.fc6.img
quiet
savedefault
boot

based on the above advise I changed the root (hd1,1)

it gave me a new error:

ERROR 17:  cannot mount selected partition

I went on to change the:       root=/dev/hdb2

to the following variations:                    hdb0, hdb1, and  hdb3

no success... same error...

I'm glad I have some movement, but I don't know where to go after this... help!

---

### Post by confused57 on 2007-02-15
You might want to boot into Ubuntu, open a terminal & post the output of:
```
sudo fdisk -l
```
The -l is a small "L"
The output of this command may give some idea of how to setup your entry to boot Fedora.

You can also boot other Linux OS from grub using  chainloading.   You would do this by booting up the live cd and installing the Fedora grub to it's root partition:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Whatever the command "find /boot/grub/stage1"(from the above link) shows as the Fedora root partition, then select to install grub on the root partition, e.g.
```
root (hdx,x)
setup (hdx,x)
quit
```

Then add an entry to your Ubuntu grub to boot Fedora:
title   Fedora
rootnoverify (hdx,x)
chainloader +1

Herman's site explains this & other ways to boot multiple Linux OS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by valourama on 2007-02-21
thanks confused57!

I will try this weekend!

V

---

### Post by louieb on 2007-02-21
> **valourama said:**
> title Fedora Core 6, kernel 2.6.18-1.2798.fc6
root (hd1,1)
kernel /fedora6/vmlinuz-2.6.18-1.2798.fc6 root=/dev/hdb2 ro quiet splash
initrd /fedora6/initrd-2.6.18-1.2798.fc6.img
quiet
savedefault
boot

Fedora 5 was my first linux disrto all of about 8 mo ago. 
And in Fedora5 the kernel and initrd are in /boot not /fedora#
You may have created a mount point in Ubuntu of /fedora6 but grub doesn't know what that is. My guess is that if you browse your fedora install you will find the kernel in /boot. And the GRUB menu should look for it there.

---

