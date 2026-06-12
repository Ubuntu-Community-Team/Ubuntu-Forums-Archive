---
title: "reinstall lightdm X.org won't start"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by vortex-5 on 2011-10-14
Edit: The title should probably say "lightdm won't start after apt-get purge gdm"

I'm having a problem the upgrade to 11.10 went successfully I decided to remove gdm as a result with

apt-get purge gdm

unfortunately after I've done so lightdm no longer loaded properly can someone figure out what's going on

/var/log/x-1.log

[FONT="Courier New"]
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Oct 14 10:03:14 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) open /dev/fb0: No such file or directory
(EE) CHROME(0): Unknown Card-Ids (3344|1462|2590), Chipset: VM800/P4M800Pro/VN800/CN700; please report to [email]openchrome-users@openchrome.org[/email]
(EE) [drm] Could not set DRM device bus ID.
(EE) CHROME(0): [dri] DRIScreenInit failed.  Disabling DRI.
Freed 12587008 (pool 1)
 ddxSigGiveUp: Closing log

[/FONT]


/var/log/lightdm.log
[FONT="Courier New"]
[+0.51s] DEBUG: Releasing VT 7
[+0.51s] DEBUG: Display server stopped
[+0.51s] DEBUG: Display stopped
[+0.51s] DEBUG: Stopping X local seat, failed to start a display
[+0.51s] DEBUG: Stopping seat
[+0.51s] DEBUG: Seat stopped
[+0.51s] DEBUG: Stopping lightdm, required seat has stopped
[+0.51s] DEBUG: Stopping display manager
[+0.51s] DEBUG: Display manager stopped
[+0.51s] DEBUG: Stopping Light Display Manager
[/FONT]



also sudo apt-get install gdm (install back gdm that was removed) doesn't fix the issue.

Maybe GDM removed more than it installs back?

---

### Post by mohansathish on 2011-10-14
I hope you have to follow [http://ubuntuforums.org/showpost.php?p=11342361&postcount=6](http://ubuntuforums.org/showpost.php?p=11342361&postcount=6) and your issue will get solved.
If it is solved, then kindly mark the thread as closed :)



------
Mark the posts as solved once you got it. Help the team
Click me: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by vortex-5 on 2011-10-14
Ok partially fixed

I found out that there was a warning during install it said 

WARNING /var/lib/gdm is not accessable by the current user during install


I did a "sudo chown gdm:gdm /var/lib/gdm" and that seems to have fixed gdm 

But I still for the life of me can't figure out how to get lightdm to work. Lightdm worked before I purged GDM now it won't boot up still.

Does upstart start both gdm and lightdm or just lightdm?


I.E. with X GDM and Light stopped can I just run 

sudo service lightdm start?

in order to start lightdm?

Doing the same thing to lightdm seems to solve loading on light DM as well
also make sure you clear the conf files from /etc/lightdm


There are still issues with the themes being missing and also how lightdm disconnects clients after login but I left that for another topic this is solved.

---

### Post by marty331 on 2013-03-22
I resolved the issue of not being able to log in on lightdm by installing [COLOR=#333333][FONT=Ubuntu Mono]lightdm-gtk-greeter.[/FONT][/COLOR]

---

### Post by Toz on 2013-03-22
This thread is more than one year old. Thread closed.

---

