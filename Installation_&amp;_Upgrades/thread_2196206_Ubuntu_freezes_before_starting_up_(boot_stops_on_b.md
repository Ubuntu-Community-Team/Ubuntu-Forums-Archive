---
title: "Ubuntu freezes before starting up (boot stops on black screen)"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by Raphael_Rocha_da_Silva on 2013-12-28
Hello! 

I've spent the entire morning trying to solve this: when Ubuntu 12.04 should boot, instead, it goes to a black screen, after showing Ubuntu logo.

(I know there's a lot of questions about it, but I feel like it would be OK to post this explaning my particular case, since I've already spent hours searching for a suitable help)

Here is how it started: I was using Ubuntu normaly when it froze. When I restarted, I couldn't boot anymore. 

I have tried things like: 

- Using 'nomodeset' parameter (as said at askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it). The difference is that, on this mode, it freezes on the purple screen before it shows Ubuntu logo.

- Using "acpi=off" parameter.

- Using another monitor, as suggested at some forums.

- Turning the brightness up. That's definetly not the problem.

- Reinstalling the graphics drivers (as taught at [http://askubuntu.com/questions/87090/how-do-i-install-drivers-for-an-intel-hd-graphics](http://askubuntu.com/questions/87090/how-do-i-install-drivers-for-an-intel-hd-graphics)) 

When I try to boot from the USB stick, the same thing happens. But here is something curious: when I press 'c' at the menu (it goes to a terminal with a "grub>"), if I just enter the command "exit", it works! So, by doing this, I can use the Ubuntu via the USB drive perfectly.
The same thing doesn't work at the normal boot, though. 

I haven't tried to reinstall Ubuntu, first because I don't know if this would fix the problem, and second because I have some programs installed on Ubuntu whitch I don't want to remove (as effect of the reinstallation).

I'm using a laptop computer with Intel HD Graphics Core i5 - I'm not sure what other information would be relevant. 

Thanks a lot for your help!

---

### Post by Raphael_Rocha_da_Silva on 2013-12-29
By the way, I am not sure if I installed the graphics drivers correctly. Here is some information:

> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)


00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1702
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e080 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915




OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 9.1.4
OpenGL shading language version string: 1.20




---

### Post by grahammechanical on 2013-12-29
There is something that you need to understand. If we follow the instructions in that AskUbuntu link about installing Graphic video drivers we install the very latest and most likely experimental or untested proprietary drivers. That may not necessarily be the best thing to do.

At the Grub menu we can select Recovery mode and that will get us to a menu with some options, such as Resume. That will load to a desktop without using a video driver. If the video driver is the problem then this will be a useful thing to be able to do.

If you manage to get to a working desktop you can use Additional Drivers to change video drivers. You may need to experiment with the choice of drivers.

You may also want to consider loading into an earlier Linux kernel (at the Grub menu) in an attempt to get around this.

Regards.

---

### Post by Raphael_Rocha_da_Silva on 2013-12-29
Hello, _grahammechanical_, thanks for your answer! 

So, when I choose *Resume *at the recovery mode, it goes to a command mode (where I'm able to log in with my Ubuntu username and password). 
Is that what is supposed to happen?

---

### Post by eprochasson on 2013-12-30
I figured that installing nvidia-prime and setting nomodeset at startup does the trick.

And it took me a lot of time to do so, and I was lucky. Hope that can help. There are issues I didn't manage to tackle though, like being able to change the brightness of the screen, or use the hibernation. Apart from that, it's a kick-ass laptop, I put Ubuntu on the 16GB SSD, it seriously rocks.

---

### Post by Raphael_Rocha_da_Silva on 2013-12-30
Hello, _eprochasson_, thanks for taking your time! 

Below, I show the current settings for the boot. 
I did what you suggested: I installed **nvidia-prime** and then I replaced the "[FONT=courier new]quiet splash[/FONT]" with "[FONT=courier new]nomodeset[/FONT]". The error persists, though. It freezes on the black screen after showing Ubuntu logo.

[IMG]https://googledrive.com/host/0B2o4S8wMQH9BQWpOaVV1Y0paU0U/DSCN0263%20C%20boot%20settings.JPG[/IMG]

---

### Post by eprochasson on 2013-12-31
This is what I have in my /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Don't forget to run update-grub before restarting. 

Imho, it is still an issue with the screen brightness that can not be adjusted. (without nvidia-prime), if I plugged a screen it would work perfectly on the second screen.

I'll be honest, as I said I spent so much time looking into the issue without finding a solution, I've been lucky to find that nvidia-prime solved my problem, but I have absolutely no idea why. I don't dare upgrading anything or trying to fix the other problems (hibernation -- also, I can't use a secondary screen anymore, Skype doesn't work because of sound issues) because I'm too scared it will break it. I'm waiting for more power-user to buy that (kick ass) model to see solution arised :)

---

### Post by Raphael_Rocha_da_Silva on 2014-01-01
Too bad it did not work for me... 
It seems like there is no solution! 
Thanks anyway.

---

### Post by eprochasson on 2014-01-06
Actually, I seem to remember that I also used an internet connection during installation, in order to download the latest software. Maybe having a more recent kernel is also a part of the solution?

---

### Post by eprochasson on 2014-01-08
Ha, I'm performing more test, trying to get the sleep/hibernate thing to work.

I found out that if I enable CSM, the system boots ok, and even the hibernate works. However, the screen definition is crap (1024x768). 

The trick is, to enable/disable CSM in the BIOS, you first need to activate/deactivate Secure Boot THEN reboot, otherwise the option stays muted. Then you can activate CSM.

I'll try to see if I can get something better than what I have right now by tweaking the CSM option.

---

### Post by eprochasson on 2014-01-08
You might also want to check [http://ubuntuforums.org/showthread.php?t=2191840](http://ubuntuforums.org/showthread.php?t=2191840)

---

### Post by eprochasson on 2014-01-08
Oh, and I also found this bugreport [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1263015](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1263015) with a fix that works quite well for me.

---

