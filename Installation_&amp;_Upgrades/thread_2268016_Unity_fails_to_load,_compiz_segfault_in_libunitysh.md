---
title: "Unity fails to load, compiz segfault in libunityshell.so, Shutter svg messag at login"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by l-contactarsergio on 2015-03-05
Hi. This is my first post here.):P
Turns out that after a recent update my Ubuntu 14.04.2 LTS the Unity desktop disappeared at login. I've tried all possible solutions, like completely purging and reinstalling unity-desktop along with compiz-manager, resetting compiz to default, clearing programs cache, creating a new user in order to try login into a new environment, etc. I've reinstalled ligtdm, configured and reinstalled ccsm with Unity Plugin enabled, tried dconf reset. Nothing worked for me. At the moment I'm using Gnome (Metacity) as I had no success loading Unity again. Besides, I've tried to completely remove/reinstall fglrx video drivers which didn't worked for me either. I am kind of disappointed:icon_frown: and frustrated](*,) with all this situation but until now it's seems to remain without any solution. The failure applies to any user including Guest. Unity just don't want to load.

Other error #-othat appeared with this update is that Shutter at login starts to show a lot of error messages similar to the following (valid only for SVG files, but for now this problem is not critical to me):
 ```
"There was an error opening the image. 
Error while opening image 'executable.svg'.
Could not recongize the image file format for file 
/usr/share/shutter/resources/icons/executable.svg
"
```
libgdk-pixbuf2.0-0 and librsvg2-2 were reinstalled and the "loaders.cache" was regenerated and contains svg same as svg library is in "loaders" folder 


Any help, ideas, solutions will be greatly appreciated!


[B]My PC:
Intel® Core™ i5-4690K CPU @ 3.50GHz × 4
Video AMD Radeon R9 200 Series
64-bit
RAM 7.6 GiB
Ubuntu 14.04.2 LTS
Compiz 0.9.12[/B]

Syslog:
```

Mar  6 03:44:59 spasmws01 kernel: [   37.091869] show_signal_msg: 171 callbacks suppressed
Mar  6 03:44:59 spasmws01 kernel: [   37.091872] compiz[4598]: segfault at 0 ip 00007f654cae61eb sp 00007fff5726e9c0 error 4 in libunityshell.so[7f654c6a8000+5ab000]
Mar  6 03:44:59 spasmws01 gnome-session[4323]: WARNING: Application 'compiz.desktop' killed by signal 11
Mar  6 03:44:59 spasmws01 gnome-session[4323]: WARNING: App 'compiz.desktop' respawning too quickly
Mar  6 03:44:59 spasmws01 gnome-session[4323]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Mar  6 03:44:59 spasmws01 kernel: [   37.760065] compiz[4791]: segfault at 0 ip 00007f1ffb4c11eb sp 00007fff7ed32480 error 4 in libunityshell.so[7f1ffb083000+5ab000]
Mar  6 03:44:59 spasmws01 gnome-session[4323]: WARNING: App 'compiz.desktop' respawning too quickly
Mar  6 03:44:59 spasmws01 gnome-session[4323]: WARNING: Application 'compiz.desktop' killed by signal 11
Mar  6 03:44:59 spasmws01 gnome-session[4323]: WARNING: App 'compiz.desktop' respawning too quickly[7f906f5cc000+5ab000]

```

Xorg.0.log content (as always, nothing unusual):
```
Script for ibus started at run_im.
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth main process ended, respawning
upstart: indicator-bluetooth respawning too fast, stopped
```

/usr/lib/nux/unity_support_test -p output:
```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon R9 200 Series
OpenGL version string:  4.3.12798 Compatibility Profile Context 13.35.1005

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by l-contactarsergio on 2015-03-06
Ok  guys. I have a massive Unity crash after update to latest 14.04.2LTS.  After trying a whole bunch of options, I've downloaded the latest Ubuntu  desktop, started live CD (Try Ubuntu) instead of installing it, and  guess what? It crashed the same way as on my computer. I have an empty Desktop with no panels and  notifications. After debugging I'm pretty sure it's a Compiz issue, it  crashes there at generate desktop, and it should be fixed ASAP. It just  didn't work. Meanwhile I'll be moving to other flavor of Linux. After  YEARS using Ubuntu that's the first time it happens. Kernel Update  didn't helped, I had to revert to the 3.13.0-46.77 in order to be able  to load Gnome at least and backup everything. Tried to install MATE desktop but it appears broken with icons and I'm unab;e change Themes. Something just didn't add here. Syslog keeps generating compiz and desktop issues.

---

### Post by PopsTheSailor on 2015-03-07
I'm having a similar issue that I'm trying to track down. One thing that was suggest to me to try (and it worked) is to boot into recover mode (at the Grub menu) the just select resume. I did that and I get my UI back. It's a pain in the keester but at least I can get to my UI while I try and track down the root cause.

---

### Post by l-contactarsergio on 2015-03-07
Thanks man. That was one of the first things to do before purging/reinstalling stuff. I'm always go step-by-step before do core changes. The funniest thing is that even Live CD fsils with the same issue on my machine While 14.04.1 LTS works. Xorg and xsessions messages are basically clean. If fglrx fails normally it starts in low graphics mode. But in my case it loads as usual and picks resolutions correctly. More than that, Gnome works perfectly fine. The default one, the Compiz and the Metacity. The only issue is when I'm trying to start Unity. Well, and this annoying SVG error. I'm moving to xubuntu mint install and will see what happens. Will do daily rsync backups just because I can't rely on stability of the system anymore.

---

