---
title: "Kernel Panic - Not Syncing : Attempting to Kill Init!"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by sayxnug on 2006-11-28
Okay I've searched and searched for information to fix this problem. A good friend of mine has the Ubuntu book and it referred me to look up the GRUB manual saying something about a menu.lst file? (or it may have been grub.lst) I am really new to linux and seriously have no idea what I am doing besides basic computer stuff (im not an idiot).


So I boot up, it hangs at "kernel_thread_helper+0x5/0x10

I put the Ubuntu 6.06 LTS cd in (i ordered from ubuntu) and it goes a little further in the boot process im guessing but hangs up at

"Kernel Panic - not syncing: Attempted to kill init!"

Now ive read some into this and, am i to believe there may be a need to update my bios? how am I to do that when i cant even run an OS (I tried reinstalling windows and it said something like it couldnt find the system.inf file yet i installed windows on a newer computer with the same cd shortly thereafter so i know its not scratched)    or may it be a power management issue? something having to do with acpi=off (or apci i forget which one)??

here is what each of my kernels are running from the command line (two are normal, two are recovery)

root (hd0,4)
kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd /initrd.img-2.6.15-27-386
savedefault
boot

okay I am stuck, I think I got the ubuntu cd running by disabling my HD and running it just from the CDROM but ya that does no good being i have nothing to install it on.


Also, I'd like to point out that I didnt have this problem until last week, there was an update ubuntu had and after i rebooted, my computer has been doing this since.



PLEASE help me. I'll love you for life.
I have aim at: sayxnug

---

### Post by sayxnug on 2006-11-28
Or if someone can just point my in the right direction, I'd appreciate it greatly. Like i said I've looked around but it just seems everyone leaves *something* out and it leaves me in the dark.

---

### Post by RJARRRPCGP on 2006-11-28
Sounds like you have a hardware malfunction. Please make sure that the heatsink is seated properly and that the fan didn't stop spinning. Then make sure that the BIOS settings are set properly for the RAM and HDD.

---

### Post by sayxnug on 2006-11-28
Fans spinnin,
how exactly can i check the ram and HD, i know how to get into bios but what am i looking for?


You know, i'm sorta thinking it may be the HDD.

---

### Post by sayxnug on 2006-11-28
UPDATE:


okay well i updated to 6.10 after someone suggested it.

booted from CD on startup (6.06 never did that unless i disabled the HDD) and i clicked install/startup

went through the same process and ended up at

Kernel Panic - Not syncing : Attempted to kill the idle task






any takers?

---

### Post by cmichaelboyd on 2006-11-28
1) if you are able, could you print here the contents of your /boot directory?
2) also, i need to know about your hard drive configuration.  did you set up a different partition for /boot or did you set up a single partition (besides swap) and have all of your directories reside on that single partition.  

3) also, go to your top level directory and type

ls -l *vmlinu*

and print the output from that here.


I don't think you're having a hardware malfunction, though it's possilbe.  I think that your system isn't finding the kernel where it's expecting to, which could be the result of either improper linking or an incorrect kernel name in the menu.lst. 
Anyway, post those things, and we'll get to the bottom of it.

---

