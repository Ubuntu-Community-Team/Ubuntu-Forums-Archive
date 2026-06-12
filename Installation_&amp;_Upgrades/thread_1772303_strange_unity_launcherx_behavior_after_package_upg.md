---
title: "strange unity launcher/x behavior after package upgrades"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by ElmervG on 2011-05-31
Hi,

I've upgraded to Ubuntu 11.04 some weeks ago and after some minor tweaking everything has been working fine. But all of a sudden, it seems after some package upgrades, I'm experiencing strange behavior:

[LIST]
[*]The first thing I noticed is that after reboot the default application that should be kept in the Unity Launcher have all disappeared.
[*]The unity launcher doesn't hide itself anymore.
[*]The unity launcher does not react to changes I make via the 'System Settings'->'compizConfig settings manager'->'Ubuntu unity plugin' menu (icon sizes in launcher,  hiding method, etc.). Even after logout/login or reboot the changes aren't applied, although the corresponding settings in the configuration menus remain changed.
[*]One application that used to work as a charm started giving the following error on startup:
[/LIST]
[INDENT][INDENT]The program 'VESTA' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
(Details: serial 489 error_code 3 request_code 138 minor_code 4)

[/INDENT][/INDENT]Since yesterday everything was still working properly and today I get this strange behavior, it seems that something must have changed in between.  The only changes on the system in the last 24 hours are the upgrades of the following packages:[INDENT]     chromium-browser
    xserver-xorg-core
    xserver-common
    firefox-globalmenu
    software-center
    gnome-nettool
    firefox
    chromium-browser-l10n
    chromium-codecs-ffmpeg
    xserver-xorg-dev
    phonon-backend-gstreamer
    chromium-browser-inspector
[/INDENT]I would expect that only the xserver-* packages could be the culprit so I reverted them to their previous versions. But no luck, the strange behavior is still there. I reinstalled the unity package as well to be sure, but again no changes.

I can't find anything out of the ordinary in any of the log files and am at a loss as were to start looking for a cause and a solution.

Any help is greatly appreciated.

Kind regards,

Elmer

---

### Post by ElmervG on 2011-06-01
Ha! 

"It came to me in a dream." ;)

After a good night's sleep I found the problem. It seems that my X configuration was overwritten, probably by the xserver-* packages upgrades. Due to this change the wrong drivers for my NVIDIA card were used, causing OpenGL not to function, even after reverting to the previous versions of the packages. Because OpenGL wasn't working gdm or compiz (I guess) decided to start unity2d instead of unity, without any notification. 

I reinstalled the correct NVIDIA drivers and everything is back to normal.

Thanks to those who read my post and lost more than a second doing so. :D

Elmer

---

