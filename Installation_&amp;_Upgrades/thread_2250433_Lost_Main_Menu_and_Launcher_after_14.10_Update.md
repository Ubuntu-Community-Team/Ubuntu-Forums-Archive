---
title: "Lost Main Menu and Launcher after 14.10 Update"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by rob102 on 2014-10-28
Happy Tuesday Oct 28th,

I recently was prompted to update Ubuntu 14.x to 14.10, so I did. After the update I rebooted and logged in. After the login, no menu or launcher showed.

I have tried the following:
[LIST]
[*]uninstall and reinstall fglrx drivers
[LIST]
[*]apt-get remove fglrx
[*]apt-get remove fglrx-core
[*]reboot
[*]apt-get install fglrx
[/LIST]

[*]install compizconfig-settings-manager
[LIST]
[*]ran ccms but received error
[*]AttributeError: 'NoneType' Object has no attribute 'get_default_screen'
[/LIST]

[*]installed KDE - apt-get install kubuntu-desktop
[*]Desktop login follows with System program problem detected | Cancel | Report problem...
[LIST]
[*]No additional information is provided
[/LIST]
[/LIST]

I'm not sure what would be the next step to try here. Any help or suggestions would be appreciated.

---

### Post by jbinpg on 2014-10-30
> **rob102 said:**
> Happy Tuesday Oct 28th,

I recently was prompted to update Ubuntu 14.x to 14.10, so I did. After the update I rebooted and logged in. After the login, no menu or launcher showed.

I have tried the following:
[LIST]
[*]uninstall and reinstall fglrx drivers
[LIST]
[*]apt-get remove fglrx
[*]apt-get remove fglrx-core
[*]reboot
[*]apt-get install fglrx
[/LIST]

[*]install compizconfig-settings-manager
[LIST]
[*]ran ccms but received error
[*]AttributeError: 'NoneType' Object has no attribute 'get_default_screen'
[/LIST]

[*]installed KDE - apt-get install kubuntu-desktop
[*]Desktop login follows with System program problem detected | Cancel | Report problem...
[LIST]
[*]No additional information is provided
[/LIST]
[/LIST]

I'm not sure what would be the next step to try here. Any help or suggestions would be appreciated.
=============================

Same thing happened to me on two machines. I think what fixed it was when I went and renamed my home directory .cache file to .cache.org and my .config file to .config.org and rebooted. All good after that, albeit without my previous customizations.  I bet if I had backed up my /home and formatted it during install that everything would have been fine. Then I could have reloaded from the backup.

However, for me, this problem is overshadowed by the fact that you cannot install wine if you are running fglrx due to a collision of opencl files. Can't believe that a dependency hell this major got by the devs before release.   

jbinpg

---

### Post by rob102 on 2014-11-05
Thanks for the reply jbinpg. I know enough to be dangerous in the terminal, so I'm having trouble finding the .cache and .config files.

I'm in what I believe to be the user home directory, but the dir command doesn't show either file. How do I locate these files so that I can rename them?

-Rob

---

### Post by filter4ever on 2014-12-13
What I finally did (after so far as a WIPE and RE-INSTALL from scratch) is rename them to /[me]/.config.org, and /home/[me]/.cache.org respectively.  I'm not sure which file/folder, I went as far as to 'erase and re-install' and take the risk of losing all files in '/home' (I use encrypted home).  This happened to me after turning my computer off the night of 12/10/14 and on 12/11/14.  After checking the 'apt-get' logs, there were updates for Nvidia-304:amd36, xserver-xorg:amd386, and xserver-xorg-common:x386.

How can I report this to the developers as a bug, along with the LOCATION?  I clicked "submit bug report" when it crashed but I was messing with other things that were missing (lightdm and Ubuntu-desktop for example), and found out they were not the problem?  The problem is the Unity /home/.config and /home/.cache config folders (or a file in them).  I'm a newbie at Ubuntu, and haven't ever used a GUI Linux (just Command Line on a POS 486 I found in the trash in 1998, as a router/firewall/server when I first got broadband).

I have concluded that the problem is in the existing /home/[me]/.config and /[me]/home/.cache folders.
 I loaded Ubuntu after shutting it down the night before.  Would get to logon, it would "freeze", no desktop icons. CTRL-ALT-DEL showed processes running, but no desktop, so I knew it wasn't a CRASH.  I tried everything, reloading Nvidia drivers, re-installing Ubuntu-desktop, unity, lightdm.  Tried everything, including taking the CD and wiping all partitions except /home, which was encrypted (big risk), and unity still wasn't working.  The ./compiz remove/reinstall/select "unity" plugin did not work either. Reinstalled from LiveCd, finally... fresh install, selected EXACT SAME size, mounting points, username, and password (important).  My /home came back (relief), but still... no desktop.  I tried 'Guest', and it worked... My troubleshooting instincts narrowed this down to the /home/[me] folder, as the rest were wiped.  After reading about another user with the same problem, I renamed the existing /home/[me]/.config and /[me]/home/.cache to /[me]/.config.org, and /home/[me]/.cache.org respectively.


I have 2 NVidia cards - one is a BFG 7800OC - FACTORY OVERCLOCKED - It just freezes when you try to start Ubuntu with X.Org driver in High Graphics mode (unity or setup).  I also have a GeForce 6600, luckily takes the same drivers, I found in a pile of junk (missing heatsink - replaced).  Every time I have to "reinstall" or it goes back to the X.Org driver.  If you have one of these, install "NVidia-304" (apt-get install NVidia-304), will work with proprietary driver ONLY.

---

### Post by rob102 on 2014-12-24
I finally gave up and just did a new installation of the latest kubuntu 14.10 with a format of the same partition. I'm back up and running and so far the kubuntu is looking pretty nice and intuitive. Hopefully everything goes well when the next update comes along.
Thanks for all of the responses from everyone.
-Rob

---

