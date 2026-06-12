---
title: "Ubuntu 18.04 / Windows 10 dual boot"
date: 2020-03-22
forum: Installation &amp; Upgrades
---

### Post by kathrync on 2020-03-22
Hi all,

I am trying to set up our Windows 10 desktop computer to dual boot Ubuntu 18.04 so that I can use it to work at home. The desktop has two M5 hard drives.  One already had Windows 10 installed.  I have installed Ubuntu on the other (mounted it on Ubuntu live CD, all system files are in place), but I put the boot loader in the efi partition that Windows was already using, which is on the other disc.

When I boot, it goes into Grub, and I can see options for both Ubuntu and Windows.  Windows boots fine if I select the appropriate option. 

When I select Ubuntu, it initially looks ok - I get the splash screen with the Ubuntu logo and the 5 white dots underneath.  However, the boot proceeds no further - the screen goes black, the monitor indicates it is not getting a signal and the fan stops, but the power light remains on.  I have to hard reboot using the button on the case. 

I have tried running boot repair from the Ubuntu live USB.  More boot options appeared in the Grub menu, however all the Ubuntu options exhibit the same symptoms as described above.  The pastebin is here: [http://paste.ubuntu.com/p/7RmmWP735r/](http://paste.ubuntu.com/p/7RmmWP735r/)

I suspect my issues are because the boot loader and the rest of the OS are on different drives.  Can anyone help me to sort this out?  Ideally I would like to be able to access Ubuntu and Windows from the Grub menu.  I haven't done anything with the Ubuntu installation yet, so I am happy to re-install if this would help - my partner would prefer I didn't try to re-install Windows if at all possible.

Thanks!

---

### Post by oldfred on 2020-03-22
Different drives is not an issue.

Is Windows fast start up off?
It does not look like you have installed nVidia driver. You show nouveau.

From grub menu can you boot second entry recovery mode. That has nomodeset as a default and then you should be able to install the nVidia driver.

What brand/model system?

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You can also use nomodeset temporarily with normal boot entry:
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by kathrync on 2020-03-22
Ah, yes - the symptoms fit and this is my partner's gaming machine (I want to use it because my work vpn is overloaded so I am having trouble getting to our cluster) so it probably does need the nVidia driver. I'll give that a go and report back!

---

### Post by kathrync on 2020-03-22
Perfect, installing the recommended nVidia driver has done the trick!  Thanks!

Thanks also for the tip about Windows turning fast boot back on when it updates - I had turned it off, but it's useful to be aware of that!

---

### Post by oldfred on 2020-03-22
Glad you got it working.

You can change to solved. 
Also post brand/model so others will know.

---

### Post by kathrync on 2020-03-23
Tbh, this is the gaming machine that my partner built and I don't have a brand/model as components came from all over - however the important part for this thread is probably the graphics card: Palit GeForce GTX 1060 Dual 6144MB GDDR5 PCI-Express which wanted nvidia-driver-435

---

