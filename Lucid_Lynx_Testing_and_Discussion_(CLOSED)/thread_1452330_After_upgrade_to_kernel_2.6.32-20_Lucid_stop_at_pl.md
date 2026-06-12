---
title: "After upgrade to kernel 2.6.32-20 Lucid stop at plymouth"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chromagnum on 2010-04-11
So, after upgrade kernel, here:

```
[INSTALL, DEPENDENCIES] linux-headers-2.6.32-20
[INSTALL, DEPENDENCIES] linux-headers-2.6.32-20-generic
[INSTALL, DEPENDENCIES] linux-headers-2.6.32-20-generic-pae
[INSTALL, DEPENDENCIES] linux-image-2.6.32-20-generic-pae
[UPGRADE] ca-certificates-java 20091021 -> 20100406ubuntu1
[UPGRADE] linux-generic-pae 2.6.32.19.20 -> 2.6.32.20.21
[UPGRADE] linux-headers-generic 2.6.32.19.20 -> 2.6.32.20.21
[UPGRADE] linux-headers-generic-pae 2.6.32.19.20 -> 2.6.32.20.21
[UPGRADE] linux-image-generic-pae 2.6.32.19.20 -> 2.6.32.20.21
[UPGRADE] xserver-xorg-video-r128 6.8.1-2 -> 6.8.1-2ubuntu1
```

When I rebooted the system and use new kernel, booting process stop at plymouth. I did booting onto recovery mode and got a msg like "plymouth failsafe etc etc." Right now I'm using kernel 2.6.32-19. Is it a bug, or is it just me? Anyone stumble onto the similar problem as well?

I don't know is this the similar problem or not:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561053)

---

### Post by VMC on 2010-04-11
> **Chromagnum said:**
> linux-headers-2.6.32-20-generic-pae
...
When I rebooted the system and use new kernel, booting process stop at plymouth. I did booting onto recovery mode and got a msg like "plymouth failsafe etc etc." Right now I'm using kernel 2.6.32-19. Is it a bug, or is it just me? Anyone stumble onto the similar problem as well?

I don't know is this the similar problem or not:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561053)

I noticed your using *pae*. Any reason for using it? More than 3gigs of ram, or are you running 32-bit? Also that bug report is kind of vague. Would need more to go on.

Here's my kernel:
Linux 2.6.32-20-generic #29-Ubuntu SMP Fri Apr 9 20:35:55 UTC 2010

I have no problem with the new kernel. I'm using 32-bit, P4, Intel i865 video.

---

### Post by Chromagnum on 2010-04-11
> **VMC said:**
> I noticed your using *pae*. Any reason for using it? More than 3gigs of ram, or are you running 32-bit? Also that bug report is kind of vague. Would need more to go on.

Here's my kernel:
Linux 2.6.32-20-generic #29-Ubuntu SMP Fri Apr 9 20:35:55 UTC 2010

I have no problem with the new kernel. I'm using 32-bit, P4, Intel i865 video.

The pae? Honestly I don't know, it is the way it is since I'm using Karmic. And yeah, I'm running 32 bit. Only have 1 gig of ram, p4, nvidia fx5500.

Right now I'm using this:
Linux kickass 2.6.32-19-generic-pae #28-Ubuntu SMP Wed Mar 31 18:57:46 UTC 2010

---

### Post by _h_ on 2010-04-11
Just got the upgraded kernel just now, working nice and dandy without a hitch.

```
Linux 2.6.32-20-generic #29-Ubuntu SMP Fri Apr 9 20:35:00 UTC 2010 x86_64 GNU/Linux
```

---

### Post by Uncle Spellbinder on 2010-04-11
Running 2.6.32-20-generic pae here, 8 gigs of ram, 32 bit Lucid Beta 2. No issues to report. All is well.

---

### Post by Chromagnum on 2010-04-11
Okay now I feel embarass. After rebooted it is finally works. Strange though, I have to use old kernel before boot again to use new kernel. 

Linux kickass 2.6.32-20-generic-pae #29-Ubuntu SMP Fri Apr 9 22:05:09 UTC 2010

I'm gonna just mark as solved, obviously this is a false report. I'm sorry guys.

---

### Post by kcleworth on 2010-04-11
I've also had problem with kernel 2.6.32-20 aswell as a few people over at:

[http://ubuntuforums.org/showthread.php?p=9109647#post9109647](http://ubuntuforums.org/showthread.php?p=9109647#post9109647)

I can't only make Lucid boot now if I use the previous -19 kernel...

---

### Post by lovinglinux on 2010-04-12
I can boot, but grub doesn't update. I have two instances of Lucid installed, one in a testing partition and the other is my main system. I have upgraded both with the latest kernel and now only the testing partition updates the grub. The main partition, which is now at the end of the grub,  still shows 2.6.32-19 kernel, although 2.6.32-20 has been installed. 

I have already tried to do a update-grub without success. It looks like updated, but then the test grub is still loading.

---

### Post by kcleworth on 2010-04-12
This bug is reported here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561140](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561140)

Please add your information if it is affecting you.

---

### Post by ubername on 2010-04-12
> **lovinglinux said:**
> I can boot, but grub doesn't update. I have two instances of Lucid installed, one in a testing partition and the other is my main system. I have upgraded both with the latest kernel and now only the testing partition updates the grub. The main partition, which is now at the end of the grub,  still shows 2.6.32-19 kernel, although 2.6.32-20 has been installed. 

I have already tried to do a update-grub without success. It looks like updated, but then the test grub is still loading.

You will need to update grub from the testing partition or run
```
sudo grub-mkconfig -o /<mountpoint-for-testingpartition>/boot/grub

```
from the main partition and then rename grub.new to grub.cfg in the testing partition's /boot/grub.

When you update grub when booted from the main partition it writes grub.cfg to the main partition /boot/grub by default. However when you boot, grub looks for the grub.cfg in the testing partition.

There are other ways to fix this (for example, you could copy grub.cfg from the main /boot/grub to the testing /boot/grub.)

---

### Post by Chromagnum on 2010-04-12
Finally I can boot to new kernel and everybody shows up with the problem. Okay, I'm gonna mark this thread again unsolved, and for the further discussion, here:

[http://ubuntuforums.org/showthread.php?t=1452368](http://ubuntuforums.org/showthread.php?t=1452368)

---

### Post by BrokeMahPC on 2010-04-12
No problems here with that upgrade - all working fine:
10.04 Desktop i386, 32 bit
Updated 12pm GMT - 12th April

---

### Post by kansasnoob on 2010-04-12
> **lovinglinux said:**
> I can boot, but grub doesn't update. I have two instances of Lucid installed, one in a testing partition and the other is my main system. I have upgraded both with the latest kernel and now only the testing partition updates the grub. The main partition, which is now at the end of the grub,  still shows 2.6.32-19 kernel, although 2.6.32-20 has been installed. 

I have already tried to do a update-grub without success. It looks like updated, but then the test grub is still loading.

Try running "update-grub" in the testing installation (the one at the top of the boot menu) and see if that picks it up. If not read onward:

Boot into each Lucid (I'd expect to find the problem in the one that won't update) and run the command:

```
ls /boot/grub
```

You'll see columns of files & directories in alphabetical order. Look to see if you have both a grub.cfg and a menu.lst. If so you found the problem :)

You probably already know but grub.cfg is a grub2 file whereas menu.lst is a legacy grub file. Anyway having mixed grub files causes problems.  My preferred way of dealing with that is basically explained in Appendix #2 here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Of course after backing up your /boot/grub you'd "mkdir" a new one and /dev/sda may not be the proper destination to install grub.

If that isn't the problem or if you just need more detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You may of course want to start a new thread, if so feel free to send me a PM pointing me to it.

---

### Post by lovinglinux on 2010-04-12
> **ubername said:**
> 
When you update grub when booted from the main partition it writes grub.cfg to the main partition /boot/grub by default. However when you boot, grub looks for the grub.cfg in the testing partition.

Thanks. I don't exactly understand this. This always worked with Karmic. My grub in use was created by whichever system was updated with a new kernel last or the last I run update-grub. I forgot to mention that the testing partition is on the drive with the MBR.

> **kansasnoob said:**
> You probably already know but grub.cfg is a grub2 file whereas menu.lst is a legacy grub file. Anyway having mixed grub files causes problems.  My preferred way of dealing with that is basically explained in /[/url]

You may of course want to start a new thread, if so feel free to send me a PM pointing me to it.

Thanks, but I have been using grub2 since Karmic Beta and I always fo clean installs, so there is no menu.lst anymore.

BTW, grub2 is only causing me headaches. In Karmic there was a bug in which grub would take 23 seconds to load, because the main partition with the grub files wasn't in the MBR drive. Now this...](*,)

---

### Post by lovinglinux on 2010-04-12
After updating grub in the testing partition, I can see both kernel options on both system, but grub in use is still the one from the testing partition.

I have created a new thread for my issues [http://ubuntuforums.org/showthread.php?t=1452866](http://ubuntuforums.org/showthread.php?t=1452866)

---

### Post by mc4man on 2010-04-12
In regards to having 2 grub2 installs (dual booting lucid, one w/nouveau, one w/nvidia-current.

When the kernel updates in the 2nd listed install I've always had to run an update-grub in the first listed for the new one (in 2nd listed) to show up.

If a grub update happens in the 2nd listed that requires an configure grub-pc then I'm pretty sure that the 2nd listed then becomes the first listed (depending on how you configure
(at times I forget which is which, but pretty sure they've flipped -flopped a few times

---

### Post by lovinglinux on 2010-04-12
> **mc4man said:**
> In regards to having 2 grub2 installs (dual booting lucid, one w/nouveau, one w/nvidia-current.

When the kernel updates in the 2nd listed install I've always had to run an update-grub in the first listed for the new one (in 2nd listed) to show up.

If a grub update happens in the 2nd listed that requires an update-grub pc then I'm pretty sure that the 2nd listed then becomes the first listed
(at times I forget which is which, but pretty sure they've flipped -flopped a few times

Still no joy. 

BTW, they both have nvidia current.

---

