---
title: "Does not boot anymore"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jschneider on 2009-10-13
Hi,

I just installed the latest updates and know my desktop does not boot anymore.
I tried several kernels (even an old 2.6.28) and the rescue system.

It always stopps after having tried to mount my nfs shares - which fail with "DNS resultion failed" or "Connection reset by peer"
That is the last output and then the boot process stops forever...

Any ideas how I could fix that or find out what the problem might be? Any magic boot parameters?


Oh - Ctrl-Alt-Del shuts down and reboots the computer as expected...

---

### Post by whitethorn on 2009-10-13
Do you have any proprietary graphic drivers?  I wasn't able to boot after installing them.  [http://ubuntuforums.org/showthread.php?t=1290122](http://ubuntuforums.org/showthread.php?t=1290122)

---

### Post by dino99 on 2009-10-13
boot fine here with last nvidia 185

---

### Post by jschneider on 2009-10-13
I have removed the fstab entries that failed. Then I saw that one of my partiontions got checked....
Maybe I have missed that (no visual feedback therefore within the splash?)...

I will add the entries to the fstab and try again...

---

### Post by c00kie55 on 2009-10-13
happend to me to.. but only on my 32 bit partiton ?? not on 64bit wierd

so i tryed manauly fsck from safeboot and i should not have done that !!! it broke something

i think my 32bit installation disk migth be older than my 64bit disk 

this prob came on same time as the new kernel that i tryed with nvidia drivers
but i dont think it a nvidia thing i cut startx from safemode without any probs...  there was   610 (or high number like that cant really remember) other updates that day and i think one have broke the filesystem

---

