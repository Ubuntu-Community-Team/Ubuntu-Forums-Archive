---
title: "New Karmic Kernel 2.6.31-19"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2010-02-04
I think this just came, today (I didn't see it, yesterday). How many of you are installing it? Is it working well?

Tim

---

### Post by wkulecz on 2010-02-04
If it ain't broke, don't fix it!

If its not tagged as a security update, I'd ignore it unless your system is just for playing around with and you don't suffer if it stops working.

I'll install it next time I boot 9.10 as my 9.10 system is just to give me a heads up as to major differences to expect in 10.04 from 8.04,  OTOH 7.10 left me rudely suprised by PulseAudio in 8.04 -- I had audio issues initially but updates eventually resolved them. 

--wally.

---

### Post by ratcheer on 2010-02-04
According to what I can determine on LaunchPad, it is a security update.

Tim

---

### Post by Enigmapond on 2010-02-04
Why doesn't this show when I do an update in the terminal? I don't use update manager..in fact I deleted it as it was getting in the way.

---

### Post by oldos2er on 2010-02-04
Give it some time to propagate to all the servers.

---

### Post by ratcheer on 2010-02-04
Well, maybe I jumped the gun. While my package manager is picking up various parts of this new kernel (image, backports, etc), I  cannot yet find the release of linux-meta which corresponds to it. So, it is probably too soon to install it.

Here is what I am finding as NEW packages in aptitude:

linux-headers-2.6.31-19-generic
linux-backports-modules-2.6.31-19-generic
linux-backports-modules-alsa-2.6.31-19-generic
linux-image-2.6.31-19-generic

Sorry,
Tim

---

### Post by PC_load_letter on 2010-02-04
I just installed it and running it as I write this. Nothing bad, the usual everything, by this I mean the usual awesomeness :D. I'm running the 64bit version btw.

---

### Post by sportsdude81 on 2010-02-05
Same here. running great so far.  64bit system as well

---

### Post by Blayze187 on 2010-02-05
> **ratcheer said:**
> I think this just came, today (I didn't see it, yesterday). How many of you are installing it? Is it working well?

Tim

 i installed the updates, and now it wont boot to the desktop, it shows the login screen, then all that shows up is the terminal... can you guys help me? in a Complete N00b to this. plz help!

---

### Post by raysaunders on 2010-02-05
Hmmmm.....

I just installed the update as proposed by Update Manager and the system no longer boots.

Message is "Missing Operating System_" :shock:

Guidance anyone?

---

### Post by shriramrs31 on 2010-02-05
> **Blayze187 said:**
> i installed the updates, and now it wont boot to the desktop, it shows the login screen, then all that shows up is the terminal... can you guys help me? in a Complete N00b to this. plz help!

Try choosing the old kernel from GRUB menu and booting with it.

---

### Post by shriramrs31 on 2010-02-05
> **raysaunders said:**
> Hmmmm.....

I just installed the update as proposed by Update Manager and the system no longer boots.

Message is "Missing Operating System_" :shock:

Guidance anyone?

My first guess would be GRUB problem. Try booting via LiveCD and then restoring GRUB. Here's a good link that might point you in the right direction (even though it is for restoring after an accidental windows bootloader).

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope this helps ;-) Good luck.

---

### Post by saif_held on 2010-02-05
32-bit, installed and working as usual.

---

### Post by ratcheer on 2010-02-05
> **Blayze187 said:**
> i installed the updates, and now it wont boot to the desktop, it shows the login screen, then all that shows up is the terminal... can you guys help me? in a Complete N00b to this. plz help!

If you use a proprietary display driver, you probably just need to reinstall it for the new kernel.

Tim

---

### Post by raysaunders on 2010-02-05
> **shriramrs31 said:**
> My first guess would be GRUB problem. Try booting via LiveCD and then restoring GRUB. Here's a good link that might point you in the right direction (even though it is for restoring after an accidental windows bootloader).

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope this helps ;-) Good luck.

Thank you, shriramrs31. Your guidance sorted me out. All's well.

---

### Post by PC_load_letter on 2010-02-05
> **ratcheer said:**
> If you use a proprietary display driver, you probably just need to reinstall it for the new kernel.

Tim

I'm using Nvidia's driver and I didn't need to do anything when I updated.

---

### Post by ratcheer on 2010-02-05
> **PC_load_letter said:**
> I'm using Nvidia's driver and I didn't need to do anything when I updated.

Cool. I always have to reinstall it for each new kernel.

Tim

---

### Post by crucialhoax on 2010-02-05
Mine updated last night. I noticed no differences in the system. Then again I don't use my laptop to heavily. However it did appear as a security update in update manager for those who were asking...

---

### Post by EMVirostek on 2010-02-05
I just updated as well...and my only issue is now i have 3 different kernels in my grub menu...along with xp.  is there a reason that all the kernels stay in grub?  are they even accessible?  is there a way to get rid of the oldest?  thanks...

---

### Post by sporkinum on 2010-02-05
Go into your package manager and search for 2.6. . Uncheck the ones you don't want anymore. After a reboot, they will no longer be in grub.

---

### Post by SecretCode on 2010-02-05
> **PC_load_letter said:**
> I'm using Nvidia's driver and I didn't need to do anything when I updated.

> **ratcheer said:**
> Cool. I always have to reinstall it for each new kernel.

Tim

dkms may be the solution you need!

---

### Post by Silvertones on 2010-02-05
Upgraded. All good so far..............;)

---

### Post by RazVayne on 2010-02-05
An article on the kernel update [[COLOR="Magenta"]here[/COLOR]]("http://news.softpedia.com/news/10-Kernel-Vulnerabilities-in-Ubuntu-6-06-8-04-8-10-9-04-and-9-10-134162.shtml").

---

### Post by jenaniston on 2010-02-05
> **Blayze187 said:**
> i installed the updates, and now it wont boot to the desktop, it shows the login screen, then all that shows up is the terminal... can you guys help me? in a Complete N00b to this. plz help!

**install all the updates and system won't boot** . . . *it happens* - maybe not to everyone -
but it has to me as well - and with other linux distributions also.

I now avoid updates - 

Unless you don't absolutely need the machine working right then
 and have time and want to experiment for the fun of it - imho, update at your own peril.

---

### Post by ratcheer on 2010-02-05
> **RazVayne said:**
> An article on the kernel update [[COLOR=Magenta]here[/COLOR]]("http://news.softpedia.com/news/10-Kernel-Vulnerabilities-in-Ubuntu-6-06-8-04-8-10-9-04-and-9-10-134162.shtml").

Thank you. Excellent info.

Tim

---

### Post by howefield on 2010-02-05
> **jenaniston said:**
> imho, update at your own peril.

Or the converse, don't update at your peril :)

To each their own, but prepared with a disk image, a borked update means (at worst) you are only 15 minutes or so away from a restored disk,.

Just enough time for a cup of coffee. YPMV. :)

---

### Post by eraevous on 2010-02-05
I don't know what I did wrong, but I installed the new kernel and immediately (either on reboot, or while trying to shut down) hit a kernel panic. Everything else works just fine. I'm using the previous version right now, and my other partition still boots Win7. Any advice on what to do, how to solve the problem, or even how to diagnose what's wrong?

---

### Post by SaintDanBert on 2010-02-05
> **sporkinum said:**
> 
...
After a reboot, they will no longer be in grub.


Speaking of GRUB -- v2 that is -- "this can happen to you..."

With the switch to GRUB-2, any time you get a new kernel or tinker with your boot-time settings, somehow [highlight]update-grub2[/highlight] runs either automatically or manually. This command creates the files that result in the new-and-improved grub boot menu with all of the various boot-time selections.

Now, every time I load a larger drive into my laptop, I save the olde drive as-is as an external USB drive. Notice, I said **as is**.
I happened to have one of these drives connected when I happened to run
[highlight]update-grub2[/highlight].

Sha-Zaamm!!!  Now I have all of the possible bootables from my primary disk as well as whatever there was on the USB connected drive. Nice to know this will happen and if you need it. However, now I have forty-leven boot choices. These choices are written into the grub configuration regardless of whether the drive remains connected.

Corrective action means that you must run [highlight] update-grub2 [/highlight] again -- this time without the extra boot possibilities present.

SUGGESTION: It might be nice if [highlight] update-grub2 [/highlight] offered (1)enable or disable scans of removable drives or media as part of grub configuration, and (2) optional confirmation dialog "Do you want to boot here...?" for each target found.

Cheers,
~~~ 8d;-/ Dan

---

### Post by auh2o on 2010-02-05
> **PC_load_letter said:**
> I'm using Nvidia's driver and I didn't  need to do anything when I updated.

> **ratcheer said:**
> Cool. I always have to reinstall it for each new kernel.

Tim

The NVIDIA driver was updated/installed automatically after the new kernel was installed as part of the installation process. I was looking at the info in the terminal window in the Update Manager as the installation ran and was pleased to discover this.

> **RazVayne said:**
> An article on the kernel update [[COLOR=Magenta]here[/COLOR]]("http://news.softpedia.com/news/10-Kernel-Vulnerabilities-in-Ubuntu-6-06-8-04-8-10-9-04-and-9-10-134162.shtml").

Thank you! Very good info.

I updated without problems and everything is running smoothly.

---

### Post by Claude Warren on 2010-02-05
I updated my Toshiba Satellite (A505) which has the Realtek RTL98192SE wireless card built in.  When I booted the wireless was not found.  I attempted to rebuild the driver but got a kernel/bounds.c missing error.  I spent several hours attempting to figure out how to fix it with no luck.

I am back to the 2.6.31-17 kernel in the mean time.

I have executed:

sudo apt-get install build-essential linux-headers-generic

and 

sudo apt-get install linux-source

as well as 

sudo apt-get update 

and 

sudo apt-get upgrade

in an effort to resolve the issue.


Anybody have any suggestions?

---

### Post by ratcheer on 2010-02-05
> **Claude Warren said:**
> 


Anybody have any suggestions?

Try "sudo apt-get dist-upgrade".

Tim

---

### Post by Claude Warren on 2010-02-05
OK I tried the **[FONT=Fixedsys]sudo apt-get dist-upgrade[/FONT]**[FONT=Arial]
but it did not update anything.  I attempted to rebuild.. same result.
I download the driver package from Realtek and built in a different directory...same result

What I get is the following:

[/FONT]```

make[1]: Entering directory `/tmp/rtl8192se_linux_2.6.0013.1204.2009/HAL/rtl8192'
make -C /lib/modules/2.6.31-19-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/tmp/rtl8192se_linux_2.6.0013.1204.2009/HAL/rtl8192'
make: *** [install] Error 2

```

---

### Post by Claude Warren on 2010-02-07
**](*,) DOH!**  The problem was in the CBU (Carbon Based Unit)

The short answer is RTFM.

The FM says:

```
sudo su
make
make install
reboot
```

While the CBU typed:

```
sudo make
sudo install
```

Once the CBU followed the FM the problem went away.

---

### Post by beatanga on 2010-02-08
i have a big problem after installing this kernel. 

[http://ubuntuforums.org/showthread.php?p=8796754#post8796754](http://ubuntuforums.org/showthread.php?p=8796754#post8796754)

i see that more people have this. also happend when i installed version 17.

anybody have any idea how is this solved apart from solution being never to update kernel again?

---

### Post by beatanga on 2010-02-09
solution found on this topic

[http://ubuntuforums.org/showthread.php?t=1376781](http://ubuntuforums.org/showthread.php?t=1376781)

with this patch for wubildr

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

:)

---

### Post by MacBear on 2010-02-15
I installed the -19 update on my Dell desktop and it works well enough that I uninstalled 2.6.31-17. Oddky enough when i fired up my Toshiba laptop and ran Synaptic, it said that it was up to date (with 2.6.31-17).  I have almost completely turned to Ubuntu. Still need a GUI OCR program. Soon,... maybe LOL.

---

