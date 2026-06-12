---
title: "hardy upgrade: usplash not displaying"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by tanguyr on 2008-04-27
Hello,

After upgrading from Gutsy to Hardy, i am experiencing the following problem with usplash: when the boot process starts, the usplash screen with the blue bar traveling back and forth; left to right and back (what i call "knight rider" mode :) is displayed, but when i expect it to go into "progress bar" mode (where the blue section just grows from left to right) it drops me back into text mode boot (displays message "* Reading scripts needed to boot... [ok]" and so forth).

Any ideas?

Regs,
/t

PS: this is on an Asus W2 laptop with an ATI X1700 card, using fglrx drivers.

---

### Post by ajgreeny on 2008-04-27
I don't get the bar moving back and forth on my installed system; I thought that only happened on a live CD boot up.  Mine goes straight to the bar growing from left to right.  OK, I am using Ubuntu, not Kubuntu, and I don't use the fglrx drivers for my ati card, but I don't think that would make any difference.

---

### Post by tanguyr on 2008-04-27
> **ajgreeny said:**
> I don't get the bar moving back and forth on my installed system; I thought that only happened on a live CD boot up.  Mine goes straight to the bar growing from left to right.  OK, I am using Ubuntu, not Kubuntu, and I don't use the fglrx drivers for my ati card, but I don't think that would make any difference.

I'm trying to remember whether it did do "knight rider" mode in Gutsy - despite having seen it untold times i can't be sure. In any case, i'd like to return to the progress bar as opposed to the text mode boot. 

Regs,
/t

---

### Post by erginemr on 2008-04-27
Same story (Knight Rider, then text). I'd be glad if any fellow Ubuntero came up with a solution...

---

### Post by erginemr on 2008-04-27
Well, I have some good news! :D

It seems the upgrade process has somehow changed the UUID code for the swap partition and having a wrong code causes usplash to crash.

Following this thread:
[http://ubuntuforums.org/showthread.php?t=746132](http://ubuntuforums.org/showthread.php?t=746132)

1. I could fix usplash screen by first issuing:
```
sudo blkid
```
from a terminal, copying the UUID for "swap".

2. And then, editing the file:
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
and paste the correct UUID for swap, but without the quotes.

3. Finally, to make sure that the changes are reflected in usplash:
```
sudo update-initramfs -u
```
This will take about a minute, but it is crucial that this process is completed. Otherwise, you will have a broken initramfs file and won't be able to boot.

The credit goes to **analystscouch** and **MALEADt** from the a/m thread:
[http://ubuntuforums.org/showpost.php?p=4714344&postcount=16](http://ubuntuforums.org/showpost.php?p=4714344&postcount=16)
[http://ubuntuforums.org/showpost.php?p=4714530&postcount=20](http://ubuntuforums.org/showpost.php?p=4714530&postcount=20)

---

### Post by tanguyr on 2008-04-27
> **erginemr said:**
> Well, I have some good news! :D

hello erginemr, thanks for the tip!

---

### Post by jibro on 2008-04-29
Hi - I had the same problem on Xubuntu, however the cause of the issue was a little different to the one described above, but the fix followed the same routine.

When I ran blkid there was no uuid for the swap partition. After reading through the development thread pointed to earlier in the discussion I checked the /etc/fstab file, this had a uuid entry in place for swap (I forgot to check if it was being mounted) I then updated /etc/fstab to point to  /dev/sda1 instead of the uuid, I then changed the resume file (/etc/initramfs-tools/conf.d/resume) to also point to /dev/sda1 and ran update-initramfs -u as described. This resolved the problem.

Swap must have had a uuid at some point for the entry to have been in the fstab file.

This system went through a double online upgrade first to 7.10 then straight to 8.04.


Thanks for the fix info.

---

