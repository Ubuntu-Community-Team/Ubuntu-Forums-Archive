---
title: "Severe Problems in Installing Ubuntu at an old AMD 475 MHz system"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by Mian Mansoor on 2007-07-30
Hi, I am facing severe problems while installing 'ubuntu-7.04-desktop-i386'. I will explain the problem in detail, so please help.
I must tell that i have an old AMD 475MHz system which is running Windows 2000 without any problem. I have successfully downloaded and burned the ISO on a CD.

At the beginning, when i boot from the CD, it gives me a menu whose first option is "Run or install ubuntu". Selecting this option starts the procedure BUT the following error message appears on console:

 [    0.0000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
   Loading, Please wait ...

and then a lot of things are loaded / checked ...                              with the status [OK].

During the process, the following errors also appear on console which i get through pressing <Ctrl><Alt>F1

[    499.636636] Sis630_smbs 0000:00:01.0: SIS630 Computer bus not detected, module not inserted

* Starting Powernowd...
/etc/rc2.d/S20 Powernowd: 156: cannot create /sys/device/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
* CPU frequency scaling not supported

Then after some time a GUI appears with the following Error Message in a Window:

There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timout expired, or the network cnnection was broken.
GNOME will still try to restart the Settings Daemon next time you log on.


Then nothing happens further and the screen stays there. On pressing <Ctrl><Alt>F2, I get a console stating:
To run a command as administrator (user "root"), use "sudo <command>". See "man sudo_root" for details. _


Please help me as i have just given up!!!

---

### Post by Pumalite on 2007-07-30
Try Alternate CD ( Text Mode ). Check iso with md5sum, burn at 4x or less, check CD for corruption, then install.

---

### Post by Mian Mansoor on 2007-07-30
I have checked my CD for errors and it is fine.
What is meant by trying Alternate CD ( Text Mode )  and Checking iso with md5sum? i am very new in the field. Please explain!

---

### Post by poohbear1616 on 2007-07-30
> [ 0.0000000] ACPI: BIOS age (1997) fails cutoff (2000)

See if you can find an update to your bios. It's not a hard process to flash
the bios.

Also you did not mention how much ram is in the system.

---

### Post by SixedUp on 2007-07-30
Most of your errors sound like they are related to the age of your machine; it simply doesn't have many of the features that a modern distribution like Ubuntu expects to see and cope with. This is what is causing many of your "error messages", which in practice are really just warnings.

I doubt that you will find an upgrade to your BIOS that will change any of this.  Your machine is just very old.  However, that will not prevent you running Ubuntu, although I suspect the full Ubuntu 7.04 will run very slowly. You might actually be better off with Xubuntu, which is specifically tailored for older / slower machines, with less memory. 

However, if you want to try Ubuntu, I recommend that you use the "Alternate CD".  This is an installation CD for Ubuntu which doesn't have a "live environment" on it, but instead can only do installs. The advantage is that it can cope with more unusual configurations - which is what you have.  Find the ISO in the same place that you found your existing image, download it, check the checksum, and burn it to CD. Then use that to do a "text mode" install.  This is where the installer asks you questions using a terminal interface, rather than a graphical one.  The installed system will still be a graphical one.

Incidentally, I have also received the error about the Gnome settings daemon when installing on older hardware, and have managed to avoid it by installing from the Alternate CD, so I think that's the place to start.

Good luck.

---

### Post by High_Yield on 2007-12-11
I'm having similar problems with an old AMD system... see [http://ubuntuforums.org/showthread.php?t=637924](http://ubuntuforums.org/showthread.php?t=637924)

I get an ACPI error, but not exactly the same.  From there things sound almost exact with device failure errors etc...

This is my first experience with linux so I cannot "tinker" like I can with Windows.  I'll try XUbuntu or an older version - people seem to like Feisty Fawn but this one, Gutsy, seems to have been perhaps released early.

---

### Post by Pumalite on 2007-12-11
You could try:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Hope your video doesn't turn out to be a problem. Try first, then we'll see.

---

