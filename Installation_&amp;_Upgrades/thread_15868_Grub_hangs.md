---
title: "Grub hangs"
date: 2005-02-17
forum: Installation &amp; Upgrades
---

### Post by lanik on 2005-02-17
Hi!
    I've installed ubuntu on my laptop, and when I restarted the computer it keeps loading GRUB and stays here forever. I've tried installing Lilo, but the problem is the same. The laptop is a Fujistu-Siemens, P IV . Any ideas?

Thanks

---

### Post by rmjokers on 2005-02-17
Do you have any information on how you set up the partitions and where you installed GRUB (MBR or beginning of root partition)?  Also, how does the GRUB message still appear after you installed LILO?  If so, how did you install LILO?

---

### Post by lanik on 2005-02-17
I installed Grub on MBR.  I reinstalled ubuntu and selected Lilo. This time doesn't show any Grub message. Lilo also hangs.  The only message is "please wait", and it can last for an hour. 
  I used windows free space for the new partitions, one for swap. I already had Mandrake installed. I deleted Mandrake partitions and installed ubuntu on free space

---

### Post by wallijonn on 2005-02-18
You may want to turn off as much in the BIOS as possible, like USB, Power Saver, etc. and see if it'll allow you to boot. It may be a pcihp type problem.

---

### Post by Ronbo on 2005-02-19
I had the same problem with my box, motherboard is an Asus K8N.  What I had to do is flash the bios to the most current version (from version 1002 to version 1004),  now works without a problem.  I also got a reply on the user mailing list about someone else having the same problem, his fix was to set the bios to boot the hard drive first, after the initial install from cd and before the reboot,  instead of booting the cd first.  I don't know if this will solve your problem but hopefully it helps.

---

