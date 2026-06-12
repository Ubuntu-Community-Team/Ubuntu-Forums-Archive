---
title: "X Server problem."
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Jordan777 on 2007-06-29
I had to reinstall Ubuntu (no problem just  a simple / re installation but I'm having the same problem as before right after restarting for updates.  There is some kind of X server error.  Ubuntu doesn't start up it just gives me the command line to log in but it's only a black screen with some stuff and the command line.  Then after a few seconds a bunch of jumbled text comes up and it says there was a fatal error with the X server or something like that.  Anyone know what to do?  I didn't do anything but install the updates and put on my graphics card restricted drivers.  

My system

320 HDD
2 GB DDR2 ram
Nvidia 8800 GTX 320MB

I built it.  I don't know what kind of info you needed so I just included my specs.  Ubuntu was running great until last night after I shutdown.  this morning I got the X server error and reinstalled then i just got it again after restarting.  I am dual booting XP and Ubuntu.:(:(

---

### Post by Jordan777 on 2007-06-29
*UPDATE*  I took these pics of the screens I received.  Anyone know what to make of them?  And I looked at another topic and got into the configuration settings using [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg ran[/COLOR] and saw that I was using the vesa drivers so that can't be it.  I got out of it though because I didn't want to mess up anything further.

********Screenshots********
[[IMG]http://img87.imageshack.us/img87/9372/downloadkt7.jpg[/IMG]](http://imageshack.us)
Shot at 2007-06-29

[[IMG]http://img248.imageshack.us/img248/3177/download1ze2.jpg[/IMG]](http://imageshack.us)
Shot at 2007-06-29

[[IMG]http://img266.imageshack.us/img266/9450/download2ru6.jpg[/IMG]](http://imageshack.us)
Shot at 2007-06-29
**************************
Sorry the screens are so big I forgot to edit them.

Anyone know what I can do?:(

---

### Post by fain on 2007-06-30
check under /lib/linux-restricted-drivers/your kernel version/
or on a 64bit
/lib64/linux-restricted-modules

look for a hidden file called .nvidia_new_installed or something like that

i just had a problem like this and i removed that file and installed the driver and booted right in. 
although i do not see the api mismatch on your error.
when i installed the last update for the restricted modules i got api mismatch error.
i run the compiled driver from nvidia-installer.
i installed nvidia-glx-new and got the error you have.
so i purged it found that hidden file, deleted it
then built the driver again
works great now :) 

check here for more info on this bug
[URL="https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217"]
https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217[/URL]

hope this helps.

---

### Post by Silvestre on 2007-06-30
You must uninstall your nvidia-driver:

On terminal:

```
NVIDIA-Linux-x86-1.0......pkg1.run --uninstall
```

Have you a new kernel? Then you need the new kernel-headers and you need to uninstall

the nvidia-kernel-common and linux-restricted-modules

Further you need to deny the start to "nv" driver

```
/etc/default/linux-restricted-modules-common
```

```
DISABLED_MODULES="nv"
```

When you have cleaned yor pc from all the nvidia-parts you can install the new driver.

WARNING!!! This is only as info because i run linux alone on a pc. I don't know what should you do, if you are running 2 systems, but i think that you will not have problems for updates under Windows.

---

### Post by Jordan777 on 2007-06-30
Hey thanks guys.  I just reinstalled my / and it booted ok (of course).  IF the problem happens again I will definitely take your advice.  I'm going to look through what you said and try some of that now I think to keep the crash from happening in the future.  Again, thank you very much for you're help.

---

