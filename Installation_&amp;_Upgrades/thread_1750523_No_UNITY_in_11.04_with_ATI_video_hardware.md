---
title: "No UNITY in 11.04 with ATI video hardware"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by tazzarias on 2011-05-05
Hi all,
 
Upgraded yesterday from 10.10 to 11.04, UNITY issues with the PC. The "Ubuntu Classic" option at login works fine.
 
The symptoms when attempting to use UNITY are:
1) after login, I see desktop background image
2) mouse works, context menu I can pull up has "Create Folder", "Create Launcher" ...etc
3) keyboard works, ie, CTL-ALT-T brings up terminal, I can type away
4) desktop shows no toolbars, no menubars, no dash, nothing UNITY related
 
Running unity_support_test (output below) reveals it is a PASS for UNITY support:
 
$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV515
OpenGL version string: 2.1 Mesa 7.10.2
Not software rendered: yes
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
GL vertex program: yes
GL fragment program: yes
GL vertex buffer object: yes
GL framebuffer object: yes
GL version is 1.4+: yes
Unity supported: yes
 
Here's the output from lspci:
 
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
 
Also, System->Administration->"Additional Drivers" shows "No proprietary drivers are in use on this system", and there are no selections available to me in that dialog box.
 
Any assistance would be appreciated please, as I would love to try UNITY out.

---

### Post by tazzarias on 2011-05-06
Good results so far by following this guide:
 
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)
 
Note that I'm not using proprietary drivers.
 
Seems the steps that really did it for me were:
1) ensuring Unity was enabled via ccsm
2) moving aside the existing /etc/X11/xorg.conf file
 
In any case, playing with UNITY now.

---

### Post by sikander3786 on 2011-05-06
So we can assume that the issue has been resolved by now?

---

### Post by rtimai on 2011-05-08
Sikander,

Thank you so much for your Unity blog! 

I have ATI M880G [Mobility Radeon HD 4200] video system, and Unity booted to only a blank desktop wallpaper with no panels. Alt-F2 was disabled, so I could not run anything except in TTY. Fortunately Alt-Ctrl-Del continued to work so I could restart and select Ubuntu Classic (Metacity.) 

However I was dying to learn more about Unity, and your blog finally provided the fix for my problems (in my case it was the "unity --reset" command that restored my side launcher panel and top panel. 

It does seem that the causes of missing panels vary from system to system depending on pre-existing settings. BTW, I set the default window decorator command to 'gtk-window-decorator --replace' but after resetting Unity, it was changed back to '/usr/bin/compiz-decorator'.

Now for those new to the Unity desktop, I think everyone's a beginner!

---

### Post by Blasphemist on 2011-05-08
I just wanted to be sure both of you ATI users that have had some issues had this. It looks like both of your systems are covered by this.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by rtimai on 2011-05-09
Blasphemist,

Yes, I have the supported Mobility Radeon HD 4200 adapter. Tazzarias has stated that he was using the open source driver with the RV516 Radeon X1300/X1550 Series. 

I had installed the "ATI/AMD proprietary FGLRX graphics driver" before applying the fix that restored Unity to my system. And Unity appears to be running now without problems (in fact it is described in the "Additional Drivers" tool as necessary for 3D support,) so I will keep it. 

I will, however keep the URL to the Radeon information you provided, in case I need to remove the proprietary driver and revert to the open source driver -- and I thank you for that reference. It does appear that some systems may actually run Unity better with the proprietary driver (and I have seen this supported by other user postings.)

My main concern right now are usability issues. I'm finding the changes brought by Unity a little frustrating at the moment, can't see all of my installed applications, and finding that launcher icons appear to move around in the menus. For users who like everything in its place, this takes some getting used to.

---

### Post by sikander3786 on 2011-05-09
> **rtimai said:**
> BTW, I set the default window decorator command to 'gtk-window-decorator --replace' but after resetting Unity, it was changed back to '/usr/bin/compiz-decorator'.


No problem, both of them are reportedly working fine in Unity :-)

---

### Post by tazzarias on 2011-05-10
> **sikander3786 said:**
> So we can assume that the issue has been resolved by now?
 
Yes, it is resolved for me.
 
On a side note: Sadly, UNITY causes more problems than it solved, so I've reverted back to Ubuntu Classic.

---

