---
title: "Install hangs after splash screen"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by oxo2oxo on 2010-05-17
Clean install on dell d400 laptop, worked fine with 9.10 but 10.04 gets past the stick man then after several minutes with the red/ white buttons a quick flash of colour on the screen and then nothing, just a dead PC. 

Have tries alternative F6 and also i915.modeset=1  and 0 but no change. Pre release 10.04 worked fine just a problem with the official release ! help please !

---

### Post by oxo2oxo on 2010-05-18
Further update, I re installed 9.10 and then upgraded which went through without errors however on boot get the first splash screen and then the system dies completely

---

### Post by Catharsis on 2010-05-18
Do you have any other kernels in grub you can boot into? Hold down Shift while booting to get to grub.

P.S.:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by efflandt on 2010-05-18
What video does it have?  Have you tried using **nomodeset** kernel parameter (and possibly removing **quiet spash** to see more boot info)?

I had to use nomodeset or radeon.modeset=0 with a Dell Inspiron 6400, but that has Radeon Mobility X1300 video, and various Dells have various video chips.  The nomodeset would use user space modules similar to 9.10 for any video, instead of the new kernel mode setting (KMS) video drivers.  Without disabling KMS it sometimes booted 10.04 to a screen with a pattern of colored has marks at the top, and then unresponsive.

---

### Post by garvinrick4 on 2010-05-18
Can you download as .iso file of 10.04 to your desktop. (I will give you the link)
Burn a CD at the slowest speed possible. Install from the CD into the partition that
you use Ubuntu. 
 In your upgrade for some reason you are not mounting your / . There are 3 things that
happen at get go and that is a package called "ureadahead" a package called "mountall"
and a package called "plymouth" your splash screen. Are they the latest packages? If not
a lot of users had trouble booting during testing so lets check it out.
 Hopefully you have a machine to burn a disk with. If not we can try a Live CD and get into your / using the chroot command and updating your OS. But one step at a time.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Catharsis on 2010-05-18
The OP has an intel 855GM card. There have been a huge number of problems with the drivers for this card and Lucid. The symptoms he described are textbook X Server freeze.

If you can't get in through Recovery Mode or an older kernel (both in GRUB, described above), then you should try Stefan Glasenhardt's remastered LiveCD with the patched kernel-modules for i855. You can find it along with more information here:
[http://glasen-hardt.de/?p=568](http://glasen-hardt.de/?p=568)

---

### Post by oxo2oxo on 2010-05-26
Latest update, sun stopped play !, ie the weather has been too good, however download of Stefan Glasenhardt's remastered LiveCD at [http://glasen-hardt.de/?p=568](http://glasen-hardt.de/?p=568) seems to do the trick. Am having a few repository issues will report back

---

