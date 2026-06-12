---
title: "Installation on Dell D620"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by jackfurlong on 2018-09-16
System is a Dell D620

The system boots from a Ubuntu 18 USB just fine, and runs flawlessly. 
So I installed to the hard drive, and rebooted. 
Grub loads and lets me select Ubuntu; the "loading" screen appears, then locks up with mouse pointer displayed.
I rebooted via Ubuntu USB, and did a repair of the HD install.
Booted from HD again and got the same lockup as before.


  I'd appreciate any suggestions, please.

---

### Post by oldfred on 2018-09-17
How much RAM?
What video card/chip?

Since older system, you may be better off with one of the lightweight flavors.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie

---

### Post by jackfurlong on 2018-09-17
I'll give Lubuntu a shot, and see if that works.
Still puzzles me why Ubuntu 18 works from a "live usb drive", and not when installed to hard disk.

---

### Post by GlenH on 2018-09-25
I'm having the same problem on a Dell D620.  Boots fine from 18.04.1 LTS USB stick, but hangs on boot after installation.  Also hung at the same place after upgrade from 16.04 LTS, so I saved my home directory and did a fresh install and get the same hang

My system configuration:
4GB RAM
Intel Core 2 T7400
Intel 945GM Graphics

Back in July, there were reports of issues with kernel 4.15.0-24 and later due to a lack of entropy sources for getrandom().  I'm not sure if that's the problem I'm having, or something else.

Edit: 
I pulled 18.04 LTS (kernel 4.15.0-20) from old-releases and tried installing that. Same issue, so it's not lack of entropy; it's an older bug. 

Booting into recovery mode and examing the boot log shows an ACPI message about a firmware bug that causes duplicate video bus devices for the same controller and suggests "video.allow_duplicates=1"

Enabling networking in recovery mode hangs.

Heading to work... will do more troubleshooting later.

---

### Post by GlenH on 2018-10-01
Further troubleshooting... If I boot into recovery mode and choose Resume, 18.04 LTS boots.  Trying again with 18.04.1 LTS.  Both work from USB boot using the ISO; both crash after installation while booting from the hard disk, shortly after the mouse appears on the screen.

---

### Post by GlenH on 2018-10-02
Resolved on my Dell D620.

Easiest fix for me:
In Grub, choose "Advanced options for Ubuntu", then boot the latest "Recovery Mode" kernel.
At the Recovery Mode menu, choose Resume. Ubuntu should boot more or less normally.
Log in.
Open a terminal window with Ctrl-Alt-T.
Enter the following: "sudo pico /etc/gdm3/custom.conf"
Uncomment (remove the hash symbol) from the line "#WaylandEnable=false"
Save your changes and exit pico.
Reboot.

There is a bug in the GNOME3 mutter window manager that affects older Intel graphics chipsets, particularly the GMA900 and GMA950 families.  The bug is fixed in mutter 3.28.4, but that hasn't made it to Ubuntu 18.04.x LTS, so the above workaround disables the offending software.  mutter 3.30 is in Ubuntu 18.10, and the bug is apparently fixed there.

See the discussion at [https://bugs.launchpad.net/gnome-shell/+bug/1727356](https://bugs.launchpad.net/gnome-shell/+bug/1727356)

---

### Post by jessieinnewy51 on 2018-10-03
Thanks for the Resolution Information.
 I have had a similar problem and it was resolved with the Information provided above.
 In my case I had the Problem with UBUNTU Version 18.04 after an upgrade from Version 17.10 and then I tried a complete New Installation of 18.04 which would not boot through to the Login Screen.
 In my Case it happened on a Desktop With the Graphics Card INTEL G33 in conjunction with Intel Dual Core, CPU E 5400,2.7Ghz,Motherboard Elite Group G31T-MT 
[LEFT]
Easiest fix for me:
In Grub, choose "Advanced options for Ubuntu", then boot the latest "Recovery Mode" kernel. (4.15.0.29)
At the Recovery Mode menu, choose Resume. Ubuntu should boot more or less normally.
Log in.
Open a terminal window with Ctrl-Alt-T.
Enter the following: "sudo pico /etc/gdm3/custom.conf" 
 (Then Scroll Down, Down Arrow Key)
Uncomment (remove the hash symbol) from the line "#WaylandEnable=false" (Delete #)
Save your changes and exit pico. (CTRL "X")

Reboot.

If you want to re arrange the GRUB their is an Excellent GRUB Customizer within LINUX VOYAGER 18.04 that works well once you become familiar with it and remember to Save to the Master Boot Record.
Linux Mint 19 Xfce is extremely Slow to get to the Login Page on my Desktop but it looks like it has a Programming problem also.

Hopefully UBUNTU 18.10 will correct a few of these newly created software problems.
I nearly gave up on UBUNTU 18.04 and stuck to VOYAGER 18.04 but now I am Dual Booting with VOYAGER 18.04, MINT 19, UBUNTU 18.04
all are now working well.
Thanks for the FORUM HELP.
[/LEFT]

---

