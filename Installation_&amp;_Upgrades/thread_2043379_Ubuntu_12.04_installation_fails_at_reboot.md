---
title: "Ubuntu 12.04 installation fails at reboot"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by Quazze on 2012-08-16
Hello everyone

After resizing my Ubuntu partition, Ubuntu got very slow and so I decided to reinstall Ubuntu 12.04 over the existing Ubuntu installation. This went very quickly (something like 10 mins?). Then the laptop has to be rebooted to finish the installation, so it comes to the screen where I have to log in. But after I log in, the screen just shows black and white rectangles; and some weird colors when I click with the mouse. Sometimes it seems like I can see some of the menu items very large I might have clicked on without being able to see it behind the black and white...

I installed Ubuntu 12.04 from a Live USB disk.

Can anyone help? Otherwise I'm going have to try to install an earlier version and upgrade, but that is going to take a whole lot of time...

Thanks in advance
cheers
Lukas

---

### Post by cbanakis on 2012-08-16
If possible, it might be worth re-installing using a cd.

I have had random problems before when installing off a flash drive, and using a cd fixed it.

Not sure why that would help, but it has worked for me.

---

### Post by Quazze on 2012-08-16
can't use a cd-rom, because my cd-reader doesn't work...

There's actually also another problem. When I now turn on my laptop without the Live USB diks I get an error:
Error: Unknown filesystem
grub rescue >

but I don't really know what to do in this grub rescue console.
Only when I start up with the Live USB disk I get the normal GRUB start up menu

---

### Post by Jt00 on 2012-08-16
Try reinstalling from the USB stick. If that doesn't work, you may have to buy a CD drive that plugs in the USB port and try the liveCD.
What other OS's do you have on the computer (if any)? You may be able to install from the hard drive. See oldfred's 2nd post on my thread [here]("http://ubuntuforums.org/showthread.php?t=2042085"), where he gives lots of info about doing that.

---

### Post by cbanakis on 2012-08-16
I know exactly what happened.

Format and rebuild the flash drive.

Re-install, and make sure no aspect of Ubuntu is being installed on the flash drive.

Installing off a cd should work too.

The problem, is that Ubuntu installed the boot-loader, and who knows what else on your flash drive, instead of your hard drive.

If you used "advanced" install, that could explain it, but I have seen it happen on automatic.

The problem usually occurs if you have more than 1 hard drive in your system, but I have seen it happen with just 1 hard drive when using a flash drive for install.

Hope that helps.

> **Quazze said:**
> can't use a cd-rom, because my cd-reader doesn't work...

There's actually also another problem. When I now turn on my laptop without the Live USB diks I get an error:
Error: Unknown filesystem
grub rescue >

but I don't really know what to do in this grub rescue console.
Only when I start up with the Live USB disk I get the normal GRUB start up menu

---

### Post by Quazze on 2012-08-18
thanks for the answers. the Live Ubuntu 12.04 didn't work, so I just did one I knew worked: Ubuntu 11.04. So now I just need to upgrade two times...

---

