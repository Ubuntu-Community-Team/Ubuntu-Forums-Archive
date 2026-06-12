---
title: "System hang after upgrade."
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by inkrypted on 2011-10-14
I was wondering if anyone else had this happen after upgrading from 11.0 to 11.10. During boot the system hangs right after the line "starting Timidity++ ALSA Midi emulation...OK" I found a few references to Timidity but not quite sure that's the problem since it said OK. By the way I am running Kubuntu 64 Bit.

---

### Post by soldave on 2011-10-14
Having the exact same issue after trying to update from 11.04 using the system update software within Ubuntu.

---

### Post by ankh0r on 2011-10-15
Same here.

---

### Post by madjr on 2011-10-15
issue is worth reporting and getting a fix for it:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

---

### Post by cool_s on 2011-10-17
Is there any news on this issue?
Facing the same problem here 0.o

---

### Post by c69 on 2011-10-17
Same here.

---

### Post by andy53981 on 2011-10-17
Same problem and starting to get concerned about this.:(

---

### Post by madjr on 2011-10-17
A few friends have also had their systems un able to boot...

had to spend lots of time trying to rescue their systems

Am trying to grab devs attention about the risks of upgrading ubuntu and possible solutions to the problem:

[https://bugs.launchpad.net/ayatana-design/+bug/876146](https://bugs.launchpad.net/ayatana-design/+bug/876146)

please add yourself to the bug and possibly add your experience, thanks

---

### Post by soldave on 2011-10-17
I got around it by doing a clean install of Ubuntu instead of an upgrade.  After doing that, no hanging.

---

### Post by niwics on 2011-10-18
I had exactly the same problem. The trouble was not with Timidity, but right after that - it was problem with display manager gdm.
I booted to Ubuntu in recovery mode (and with old kernel - 2.6.31-22-generic) and run the program for selecting display manager:
```
sudo dpkg-reconfigure gdm
```
There I selected lightdm instead of gdm.

---

### Post by inkrypted on 2011-10-19
Mine turned out to be a video driver issue but unable to resolve it I had to do a clean install. Then running into alot more trouble that forced me to try Unity. After that I tried Gnome shell 3.2. I finally decided to migrate to openSuse using KDE. I believe I will be much happier here.

---

### Post by Leed on 2011-10-25
Still got the problem here, it is highly annoying. 

I guess it has to do with two things:

1. Async Boot procedure... upon restarting several times I eventually get to the desktop

2. Graphics driver. I started getting the problem after trying out the ATI restricted driver and then removing it again



You can also log in using alt+f2 and then launch the Desktop with the command "startx". But this will mess up all your Desktop settings, also not a good solution.

---

### Post by fermin on 2012-01-03
I have the same problem but not exactly after upgrading. I did a clean install of Ubuntu 11.10 on my old Pentium 4 machine and everything went smoothly until a few days ago when it started hanging at startup right at the "Starting TiMidity++ ALSA midi emulation" message and I remembered I had just installed that last time before the restart, so I figure it has something to do with that. I was trying to make the GNU Solfege program to run correctly and I found elsewhere that it needed timidity so I installed it. I'm not sure but I think it might be the reason my system broke, since it keeps hanging at that point of boot. I tried using the "boot repair" program from a Live CD session but it did not fix my problem, although I am now able to enter a "recovery session" now, which helped me go into a root terminal and reconfigure gdm, which I was using, and choose lightdm instead, as suggested in some prior post, but this did not fix my problem either. Any help would be highly appreciated since I really don't want to do a clean install again since I've put up a lot of time configuring and customizing this system :S

---

### Post by fermin on 2012-01-03
Foks I magically solved my problem :p I just went into the recovery session, mounted the filesystems, selected "repair broken packages", went into root terminal session, made some 

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade

resume normal boot and automagically recovered access to the user selection screen with gdm. I don't know what exactly fixed it but it did and I'm happy for it, though it would be instructive to know what precisely was the problem. Hope it might help somebody else.

EDIT: When I rebooted the problem persisted, that is, the above only worked once at resuming boot but then it failed. Nonetheless I went into recovery mode again and uninstalled timidity, that is

sudo apt-get purge timidity

which also uninstalled gnu-solfege-oss and some other related packages. Now it boots correctly, so in my case the problem DOES seem to have been related to timidity and that "TiMidity++" message.

EDIT2: The problem is NOT resolved, it is intermittent. Sometimes it boots and sometimes it doesn't. Any ideas?

---

### Post by b3d on 2012-01-11
> **niwics said:**
> I had exactly the same problem. The trouble was not with Timidity, but right after that - it was problem with display manager gdm.
I booted to Ubuntu in recovery mode (and with old kernel - 2.6.31-22-generic) and run the program for selecting display manager:
```
sudo dpkg-reconfigure gdm
```
There I selected lightdm instead of gdm.

Thank you.  This worked for me.  Actually, lightdm was selected for me, and I changed it to gdm and it worked.  So, I guess the point is to try both.  Also the gist of this thread is that the problem is NOT Timidity++.  That is just the last message before the display manager is supposed to launch.  If you look at the message, it says that Timidity started OK.  It's the *next* thing in the boot sequence, which is, apparently, the display manager.

BTW, I did not need recovery mode, I just did ctrl-alt-F1 to get to a terminal and entered the command.  Then rebooted.

Thanks!

---

### Post by dfv78 on 2012-06-30
Just as a reference, I had the same problem. The reason for my problem was that I had ran out of space in my hard drive and my PC would hang in the exact same place.

I resolved it by starting up in recovery mode and selecting the 'clean' option to free some space.

---

