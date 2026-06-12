---
title: "Several Kernels Dont Work"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by ndstate on 2008-06-09
Hello,

I have searched and searched but I cannot find a solution that works for me.

I cannot get a kernel beyond 2.6.24-14 to work for me.  2.6.24-16, 2.6.24-18, 2.6.24-17, and 2.6.24-19 all will not work.

What I mean is that I cannot even boot to the login screen with anything but 2.6.24-14.  My computer will just sit there with a black screen not doing anything... no error messages or anything.

I have tried some of the suggestions such as removing old kernels (from the package manager), but that doesnt work.

How would I go about trying to solve this issue?  What sort of information should I post?  Also, to note I am running 8.04 64 bit.

Thanks!

---

### Post by PmDematagoda on 2008-06-09
When you boot kernel 2.6.24-18 in Recovery Mode or without the splash and quiet parameters do you see any errors?

---

### Post by mythbuntu_user on 2008-06-09
I had a somewhat similar situation I thought I'd offer up my solution.

I had ubuntu 8.04 beta working but as soon as I upgraded to release, it would get to a certain point and hang.  When I installed, I did not re-install grub, I just added my own entry.  However, ubuntu (or latest kernel) switch the nameing scheme for my drives.  

ie. my ubuntu used to be on sda6, but when I upgraded from 2.6.24-12 to 2.6.24-15, the kernel boot strap code assumed that same partition was sdc6.  So grub was telling the kernel root was on sda6, but since the naming was different, once bootstrapped, image was looking for root partition on a completely different hard drive.  I changed my entry for root partition in grub to sdc6 and everything was fine.

Good luck on solving your issue.

---

### Post by Pumalite on 2008-06-09
Check UUID'S:
blkid
against:
/etc/fstab
/boot/grub/menu.lst
For each kernel.

---

