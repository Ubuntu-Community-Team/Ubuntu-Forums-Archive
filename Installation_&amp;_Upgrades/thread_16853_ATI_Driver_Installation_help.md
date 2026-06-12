---
title: "ATI Driver Installation help"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by starfarer on 2005-02-24
hi, i've been trying to install since very first day of installation but to no success. I've followed every guide written and now i'm getting more and more confused. So lets start line by line.

1) What do i need to start? rpm from Ati site,Kernel header.what about gcc? which version? how to get? Any other? ati control? 

2) Find any fglrx driver and remove. Find fglrx.ko and remove. what about nvidia.ko? I'm using Nforce2 Motherboard.

3)Convert rpm file to deb using alien <rpm name>

4) Install dpkg --force-overwrite -i <name of file created on step 3.deb> (what does all this switches do though)

5) Build Kernel.
   5.a) rmmod fglrx - gives error which is normal..right?
   5.b) cd to /lib/modules/fglrx/build_mod and sh make.sh
   5.c) cd to /lib/modules/fglrx and sh make_sh (this is where i'm getting some kind of error message. I'll write full text later.)
   5.d) copy fglrx.ko to directory made ( /lib/modules/<kernel version>/misc
   5.e) depmod -a (i don't know what this does)
   5.f) fglrxconfig ( once i was successful till this step and running this and saving to  fglrxconfig won't restart X. So I reinstalled Ubuntu).
   5.g) modprobe fglrx 

6) restart gnome and check with fglrxinfo. 

Now guys go slow as i'm new to linux. I want to give Ubuntu one final try as till now i'm really impressed.I've done some installation,ISO file creation,CD writing,File copying,reading NTFS+FAT partition etc. My kernel is 2.6.8.1-5-386 . I've even tried K7 version but that feels very slow although i'm using AMD XP cpu.

---

### Post by starfarer on 2005-02-24
for Step 5.c ) 

Now to edit the fglrx make.sh file so that it knows where to look...
$sudo nano /lib/modules/fglrx/build_mod/make.sh

Now somewhere a couple pages down it will say...
# specify defaults for include file locations
And there will be different locations commented out with "#", just find the kernel version that's yours and uncomment it or add your own.

I've added line linuxincludes=/usr/src/linux-headers-<kernel version>/include but still getting error.

---

### Post by starfarer on 2005-02-24
ok heres the error message:
-Creating symlink
-recreating module dependency list
-trying a sample load of kernel module 
[fglrx:firegl_stub_register]*ERROR* FireGL kernel module has to be loaded prior to any other DRM kernel module!
FATAL: Error inserting Fglrx(/lib/modules/2.6.8.1-5-386/kernel/drivers/char/drm/fglrx.ko)
Operation not permitted
Failed.

---

