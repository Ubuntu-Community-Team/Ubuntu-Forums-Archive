---
title: "We can we expect the flickering startup to be fixed?"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-08-17
I get a black screen white screen etc flicker before gdm and one after.

[edit] **Looking slick now.**

---

### Post by martijntje on 2009-08-17
I don't. Perhaps it is a good idea for you to post some more details about the hardware you are using.

---

### Post by wayne_cat on 2009-08-17
> **philinux said:**
> I get a black screen white screen etc flicker befire gdm and one after.

do you have the package xsplash on you system? GDM starts xsplash (the "white flicker")

```
root@macbook:~# cat /etc/gdm/PreSession/Default 
#!/bin/sh
#
# Note that any setup should come before the sessreg command as
# that must be 'exec'ed for the pid to be correct (sessreg uses the parent
# pid)
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin:$PATH:/bin:/usr/bin"

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash &
fi

root@macbook:~# 

```

---

### Post by edujose on 2009-08-17
> **philinux said:**
> I get a black screen white screen etc flicker befire gdm and one after.

Here too, with ATI graphics. Seems they are adjusting xsplash to behave.

Some Xsplash bugs in Launchpad about this:

[lp bug 411720 - 	 Image size popping on login]("https://bugs.launchpad.net/xsplash/+bug/411720")
[lp bug 413399 - [i945] Screen flickers after jaunty update]("https://bugs.launchpad.net/xsplash/+bug/413399")

I should report this too in one of these bugs (though not sure what the "popping" bug indicates, maybe flickering?)

---

### Post by frustphil on 2009-08-17
Me too..
> Intel Corporation 82945G/GZ Integrated Graphics Controller

---

### Post by eldragon on 2009-08-17
hmmm, enabling KMS should fix it ;) thats for intel drivers.

the rest has to wait

---

### Post by ranch hand on 2009-08-17
I get some flicker but just a flash or white and back to my background.

I have one 9.10 installation on 1 partition and it is stable.  The rest (yes I have several variations) are on 2 partitions and they all flicker.

Do those that have single partion install have this problem?

I also have another install that does not have this problem.  It is on 2 partitions.  It was a clean install of A1. Has been updated daily and all the grub-common files are in place but it has never had pc-grub offered as an update.

This, of coarse, means it is running on grub-legacy.

Are there any folks out there running 9.10 with grub-legacy and do they have this flickering?

These are things that I have just really noticed in the last 2 days and have been wondering about all day today.

---

### Post by frustphil on 2009-08-17
> **eldragon said:**
> hmmm, enabling KMS should fix it ;) thats for intel drivers.

the rest has to wait

Isn't KMS enabled by default for intel drivers?

---

### Post by papangul on 2009-08-17
I don't have this problem. 

The console that runs before and after gdm (xserver) start/stop has a non native resolution while the xserver runs at the native resolution of the lcd monitor.

If the lcd monitor has bad capacitors or has some other flaws, it may cause a fickering while switching resolutons.

---

### Post by VMC on 2009-08-17
> **eldragon said:**
> hmmm, enabling KMS should fix it ;) thats for intel drivers.

the rest has to wait

I can't use KMS for my Intel i865 chip. It freezes. So I'm stuck with using nomodeset until if and when Intel drivers get fixed. I also get that "flicker".

---

### Post by wfp on 2009-08-18
I had that flicker also. I am back on jaunty. Alphas are not for the weak of heart. I could not get any sound either. I went through the pulse audio thread, and tried some fixes with no luck. I also noticed inner Temps were about 15 Celsius higher than on Jaunty64.

---

### Post by philinux on 2009-08-18
> **martijntje said:**
> I don't. Perhaps it is a good idea for you to post some more details about the hardware you are using.

See my signature. I also get a green stripe across the top of the screen briefly after grub but before the loading ubuntu splash.

This was a clean aplha3 install. Xsplash got installed with it.

---

### Post by zanglang on 2009-08-18
Using a standard Dell laptop chipset:
> Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
With modeset=1 turned on in i915, but still have the flicker.

Isn't xsplash a dependency of ubuntu-desktop, too?

---

### Post by plun on 2009-08-18
> **philinux said:**
> See my signature. I also get a green stripe across the top of the screen briefly after grub but before the loading ubuntu splash.

This was a clean aplha3 install. Xsplash got installed with it.

Note that the x-start is going to be moved to directly after a basic boot. Otherwise we cannot see the Xsplash.

Therefore its just a "mess" for the moment when x starts directly before GDM.

Its unknown when this change is scheduled... ????   Scott J Remnant ?

---

### Post by philinux on 2009-08-18
Many thanks plun.

---

### Post by plun on 2009-08-18
> **philinux said:**
> Many thanks plun.

Well.. then its also the KMS question but I believe that first must
x-start be moved.... it seems to be vacation time for the moment so 
who knows  ??

---

### Post by BwackNinja on 2009-08-19
I wonder whether they'll wait for input hotplugging in X to migrate from hal to udev before implementing it. [https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy) it'll be interesting seeing when we finally have a system without hal and that'll make it so that the only additions to the initrd would be X (and dependencies like the DDX and hopefully not mesa; 3D graphics is silly during boot) and udev (if it isn't there already). Udev would only be a dependency for input hotplugging, not needed if we wont do any input, but we've got the cancel fsck and soon changing which OS is being booted from that screen.

[http://hoegsberg.blogspot.com/2007/01/plymouth.html](http://hoegsberg.blogspot.com/2007/01/plymouth.html) is a fun little post talking about splash screens using X running from the initrd, and even mentions KMS as a helper in initializing the graphics card earlier.

---

### Post by zoomy942 on 2009-08-21
mine flickers too.  intel x3100.  this thread didnt say much about fixing it

---

### Post by philinux on 2009-08-31
Starting to look slick now.

---

### Post by amano on 2009-08-31
> **wfp said:**
> I am back on jaunty. Alphas are not for the weak of heart. I could not get any sound either. I went through the pulse audio thread, and tried some fixes with no luck. I also noticed inner Temps were about 15 Celsius higher than on Jaunty64.

Well, just going back to Jaunty will ensure that your bugs are still present in the final karmic. The only way to get rid of them is to test for bugs, file those bugs and test all proposed workarounds and code fixes. Otherwise many bugs are likely to stay.

---

