---
title: "Live CD / Live USB will not boot no matter what"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by Hunty6 on 2012-01-12
Hi! 

For the past 3 days I have been trying to install Kubuntu 11.10 and nothing seems to work. 

I burned 2 live CDs, one of them was at lowest burn speed possible(the 2nd one), both md5sums were fine and I have downloaded the first file from Opera web browser and the second from Firefox. Since both these CDs didn't work, I tried with a USB stick and the same files and the same result happened. I thought it could be an error in the file itself but somehow the same thing happens to me with the newest release (the Beta 12.04 one) so it's most likely something wrong with my settings, I guess.

Whenever I try to launch the Install option from the main menu or the Boot from Live CD option, the Loading pops in and whenever my desktop is supposed to appear I get some screen that looks like a broken screen, and I can't do anything from there, I gotta reboot manually.

I tried checking the files from the Check files option on the Live CD and it gives me 1 error, I tried running it with the error and this is what happens. The error seems to be located in the squashfs file, since it's the last file I can see getting ''checked'' by the system.

I am currently running Windows 7 and Kubuntu 11.10 in dual boot but am willing to get rid of Windows, thus why I am trying to boot the live CD and do a new proper install (I want to format my HDD and install Kubuntu 11.10)

Any comment would be greatly appreciated, thanks for the support !

---

### Post by utnubuuser on 2012-01-12
That sounds like a driver issue.  It'd help to post some system info so people can see what kind of equipment you're using.

Have you tried some of the boot options available with the F4 or F6 keys?  Maybe try adding "nomodeset" to the kernel parameter

In any case, search the forums for liveCD kernel parameters...

---

### Post by Hunty6 on 2012-01-12
> **utnubuuser said:**
> That sounds like a driver issue.  It'd help to post some system info so people can see what kind of equipment you're using.

Have you tried some of the boot options available with the F4 or F6 keys?  Maybe try adding "nomodeset" to the kernel parameter

In any case, search the forums for liveCD kernel parameters...

I'm sorry I forgot the system infos in my first post  

I am running an Asus G60JX (G51J series, somehow) laptop. Intel core i5 CPU (Quad core), 4G of RAM. Graphics running under an NVIDIA GeForce GTS 360M.

I am not a ''newbie'' on Linux nor am I an expert :mrgreen: I have installed my first distro on semi-graphical mode and god, I don't wanna have to go trough this again, if possible :P

I went trough the options of F4/F6 menus, but i'm not quite sure which one to pick, i'll try with the nomodeset. Must admit I do not know what those other modes do, might be able to find our somewhere in the docs.

Thanks for the reply ! I'll keep you updated.

---

### Post by Desert Sailor on 2012-01-12
I had a similar problem with the original download.  There was a bug which has been squashed for me.  I waited a couple of months after release and then selected the version upgrade from the upgrade manager.  Upgrade got the latest fixes, and I installed without problem.  

I agree that a new (fresh) install is preferable, but this time, an update is the only thing which would work for me.  

Good luck.

---

### Post by mastablasta on 2012-01-13
> **Hunty6 said:**
>  
I went trough the options of F4/F6 menus, but i'm not quite sure which one to pick, i'll try with the nomodeset. Must admit I do not know what those other modes do, might be able to find our somewhere in the docs.

 
nomodeset turns off modesetting, acpi= off turns off ACPI :-) 
 
anyway: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
yeah it seems like graphics driver issue. Maybe you have switchable graphics? 
 
if it's graphics driver and if boot parameters can't get it to boot then the easiest way is to simply use alternate CD and install propper drivers via text mode installer.

---

### Post by Hunty6 on 2012-01-13
Thanks a lot for the help!

I have tried with the nomodeset and it worked perfectly. I have also run a quick search about what exactly nomodeset would do, and it turns out that it was the problem.

> Note that this option is sometimes needed for nVidia cards when using the default "nouveau" drivers. Installing proprietary nvidia drivers usually makes this option no longer necessary, so it may not be needed to make this option permanent.

Thanks a lot!

---

### Post by matza55 on 2012-01-14
> **Hunty6 said:**
> Thanks a lot for the help!

I have tried with the nomodeset and it worked perfectly. I have also run a quick search about what exactly nomodeset would do, and it turns out that it was the problem.



Thanks a lot!

Graphiccards is sometimes a complete mess. I have an HD5450, now it works, but it took much hard work.

---

