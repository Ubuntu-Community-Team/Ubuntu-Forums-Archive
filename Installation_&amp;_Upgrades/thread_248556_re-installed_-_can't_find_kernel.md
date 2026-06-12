---
title: "re-installed - can't find kernel"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by Episteme on 2006-09-01
I reformatted and re-installed ubuntu last night. On boot, I'm getting an error message:

kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro quite splash

Error 15: File not found

It gives me the option to boot from other kernels, but they give me the same error message.

I'm presuming that the re install messed up my MBR on sda1, but am unsure how to clear it out.

Your suggestions?

---

### Post by Iarwain ben-adar on 2006-09-01
Hi,
well we could always try to find the file =)

First of all, is sda1 still sda1? (eg: while reinstalling you added, changed partitions)

Second of all, try to boot via live-cd, and see if there is a file called vmlinuz...


Iarwain

---

### Post by Episteme on 2006-09-01
Hi, and thanks for the reply

Yes, I started up from cd, mounted sda1, and found /boot/vmlinuz-2.6.15-26-amd64-generic right where it is supposed to be (yeah - that's linuz with a Z - I thought that was strange too - but who am i to question the coding-gods' nominclature)

Again, I'm thinking MBR - but I'm not sure how to format sda1 and flush out the mbr. I could do it easy in windows with fdisk \mbr... but not sure how in linux - or even if this is my problem... just the only thing I can think of - especially since the first install worked flawlessly.

---

### Post by Iarwain ben-adar on 2006-09-01
Only thing i can think of then is that your fstab is not correctly configured.

I think it is in /etc (don't know for shure, because i'm at school atm :D )


Iarwain

---

### Post by Episteme on 2006-09-01
I checked fstab by way of:

gedit /mnt/old/etc/fstab 

and returned with:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and see nothing wrong with that...

---

### Post by Iarwain ben-adar on 2006-09-01
Me neither :s

Sorry, can't think of anything else that can be wrong...


Iarwain

---

### Post by Episteme on 2006-09-01
Iarwain - No worries, thanks anyways... I'm sure someone else here knows what's going on and can point me in the right direction.

Peace,

Sean

edit :  I've learned that dd if=/dev/zero of=/dev/sda will zero my hard drive, including my MBR - I'm going to unmount and try that.

---

### Post by Iarwain ben-adar on 2006-09-01
And,
got anywhere further?
Keep us up to date :D


Iarwain

---

### Post by Episteme on 2006-09-01
Well... sort of... At this point I figured a new thread was in order... (I just hope that's not against forum ediquite).

[http://www.ubuntuforums.org/showthread.php?t=248622](http://www.ubuntuforums.org/showthread.php?t=248622)

---

### Post by Episteme on 2006-10-24
Just in case someone else had an ERROR:15 on boot and came across this posting = I did find the answer to my question.

It was that Grub was looking for (1,0) when it should have been looking for (0,0)

On boot, I selected the kernel, hit 'e' to edit, and changed the value.

Then, I edited /boot/grub/menu.1st accordingly.

Hope that helps others.


This is a perpetual problem on install for me - and the edit has just become part of my install routine.

---

