---
title: "Lucid Lynx 10.04  fails to boot after upgrade or install: no video"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by rahuijts on 2010-05-08
Though I am not a very experienced Linux user, it was quite easy to turn my HP Compaq D530 desktop machine into a useful LAMP and SVN server with the Ubuntu 9.10 Server Edition. After upgrading to 10.04 it suddenly failed to boot, so I burned a 10.04 installation CD. The installation seems to run fine, ejects my CD and tells me to boot into my newly installed system. The first boot runs normally and I get a command-line interface in the right resolution (1680 x 1050). My server is running and I can access it through SSH.

But on the second and any following (re)boot, the system fails to load. After my HP splash screen it shortly shows a blinking cursor on a black screen. Then the screen goes completely black, my monitor starts searching for input and goes to standby. I use the power button to shut down.

Since this is the only operating system installed, the grub menu is not shown. Using the installation CD in rescue mode to run a shell with the hard drive mounted, I was able to edit /etc/default/grub and run update-grub. Now the grub menu is displayed on reboot and I can choose to boot Ubuntu. I had removed the "quiet" boot option so the boot progress information is shown in a low resolution, after that I get a command-line interface in the right resolution again, although now the login prompt starts halfway down the screen. This is no problem, for it will use the whole screen when, for instance, running "top". After rebooting again, the same boot progress is shown, but then the screen goes completely black again and the monitor falls asleep.

Running the CD in rescue mode every time is cumbersome, so I tried to install Damn Small Linux (DSL) onto my USB pendrive (256 MB). Although I can choose to boot from USB on this machine, I did not succeed in running DSL. The system will boot from hard disk anyway, start grub, show the boot progress information in low resolution and go black. At this point I know that Ubuntu did not complete loading, because apart from having no display I cannot access the system through SSH from another machine either. If, however, I then unplug the USB, it suddenly shows me a blinking cursor. The system is up, the SSH daemon is running and the blinking cursor appears to be a login prompt. If I try this again and unplug the USB pendrive directly after the boot progress information, the screen even shows the expected welcome message "Ubuntu 10.04 LTS compaq tty1" and a proper login prompt "compaq login:". Apache does not seem to be running though.

What causes my screen to go black and how can I fix this? I would not mind to run the system in a failsafe, low resolution, if that prevents the boot from failing, because I will access the machine remotely most of the time anyway. Is my hardware incompatible, broken or just playing with me? Any tips on how to solve this would be most welcome!

Attached are the output of lspci and lshw for my machine.

---

### Post by rahuijts on 2010-05-08
Here is the output of dmesg as well. I hope someone can help me with this.

---

### Post by Catharsis on 2010-05-08
I have no experience with the Server Edition, so please take my advice with a grain of salt.

There's a known problem with Lucid and Intel 8xx chips. From your lspci, it looks like you might have one. See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

You can also try booting with "nomodeset" in grub instead of "i915.modeset=1".

There's also some talk about blinking cursors during boot here:
[http://ubuntuforums.org/showpost.php?p=9235797&postcount=16](http://ubuntuforums.org/showpost.php?p=9235797&postcount=16)

---

### Post by rahuijts on 2010-05-08
Thanks Catharsis!

The page on the Intel 8xx chips freezes was very useful. Using "i915.modeset=0" (and thereby turning KMS off) as a boot parameter helped me to boot normally again, although the resolution fell all the way back to 640x480.

The post in your second link did the trick even better, the boot has a tiny tiny delay but gives me a beautiful 1680x1050 resolution. I do not quite understand how it works, but it works.

You saved me!

---

