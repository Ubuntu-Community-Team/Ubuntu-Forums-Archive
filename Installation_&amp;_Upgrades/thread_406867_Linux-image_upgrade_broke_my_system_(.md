---
title: "Linux-image upgrade broke my system :("
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by leona on 2007-04-11
Hi

Had one of those auto pop up things that tells me I've got updates to install, take a quick glance and apply them.

It tells me I have to restart, ok so I do.

When it restarts I get confronted with a text screen saying X would not start due to a mis configuration?

Ok, after I had calmed down, I restarted the pc and thankfully grub keeps a the old system image, so I booted the old one fine (2.6.15-27).

I have no idea what has gone wrong, I assume now this new one is unusable? 

I installed 
```
2007-04-11 18:30:14 upgrade linux-image-2.6.15-28-amd64-generic 2.6.15-28.51 2.6.15-28.53
```

The xorg log, everything looks normal until you see
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux leona-amd64-3Ghz 2.6.15-28-amd64-generic #1 SMP PREEMPT Tue Mar 13 20:51:52 UTC 2007 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 11 18:34:58 2007
----------------------    loads of info no errors until   -------------------------------
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

What has gone wrong and how do 'I' fix it?

Thanks

Leona

---

### Post by heimo on 2007-04-11
What driver are you using in Xorg? Did you install ati fglrx or nvidia drivers? (in this case, reinstalling them might work) Check your Xorg log file  /var/log/Xorg.0.log

---

### Post by leona on 2007-04-11
> **heimo said:**
> What driver are you using in Xorg? Did you install ati fglrx or nvidia drivers? (in this case, reinstalling them might work) Check your Xorg log file  /var/log/Xorg.0.log

Hi Heimo, I didn't install any drivers, just the image as per the update, I 'assumed' that anything it needed would be installed / reinstalled with the update

Do you mean this 
```

(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver

```

---

### Post by GeDaMo on 2007-04-11
The same thing happened to me. I believe the nvidia kernel module is the wrong version. I did sudo dpkg-reconfigure xserver-xorg and selected the nv driver to get going again.

---

### Post by heimo on 2007-04-11
Yeah. Basically - these problems - X breaking after kernel update - are often related to restricted/binary/proprietary drivers, like in this case (nvidia driver). nv works fine.

---

### Post by GeDaMo on 2007-04-11
I completely uninstalled nvidia-glx and the restricted modules then reinstalled and now it appears to be working.

---

### Post by karachuonyo on 2007-04-11
well i also did the upgrade and everything went smoothly. Strange enough the previous kernel upgrade broke my system and i had to repair my x-org to get started again. Despite that my sound has worked only in mono and volume is very low. This time after the kernel upgrade my faulty sound has been cured.:D

---

### Post by leona on 2007-04-12
> **GeDaMo said:**
> The same thing happened to me. I believe the nvidia kernel module is the wrong version. I did sudo dpkg-reconfigure xserver-xorg and selected the nv driver to get going again.

:( I did this and now all I have is a screen that resembles some kind of multi coloured carpet! Not very good.  I ran everything as defaults, how can I get my display back working again?

---

### Post by whitefort on 2007-04-12
> **leona said:**
> :( I did this and now all I have is a screen that resembles some kind of multi coloured carpet! Not very good.  I ran everything as defaults... 

I feel your pain.  ***Exactly*** the same thing happened to me.  :(   

I'm sorry I can't offer any suggestions that might help.  I'm on the verge of going into a rant here, but I'll restrain myself...  But I feel like I don't ***ever*** want to allow any of those updates again, as this is the second time they've wrecked my computer.

I do hope you get things working again!  

When you do, you might consider installing Mondo and learning how it works (it looks complex, but isn't really).  You can burn an image of your entire system to CDs or DVDs, and in case of disaster get things exactly back to the point where you made the backup.

Thankfully I've been doing this regularly for a while, otherwise (thanks to this latest 'update') I would have had a trashed computer.

---

### Post by MarlonNelson on 2007-04-12
i had a similar experience... almost the exact X output.

in my case, the upgrade had modified all the entries in /boot/grub/menu.lst to use the root for my feisty beta installation (i also had entries for winXP and edgy).  edgy & feisty use the same boot partition but use different root partitions.

i was able to solve the problem by editing the appropriate menu.lst entries to point back to the edgy root partition.

i think the update might have also changed the syntax of to use root=UUID=..., instead of what it used to be (i forget).  unhelpfully, it also appeared to save a backup of the new menu.lst as menu.lst~, so i don't know what the original menu.lst looked like before the update.

---

### Post by GeDaMo on 2007-04-12
> **leona said:**
> :( I did this and now all I have is a screen that resembles some kind of multi coloured carpet! Not very good.  I ran everything as defaults, how can I get my display back working again?

When you reconfigure xserver-xorg, it makes a backup copy of /etc/X11/xorg.conf in the /etc/X11 directory - you could copy an earlier one onto xorg.conf or compare the two to find the differences.

---

### Post by leona on 2007-04-12
Arr thank you for that, I did just that, instead I backed up the current conf file and restored the back up, rebooted and got my screen back, it doesn't resolve the problem of the kernel cos I'm booting the old one now, 2.6.15.27 not .28 cos it will not load at all (see post #1) but at least I have a usable machine. I guess I have to wait for the nvidia modual to be released?

---

### Post by GeDaMo on 2007-04-12
You could try uninstalling then reinstalling nvidia-glx and the restricted modules packages. It seemed to fix it for me.

---

### Post by leona on 2007-04-12
> **GeDaMo said:**
> You could try uninstalling then reinstalling nvidia-glx and the restricted modules packages. It seemed to fix it for me.

Ya I would like to try that, I guess I would need to boot the kernel that fails an issue the reinstall commands from cmd line?  Could you give ma an idea how I do that, I do like my GUI's not so good with the cmd line, sorry.

---

### Post by GeDaMo on 2007-04-12
If you have it working with an older kernel, do it in Synaptic.

---

### Post by bulldog on 2007-04-12
Type in a terminal ```
uname -a
``` to see your kernel version.
Install restricted modules.not the nvidia driver.
```
sudo aptitude install linux-restricted-modules-2.6.20-14-generic
``` <---here your kernel version of course.
In most cases it would resolve the problems.
If not try```
sudo dpkg-reconfigure xserver-xorg
``` and choose the desired driver and resolution.

---

### Post by leona on 2007-04-12
> **GeDaMo said:**
> If you have it working with an older kernel, do it in Synaptic.

Oh right, will that update the correct kernel then ?

---

### Post by Godzig on 2007-04-12
Thanks Bulldog, that worked great.  For clarification's sake this is what had me thrown for a while (still very much a newbie): I was removing and installing nvidia-glx and nvidia-kernel-common, thinking that nvidia-kernel-common would be the modules my xorg.conf was looking for.  That didn't work but when I finally installed (using uname -a to get my kernel version):
```
sudo aptitude install linux-restricted-modules-2.6.17-11-generic
```
Behold, my beloved system reappeared to me as though a phantom through a fog of green terminal characters.

---

### Post by leona on 2007-04-12
> **GeDaMo said:**
> If you have it working with an older kernel, do it in Synaptic.

Nice, worked, yes I have my lovely GUI back and no sign of the multi coloured carpet :)

Happy again.

BTW is there away of disabling, removing Kernel updates from the updater, cos this will be the last time I run one of those, far to much hassle.

Thank you all once again, much appreciated

---

