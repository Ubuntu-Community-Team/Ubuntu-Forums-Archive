---
title: "Ubuntu 16.04 problem getting out of the &quot;Ctrl-D&quot; cycle - Please Help!"
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by seanbw2 on 2016-06-16
I have had this issue before and the only solution then was to reinstall. If I have to reinstall, I will like to know what to do to avoid it happening again otherwise I am not learning.
I allowed Ubuntu to update and now I have a few more options when logging in. If I attempt to login, I get a maintenance problem error message that tells me to run "journalctl -xb" which i run and it gives me a long list of processes and stuff but I can't find any help there to identify what the issue is.
The system attempts to load the desktop because I can see the desktop scree and 16.04 and then it drops out to the maintenance shell and gives me these options which are run systemctl reboot, systemctl default or press ctrl-D  and irrespective of which option I go for, they all return me to the same menu options of - you guessed it systemctl reboot, systemctl default and Ctrl-D.
If I press enter I drop into root@nas but what do I run to get out of this loop? Even when I go for the enter option, all I get is a root@nas prompt but I have no network so I can't reinstall anything.
If I could just get network, then I can suppose reinstall the desktop but I am not sure if that will resolve anything because I can see the desktop.
I tried this option:

[COLOR=#333333][FONT=monospace]> Guys, try this. Worked for me.
Hold down shift while booting to access boot options menu
Select recovery console
Enable networking
Select Administrator Root terminal
# sudo apt-get update
# sudo apt-get install xserver-xorg-video-intel
Select Continue Normal boot.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Copied from: Bug #1575460 “Intel video driver not installed by default on Lub...” : Bugs : lubuntu-meta package : Ubuntu - <[/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460)[COLOR=#000000][FONT=&quot]>
and this:
[/FONT][/COLOR]> [COLOR=#333333][FONT=monospace]For Compaq Mini, you should press ESC key to access boot options instead of shift.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Then this PC has the broadcom wireless driver, so you must have done install with ethernet cable attached or you have no network to update and install the missing driver...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]otherwise the fix via recovery and install of intel drivers works[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Copied from: Bug #1575460 “Intel video driver not installed by default on Lub...” : Bugs : lubuntu-meta package : Ubuntu - <[/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460)[FONT=Segoe UI, Tahoma, sans-serif][COLOR=#000000]>[/COLOR][/FONT]
[FONT=Segoe UI, Tahoma, sans-serif][COLOR=#000000]but I can't get the pc to go into network mode at all so I am stuck.[/COLOR][/FONT]
[FONT=Segoe UI, Tahoma, sans-serif][COLOR=#000000]Can anybody help to at least get me into network  mode so I can at least try the apt-get update and install the xserver-org-video-Intel option to see if it works.[/COLOR][/FONT]
[FONT=Segoe UI, Tahoma, sans-serif][COLOR=#000000]Please![/COLOR][/FONT]

---

### Post by seanbw2 on 2016-06-16
I apologise for the lack of info. It is just getting so frustrating with this aspect that each time I run an update and I have more than one linux image, I just develop problems loading. It shouldn't be like that.
The pc is an HP Gen8 G1610T server with 16gb ram, 16tb hdd and 320gb system disk.

---

