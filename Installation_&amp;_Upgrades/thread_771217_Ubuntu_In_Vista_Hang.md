---
title: "Ubuntu In Vista Hang"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by rustensa on 2008-04-27
Hello, 

New to the forum obviously. Hate to be the millionth n00b to ask but, I'm trying to install 8.04 in windows and haven't had much luck. I upgraded my other PC running XP and Ubuntu just fine but trying to install with the WUBI on my kids PC just keeps hanging. Thus far I have tried....

- Installing from the alternate CD
- Installing from the normal CD
- Installing using the WUBI via the web
- I verified the checksums and they have turned out alright
- I tried the pci=nomsi workaround

The hangs I've received are, it will read through the entire install and then inform me that it can't read the CD, but only at the very end. The other hang it that it will simply stop when it's almost on the third segment of the progress bar. If I'm missing an obvious solution or haven't read enough...point me in the right direction please. Thanks.


rustensa

---

### Post by rustensa on 2008-04-27
Anyone? Am I asking in the wrong place?

---

### Post by punkybouy on 2008-04-27
What do you mean by, "trying to install 8.04 in windows"?  U mean on a second partition? or are you running some virtualization software?  Thanks.

---

### Post by lemming465 on 2008-04-27
For the benefit of the WUBI newbies, it installs Ubuntu to a disk image file on an NTFS partition, and then alters the windows boot menu to loopback mount it as the root partition.  So you get a complete Ubuntu install in a handful of files under C:\Ubuntu.

For rutensa, did you copy the wubi installer to the local hard drive and then run it from there?  There is a note that running it off the CD image directly doesn't work on Vista.  I got by that with an extra reboot, by luck, I guess.

---

### Post by rustensa on 2008-04-27
> **punkybouy said:**
> What do you mean by, "trying to install 8.04 in windows"?  U mean on a second partition? or are you running some virtualization software?  Thanks.

Thanks for replying. Trying to install on a second partition using WUBI. I just accepted the default recommendation of 15 GB. To continue, no not using virtualization software like VMWARE or VirtualBox. Thanks...


rustensa

---

### Post by rustensa on 2008-04-27
> **lemming465 said:**
> For the benefit of the WUBI newbies, it installs Ubuntu to a disk image file on an NTFS partition, and then alters the windows boot menu to loopback mount it as the root partition.  So you get a complete Ubuntu install in a handful of files under C:\Ubuntu.

For rutensa, did you copy the wubi installer to the local hard drive and then run it from there?  There is a note that running it off the CD image directly doesn't work on Vista.  I got by that with an extra reboot, by luck, I guess.

Thank you for your reply and very intelligent question, I did indeed install WUBI to the HDD. Not actually because on any specific knowledge but experimenting to get this installed. When installed on the HDD I was able to complete installation but, on reboot while trying to complete it hung up as stated before. 

I do have a spare HDD lying around but it's really for my son to play around with on his PC and I really wanted WUBI to do it's magic as I was really impressed with the idea.

Any help to make it work would be appreciated. I was wondering if perhaps there was a way to output a log file to see what's holding it up.

---

### Post by lemming465 on 2008-04-28
You mentioned trying to install from the *normal* CD.  Did you get a live desktop that worked from it when you booted the CD instead of the hard disk?  If you haven't tried that yet, try that and tell us what happens.  If you have, I'm currently stumped.

Also, are both of the PC's using 32-bit CPU's ("i386"), or is one of them new enough that it's 64-bit ("x86_64")?  64 bit code wouldn't run on a 32 bit CPU, though the converse is OK.

How to get output from a log file depends on how far it got in the boot process.  You need at least a single-user root shell prompt before you are going to be able to do anything.  At that point the easiest thing is to mount a FAT32 formatted usb flash drive (mkdir /media/xxx; mount /dev/sdc1 /dev/xxx) and copy stuff to it.
If root is still read-only (output of "mount"), the only available logs are the
kernel messages; try "dmesg > /media/xxx/failed_boot.txt"  Otherwise you can start copying stuff out of /var/log, particularly "cp /var/log/messages /media/xxx".

---

