---
title: "Nvidia GeForceGo 420 &amp; new kernel 2.6.33-999.201002061003_i386"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by DieUbunt on 2010-02-07
Hi 

I have a problem with recompiling of new kernel.
When I recompile nvidia kernel give me that :

ERROR: Unable to determine the version of the kernel sources located in
       '/lib/modules/2.6.33-999-generic/build'.  Please make sure you have
       installed the kernel source files for your kernel and that they are
       properly configured; on Red Hat Linux systems, for example, be sure you
       have the 'kernel-source' or 'kernel-devel' RPM installed.  If you know
       the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line

How can I resolve it?
Thanks in advance

---

### Post by bathory on 2010-02-08
Hi,

You have to patch your nvidia driver. You can get the patch from [here]("http://www.nvnews.net/vbulletin/showpost.php?p=2164440&postcount=20")

Regards

---

### Post by DieUbunt on 2010-02-16
Hi,
 
thanks a lot
My driver nvidia linux is for
 
Latest Legacy GPU version (96.43.xx series): 96.43.14
 
I have seen that there is a new one
 
Latest Legacy GPU version (96.43.xx series): [96.43.16]("http://ubuntuforums.org/object/linux_display_ia32_96.43.16.html")
 
I'll try it but where could I find out that one patched
 
Thanks in advance
 
 
> **bathory said:**
> Hi,
 
You have to patch your nvidia driver. You can get the patch from [here]("http://www.nvnews.net/vbulletin/showpost.php?p=2164440&postcount=20")
 
Regards

---

### Post by bathory on 2010-02-17
Unfortunately the patches are for the 190.x and 195.x drivers. 
You can take a look at the patch and try to modify yourself the respective files in nvidia 96.43.16 sources. Don't forget to make backups for the files you modify.
Or you should stick with an older kernel
If you insist to use  a 2.6.33x kernel use the nv module that comes with it

---

### Post by falconindy on 2010-02-26
> **bathory said:**
> Unfortunately the patches are for the 190.x and 195.x drivers. 
You can take a look at the patch and try to modify yourself the respective files in nvidia 96.43.16 sources. Don't forget to make backups for the files you modify.
Or you should stick with an older kernel
If you insist to use  a 2.6.33x kernel use the nv module that comes with it
The nv kernel module is old and bad. I suggest trying out nouveau instead for older cards. There's plenty of info about nouveau in the Lucid dev forum.

---

