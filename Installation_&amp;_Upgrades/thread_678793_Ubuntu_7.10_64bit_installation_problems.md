---
title: "Ubuntu 7.10 64bit installation problems"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by heathenminor on 2008-01-26
Hi,

I'm trying to install 64bit ubuntu 7.10.  

The ubuntu 7.10 live cd presents me with the boot options menu, however both "install" and the "safe mode install" options end with the screen going blank.  The 64bit kubuntu 7.10 live cd has the same behaviour.

I was able to install using the 32bit kubuntu 7.10 live cd and get that working.  

I have also installed 64bit kubuntu using the alt cd.  However when booting the 64 kubuntu the screen goes blank (similar to the live cd booting).  I am able to boot into recovery mode, run command "telinit 3" and am presented with the log in screen.  From here I have been able to update the system (sudo apt-get ugrade) and also install the nvidia driver.  I am still unable to boot the system from the grub boot option though.

What is the best way to proceed toward the goal of a working 64 bit ubuntu system?

system specs:

intel Core2 duo 6600
2 gb ram
asus p5n-e sli motherboard
nvidia 8800 gtx 
creative xfi

Any help would be appreciated.

Thanks.

---

### Post by PmDematagoda on 2008-01-26
Your main cause of that problem is:-
nvidia 8800 gtx

You should install Ubuntu using the Alternate CD and then install the Nvidia drivers and reconfigure the X-Server accordingly.

---

### Post by heathenminor on 2008-01-26
PmDematagoda, thanks for you reply.

>> You should install Ubuntu using the Alternate CD and then install the Nvidia drivers

Ok done this.

However I am still seeing the exact same behavious as the kubuntu 7.10 alt install.
That is, when I attempt to boot I get a blank screen.  I can boot into single user mode and from there run "telinit 3", which gets me into x.

>> then install the Nvidia drivers

Ok, installed this using the restricted drivers app.  But I still can't boot without going into single user mode first.

>> and reconfigure the X-Server accordingly.

Perhaps you could elaborate this point.  What needs to be changed?  
After booting into single user mode and executing "telinit 3" x-windows runs fine.

Is there any way to debug what is going on during boot and why it is failing?  Any log files to look at etc?

---

### Post by heathenminor on 2008-01-26
Workaround found!

This workaround is: Remove the "splash" boot option

from a terminal execute: sudo vi /boot/grub/menu.lst

change this line:
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=dd4400ac-7855-4d5b-afc2-36ffdc7ccaf2 ro quiet splash

to:
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=dd4400ac-7855-4d5b-afc2-36ffdc7ccaf2 ro quiet

note:  Just remove the splash

>> You should install Ubuntu using the Alternate CD 

This seems to be necessary.  (does the live cd have a splash option that could be removed?)

>> and then install the Nvidia drivers and reconfigure the X-Server accordingly.

This is not "necessary" (at least on my system).  It is desirable, but not necessary, and does not seem to have anything to do with the problem.

Now how do you go about raising a bug regarding the splash option?

---

### Post by Partyboi2 on 2008-01-26
[https://bugs.launchpad.net/](https://bugs.launchpad.net/) to file a bug, check that there is not one already posted before posting one.:)

---

### Post by heathenminor on 2008-01-26
>>Your main cause of that problem is:- nvidia 8800 gtx

This is incorrect.

The problem appears to be related to the "splash" boot option not working with my hardware (possibly the nvidia 8800 gtx).

(32bit install works, 64bit install has problems)

>> You should install Ubuntu using the Alternate CD and then install the Nvidia drivers and reconfigure the X-Server accordingly.

This is unnecessary.
The live CD works fine once the "splash" option has been removed.  press F6 at menu and remove splash.

(kubuntu also works once "splash" has been removed).

---

