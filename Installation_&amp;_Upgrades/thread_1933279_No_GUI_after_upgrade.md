---
title: "No GUI after upgrade"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by mab5 on 2012-02-29
The first thing I would like to say is that yes, I have searched for (literally) months for a solution to this problem. I know this a widespread problem and I should probably just do a clean install next time instead of just upgrading directly. 

So a couple of months ago I accidentally upgraded to Ubuntu 11.04 when I was installing updates with the program manager. I believe my current version was 10.04 at the time. After the upgrade my GUI completely disappeared because my Nvidia drivers stopped working and now I'm stuck in "terminal" mode. I've googled for months and months, I've tried uninstalling the drivers and reinstalling them, but so far nothing has worked. I'm not saying that those solutions didn't work, but I couldn't seem to get them to work for some reason. 

The computer in question is ancient, but it still ran Ubuntu perfectly fine and the hardware is still good (however old.) I seem to recall that I first installed Ubuntu on that computer via USB stick, but I've tried to do a clean install with both a CD and USB stick and the computer refuses to boot from them. The hard drive is hard to access without taking the computer completely apart as well. 

I guess what I'm trying to say is that I would rather fix the driver problem then do a complete reinstall. :P

I know that there have been many previous threads on this graphics driver problem, but I think I'm doing it wrong. I know some basic terminal commands, but I'm a noob and a bit of an idiot and would really appreciate your help with how to get the drivers working properly. It's worth mentioning that I just upgraded from 11.04 to 11.10 today because I somehow thought it might fix the problem, but it didn't. Again, I'm sorry that I'm repeating the same problem that's been asked many times, but I'm desperate and frustrated right now and would really, really appreciate your help. Thank you!

---

### Post by mastablasta on 2012-02-29
if you didn't disable (uninstall) the drivers before upgrade then you get terminal only. you now need to fully remove the drivers 
from: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nv_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nv_from_scratch)
 
>  
**Problem: Need to fully remove -nvidia and reinstall -nv from scratch**
 
A similar issue exists for -nvidia/-nv, for similar reasons. People don't run into it quite as much since -nv doesn't tap 3D functionalities as often, but it still happens. 
 
The nvidia kernel module is loading from the proprietary drivers, but x is trying to load xserver-xorg-video-nv. If you installed the binary drivers from nvidia.com to get into this situation you will want to run sudo nvidia-settings --uninstall and then install the binary drivers provided by ubuntu instead after you reboot. if thats not the case you can do a sudo apt-get install nvidia-graphics-drivers-185 and it will overwrite your xorg.conf with the needed one. 

 
even more info here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by mab5 on 2012-02-29
I tried removing all the old nvidia hardware and rebooting before reinstalling the linux nvidia driver, but now my computer won't start up. The boot up screen does look different, however. I can actually see the ubuntu logo, but the computer will just stop when all 5 of the white dots turn red and won't boot up completely anymore. Any suggestions?

---

### Post by yo_bhan on 2012-02-29
> **mab5 said:**
> I tried removing all the old nvidia hardware and rebooting before reinstalling the linux nvidia driver, but now my computer won't start up. The boot up screen does look different, however. I can actually see the ubuntu logo, but the computer will just stop when all 5 of the white dots turn red and won't boot up completely anymore. Any suggestions?
try boot from recovery mode, failsafeX graphic
and remove old driver. and restart.
install nvidia driver from tty, you should shutdown xserver.
```
sudo service gdm stop
```
and try install nvdia driver, I suggest download the latest driver from nvidia site

---

