---
title: "Failure to load following kernel upgrade"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Tom_Patten on 2010-02-06
I successfully installed Ubuntu 9.10 Netbook Remix on an Asus EeePC in a dual boot mode with Windows XP.  Because the computer has no CD drive, I used a USB stick to download the files for installation.  Twice now, after upgrading to a new kernel (2.6.31-17 and 2.6.31-19 I think), when rebooting after the upgrade and selecting Ubuntu from the operating system menu, I get a message:

sh:grub>

along with a notice about limited shell commands being available.  The ls command results in:

(loop0) (hd0,3) (hd0,2) (hd0,1)

In trying some of the other commands, I get a message that a linux kernel isn't loaded.  The computer still runs Windows fine - or at least as fine as Windows ever runs.  I'd like to recover Ubuntu without doing another full installation.

---

### Post by mushwars on 2010-02-06
take a look at the line that it is trying to boot by hitting E in grub.
I am not exactly sure the structure of how it is supposed to look, so do the same on an old working kernel and then look to see if the only change is the kernel name ( that is all that should have changed ) 

if you can get it to work by editing you can 

then you need to go into your harddrive and edit your grub.conf ( I think in ubuntu it is .cnf )

That should get you back in buisness with your new kernel. If you dont know then name of the kernel or you think it might be wrong take a look at 

```
ls /boot/
```
that will show you the kernels that you have make sure that grub points to the new kernel and that it is named correctly.

---

### Post by Tom_Patten on 2010-02-06
Thanks, but I wasn't getting far enough in the boot process for that command to be recognized.

With a new day and further research, I found the post by Agostino Russo, Comment 210 for bug 477169.  I followed the directions to replace the C:\wubildr file.  That did the trick.

Mille grazie Agostino.

---

