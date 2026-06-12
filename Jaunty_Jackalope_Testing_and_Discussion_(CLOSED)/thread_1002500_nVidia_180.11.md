---
title: "nVidia 180.11"
date: 2008-12-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2008-12-05
EDIT  Driver broken  22/12 

Community fix

[http://ubuntuforums.org/showpost.php?p=6408781&postcount=83](http://ubuntuforums.org/showpost.php?p=6408781&postcount=83)


Is available in repo, Jockey does not see this driver for the moment..
(at least for me, installed modalias with no luck)

```
sudo apt-get install nvidia-glx-180
```


Packageinfo
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)


nVidia info
[http://www.nvnews.net/vbulletin/showthread.php?p=1861825](http://www.nvnews.net/vbulletin/showthread.php?p=1861825)

Manual:
[ftp://download.nvidia.com/XFree86/Linux-x86/180.11/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.11/README/index.html)


VDPAU för newer cards, please READ the whole message....
[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

---

### Post by fjf on 2008-12-05
How can we use this to install them in 8.10?

---

### Post by plun on 2008-12-05
> **fjf said:**
> How can we use this to install them in 8.10?

The [bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/297543") says "In progress"....

This driver is a **beta release** and for Jaunty its no problem with betas.  Jaunty is unstable....

You can also find comments within the bug report that Jauntys driver can be used....   I don't recommend anything...

---

### Post by phenest on 2008-12-05
I'm using it now, but my GPU hits 70C! It never used to get hotter than 55C in Hardy. Could a high temperature cause harm? And what would be a safe limit (for a 7950GTX)? Or, maybe, could the temperature reading be inaccurate?

Otherwise the driver seems fine.

---

### Post by plun on 2008-12-05
> **phenest said:**
> I'm using it now, but my GPU hits 70C! It never used to get hotter than 55C in Hardy. Could a high temperature cause harm? And what would be a safe limit (for a 7950GTX)? Or, maybe, could the temperature reading be inaccurate?

Otherwise the driver seems fine.

If you start nvidia-settings it should be correct.

I am rock solid around 50C with a 7600GS card,   **kernel 2.6.28-ub-2 **

But... maybe we have a small memory leakage and I can also see a
little CPU increase for the Xorg process.

Also nothing alarming in nVidias forum
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by caryb on 2008-12-05
The manual download link does not work for me, does anyone else have the same problem?


Cary

---

### Post by plun on 2008-12-05
> **caryb said:**
> The manual download link does not work for me, does anyone else have the same problem?
Cary

Wake up "down under"....:D

The package is within *_Jauntys repo_*...[B]nvidia-glx-180
[/B]

But maybe you are using a sleepy archive ?

---

### Post by caryb on 2008-12-05
I have used the version in the repo's but for some crazy reason the repo version insists on removing nvidia-config & when you run KDE4 with it's limited tools you need the config tool to use 2 monitors or operate a LCD projector. Thats why I manually install my video driver.


Cary;)

BTW I don't want to wake up! I just came back from a weeks holiday on Stradbroke Island (off the east coast of OZ) & if I wake I will come to the realisation that I have to go back to work on Monday:-(

---

### Post by phenest on 2008-12-06
Hmmm. I'm getting black flashes periodically.

EDIT: Disabling Compiz does nothing. Preferences>Screen Resolution shows the Refresh Rate at 81Hz. That's not right. I've altered the refresh in nvidia-settings to 60Hz to see what that does.

---

### Post by plun on 2008-12-06
> **caryb said:**
> I have used the version in the repo's but for some crazy reason the repo version insists on removing nvidia-config & when you run KDE4 with it's limited tools you need the config tool to use 2 monitors or operate a LCD projector. Thats why I manually install my video driver.

BTW I don't want to wake up! I just came back from a weeks holiday on Stradbroke Island (off the east coast of OZ) & if I wake I will come to the realisation that I have to go back to work on Monday:-(

Aha... well we are in the middle of the winter and it rains and snowing.......:-\" 

I noticed that Jauntys driver removes the GUI entry for nvidia-settings but
it can be run from the terminal or make a new GUI entry for nvidia-settings.

---

### Post by pferraro on 2008-12-06
> **plun said:**
> 
I noticed that Jauntys driver removes the GUI entry for nvidia-settings but
it can be run from the terminal or make a new GUI entry for nvidia-settings.

It's still there - though in a different location.
Look in System->Administration

---

### Post by plun on 2008-12-06
> **pferraro said:**
> It's still there - though in a different location.
Look in System->Administration

Thanks !  it was moved ...:^o

System > prefs is maybe more logic ?


nVidia will support RandR 1.2 I also read...

[http://www.phoronix.com/scan.php?page=news_item&px=NjkwMw](http://www.phoronix.com/scan.php?page=news_item&px=NjkwMw)

---

### Post by phenest on 2008-12-06
> **pferraro said:**
> It's still there - though in a different location.
Look in System->Administration

Mine is still under System Tools.

---

### Post by phenest on 2008-12-07
Is anyone getting random black blocks in apps? I'm guessing this is a driver issue. When it next happens, I'll grab a screenshot.

---

### Post by autocrosser on 2008-12-07
Not blocks in apps, but black pixels in patterns at the top of my screen---not appearing in either of my other installs, just this one. Take a look at the upper right side.

---

### Post by ronacc on 2008-12-07
I'm not seeing anything like that here , amd64,7600gs,180.11

---

### Post by autocrosser on 2008-12-07
Interesting--that just happened with the update to 2.6.28-2 & the 180.11 driver--maybe not playing well with my SLI'd 8600GT/OC cards.......I'm going to do some checking at nVidia forums.......

---

### Post by vishalrao on 2008-12-07
No obvious issues noticed with 180.11 on an 8800GT. But then again, I'm on Kubuntu 8.10 amd64 with KDE 4.2 Beta 1 from the experimental repos :D

---

### Post by aseries on 2008-12-07
I have installed 8.10 on a new MSI GX630 notebook with no graphics trouble. I did have to go through all that ndiswrapper nonsense to get wireless networking.
I have a lab machine with PCCHIPS M825 that needs LINUX because I am using the XP Pro license elsewhere. I absolutely could NOT get any 8.10 or 8.04 graphics driver to work properly with the integrated VIA/S3 northbridge or an Nvidia MX4000, Geforce 2, or an old ATI Rage Pro and the SAMSUNG 151V LCD. I got no res past 800-600.
No offense, but PCLINUXOS installed ALL of the prior mentioned graphics solutions 1024-768-24 AUTOMATICALLY. It also installed the wireless AUTOMATICALLY. Of course, nothing is perfect, PCLINUXOS livecd hangs on boot on the MSI notebook, something to do with native SATA.
Now, :oif I could get my Linksys wireless print server to work with ANY Linux flavor.

---

### Post by ronacc on 2008-12-07
good luck with the via/s3 graphics , my one experience with them caused me to swear off via forever ditto lynksys tried one of their routers 3 frustrating days and much googling later I returned it for a refund .

---

### Post by autocrosser on 2008-12-07
Interesting comments, but this is the testing forum for 9.04. You might also find that PClinuxos uses older system versions than we do, so the compare is not very valid--It's harder for a OS that uses "almost" the latest versions.........

---

### Post by jfernyhough on 2008-12-08
Does anyone have issues with slow scrolling in Java apps? It's particularly noticeable in Freemind (freemind.sf.net) when moving the canvas, but it's also there in Netbeans. It used to be smooth as silk, tried with Metacity instead of Compiz and same thing. I haven't tried going back to a free driver yet.

---

### Post by David A Knight on 2008-12-09
> **autocrosser said:**
> Not blocks in apps, but black pixels in patterns at the top of my screen---not appearing in either of my other installs, just this one. Take a look at the upper right side.

Seeing almost the same here, although my dots are in nice straight lines, 8400M GT  x86-64

---

### Post by autocrosser on 2008-12-09
Interesting---I tried reinstalling all of Xorg & no change.....not sure what is causing it.....Have you tried anything?

---

### Post by IanW on 2008-12-09
Seems to be working ok in Intrepid, so far...

---

### Post by nanog on 2008-12-09
Supporting Rand1.2 is great but I would rather they just open source their stack.

---

### Post by plun on 2008-12-09
> **nanog said:**
> Supporting Rand1.2 is great but I would rather they just open source their stack.

Of course....

nVidia gave an answer earlier this year to a group of kernel developers that
it was impossible for the moment to open the driver, mainly as I understood it because of licensed code from 3rd partys.

Maybe next year....

---

### Post by MacUntu on 2008-12-09
Next year? No way. AFAIK they don't plan on releasing specifications or an open source driver.

Waiting for Nvidia to release open source drivers will make you as happy as waiting for Godot.

---

### Post by plun on 2008-12-13
Here we go again....   ver 180.16

[http://www.nvnews.net/vbulletin/showthread.php?t=124599](http://www.nvnews.net/vbulletin/showthread.php?t=124599)

A lot of VDPAU changes

> VDPAU users, please note that the arguments to VdpDecoderCreate have changed. Updated VDPAU patches are available.

Release Highlights:

    * Added support for the following GPUs:
          o Quadro FX 2700M
          o GeForce 9400M G
          o GeForce 9800 GT
          o GeForce 9800 GT
          o GeForce 8200M G
          o GeForce Go 7700
          o GeForce 9800M GTX
          o GeForce 9800M GT
          o GeForce 9800M GS
          o GeForce 9500 GT
          o GeForce 9700M GT
          o GeForce 9650M GT
          o GeForce 9500 GT
    * Fixed a problem with the SDI sync skew controls in nvidia-settings.
    * Fixed a problem that caused some SDI applications to hang or crash.
    * Fixed an nvidia-settings crash when xorg.conf contains Device and Screen sections but no ServerLayout section.
    * Fixed a problem that caused the Linux OpenGL library to crash when used inside FreeBSD's Linux emulation layer.
    *[B] Updated VDPAU:
          o VdpDecoderCreate API has changed incompatibly. All client applications must be rebuilt because of this change.
          o For H.264, require the application to tell VDPAU how many reference frames to allow. This allows the application to request more than 4 reference frames. VDPAU should now support level 4.1 reference frame limits on all GPUs (or very close to this limit). The application now has control over this aspect of VDPAU's memory usage.
          o Fix corruption decoding some H.264 streams on some GPUs.
          o Fix a bug that prevented VC-1/WMV3 decode from being allowed on some GPUs.
          o Documentation enhancements and cleanups to vdpau.h.
          o Don't paint the color key to presentation queue targets until the first frame is presented. This should reduce or remove the time the key is displayed before the presented frame is visible.[/B]



Testing....

---

### Post by phenest on 2008-12-13
> **phenest said:**
> Is anyone getting random black blocks in apps? I'm guessing this is a driver issue. When it next happens, I'll grab a screenshot.

Here's an example:

---

### Post by Gina on 2008-12-13
Yes, I am!  My gc is nvidia GeForce 6200 with nvidia 177 driver.

---

### Post by plun on 2008-12-13
> **Gina said:**
> Yes, I am!  My gc is nvidia GeForce 6200 with nvidia 177 driver.

The 180 driver should work for you.

180.11 is the recommended driver for Jaunty.  Check Meny System > Administration > Hardware drivers.

Just excellent performance....180.16 was even better...(better the Windows)

---

### Post by Gina on 2008-12-13
It's only showing 173, 96 and 177 for me :(  Do I have to do something to get 180?

---

### Post by plun on 2008-12-13
> **Gina said:**
> It's only showing 173, 96 and 177 for me :(  Do I have to do something to get 180?

Strange... this is Ubuntus package

[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

I wonder if modalias isnt pushed yet... ???  It is probaby needed for Jockey to see it... but :confused:

---

### Post by ronacc on 2008-12-13
modailas for 180 is showing for me on 64bit .
@ gina try another mirror I've had the 180 packages since dec 5 .

---

### Post by plun on 2008-12-13
> **ronacc said:**
> modailas for 180 is showing for me on 64bit .
@ gina try another mirror I've had the 180 packages since dec 5 .

Well... it might be the famous **dist-upgrade** again...  ):P

---

### Post by ronacc on 2008-12-13
or it might be update manager . I use apt-get for updates and synaptics for non default pkgs .

---

### Post by Gina on 2008-12-14
Thanks everyone :)  Been into Synaptic and installed the 180 driver stuff including modaliases.  It uninstalled the setting up bits for 177 at the same time.  I now have 180 in my Hardware Drivers list and it's showing as enabled so I guess that's what I'm now using.  177 is also there but no longer enabled.  I'll find out later if everything is still fine when I reboot :lol:

---

### Post by Gina on 2008-12-14
I still got the black bits after installing 180 so have restarted.  So far so good.  No disaster - now waiting for any display funnies.

---

### Post by plun on 2008-12-14
> **Gina said:**
> I still got the black bits after installing 180 so have restarted.  So far so good.  No disaster - now waiting for any display funnies.

Can you please try to take a screenshot with these boxes... ?

The only place to post such a bug is within nVidias forum.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I can search a little for other posts with black boxes.

There is also a new 173 driver.

---

### Post by Gina on 2008-12-14
I'll try :)  Just had it again whilst viewing another message board in Firefox.  What I can tell you is that the black bits move with the rest when scrolling but disappear when scrolled off and back again.  Next time I get it I'll try a screenshot.  

Ha ha - having just written that I got two small balck rectangles at the edge of this screen between the board frame and the edge of the window.  As soon as I clicked the menu to take a screenshot the black bits vanished!

EDIT After clicking Edit to correct a typo there are several black bits  Apparently a rectangle at the bottom of the frame behind this one, half height at the edge between the board main frame and the scrollbar.  Plus another at the bottom of the window.  I've put a direct access icon for screenshot on the top panel and after that some black bits came again but disappeared as soom as I brought up the screenshot dialog.

---

### Post by plun on 2008-12-14
> **Gina said:**
> I'll try :)  Just had it again whilst viewing another message board in Firefox.  What I can tell you is that the black bits move with the rest when scrolling but disappear when scrolled off and back again.  Next time I get it I'll try a screenshot.  

Ha ha - having just written that I got two small balck rectangles at the edge of this screen between the board frame and the edge of the window.  As soon as I clicked the menu to take a screenshot the black bits vanished!

EDIT After clicking Edit to correct a typo there are several black bits  Apparently a rectangle at the bottom of the frame behind this one, half height at the edge between the board main frame and the scrollbar.  Plus another at the bottom of the window.  I've put a direct access icon for screenshot on the top panel and after that some black bits came again but disappeared as soom as I brought up the screenshot dialog.

OK... are you running Firefox 3.04 or 3.1 ?   the rendering is changed in FF3.1 and faster.

Also to be sure  Meny System > Administration > nVidia Xserver setting
(or a GUI within Systemtools)  and check version.

You can also use time delay for Screenshots,  it was difficult to find bugs as you describes it...:confused:

---

### Post by Gina on 2008-12-14
Firefox 3.04 nvidia driver 180.11 (screenshot og nvidia info attached).

I'll try Firefox 3.1

---

### Post by Gina on 2008-12-14
Now in F 3.1b2 (About attached) and still getting the black blocks.  Using delayed screenshot clears the black bits, so no help. :(

---

### Post by phenest on 2008-12-15
After todays partial upgrade, I had to drop back to the nv driver. If I try to install any of the nvidia-glx packages, it wants to remove loads of other stuff. I installed nVidias driver manually and setup xorg.conf to use it but won't.

---

### Post by xebian on 2008-12-15
> **phenest said:**
> After todays partial upgrade, I had to drop back to the nv driver. If I try to install any of the nvidia-glx packages, it wants to remove loads of other stuff. I installed nVidias driver manually and setup xorg.conf to use it but won't.

I don't get the point of partial upgrade.  If required dependencies are not complete then it should not upgrade.

BTW, just ignore the ABI and it should work.  I have 180.16 working nicely with GeForce6150.

---

### Post by bobya on 2008-12-20
Hi all,
This might sound as a stupid question, but how to ignore the ABI ?

---

### Post by plun on 2008-12-20
> **bobya said:**
> Hi all,
This might sound as a stupid question, but how to ignore the ABI ?

the "dinxter" way is a smart one....:)

[http://ubuntuforums.org/showpost.php?p=6378516&postcount=25](http://ubuntuforums.org/showpost.php?p=6378516&postcount=25)

.

---

### Post by ubulette on 2008-12-20
not really usable for me. It makes X crash randomly :(

```

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813281b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c5dc5]
2: [0xb808f400]
3: /usr/X11R6/bin/X [0x812202b]
4: /usr/X11R6/bin/X [0x812261d]
5: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0xb6adfe71]
Saw signal 11.  Server aborting.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Microsoft Microsoft IntelliMouse? Optical: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

---

### Post by plun on 2008-12-20
> **ubulette said:**
> not really usable for me. It makes X crash randomly :(

```

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813281b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c5dc5]
2: [0xb808f400]
3: /usr/X11R6/bin/X [0x812202b]
4: /usr/X11R6/bin/X [0x812261d]
5: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0xb6adfe71]
Saw signal 11.  Server aborting.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Microsoft Microsoft IntelliMouse? Optical: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

Have you tried both 180.11 and 180.16 ?  .16 seems to be better and there are also 2 versions of .11

Ver 180.16
[http://www.nvnews.net/vbulletin/showthread.php?p=1873716](http://www.nvnews.net/vbulletin/showthread.php?p=1873716)

If you boots with **nosplash, tty also works**... no need for recovery and install.

I made a little adjustment for my mouse within the settings GUI, decreased both sensitive and speed. It was a rather "nervous" mouse before changing those settings...:)

---

### Post by ubulette on 2008-12-20
> **plun said:**
> Have you tried both 180.11 and 180.16 ?  .16 seems to be better and there are also 2 versions of .11

Ver 180.16
[http://www.nvnews.net/vbulletin/showthread.php?p=1873716](http://www.nvnews.net/vbulletin/showthread.php?p=1873716)

If you boots with **nosplash, tty also works**... no need for recovery and install.

I made a little adjustment for my mouse within the settings GUI, decreased both sensitive and speed. It was a rather "nervous" mouse before changing those settings...:)

I just tried the one for jaunty.
I have two mouse cursors, one fix. It's annoying, it's over everything.

boom, another crash while editing this post. Thanks to firefox 3.1 for saving my session, including this post :P Only one mouse this time..

---

### Post by plun on 2008-12-20
> **ubulette said:**
> I just tried the one for jaunty.
I have two mouse cursors, one fix. It's annoying, it's over everything.

boom, another crash while editing this post. Thanks to firefox 3.1 for saving my session, including this post :P Only one mouse this time..

Ok... also check  Xorg.0.log for more clues...  evdev thought that my sound-system was a keyboard and made some configs for it..:)
(bug filed)

Bug hunt...:)

---

### Post by IanW on 2008-12-23
[180.18 beta](http://www.nvnews.net/vbulletin/showthread.php?t=125134) released. Rumours of final version to arrive in January.

---

### Post by plun on 2008-12-23
> **IanW said:**
> [180.18 beta](http://www.nvnews.net/vbulletin/showthread.php?t=125134) released. Rumours of final version to arrive in January.

Tried it and broke it....:---)

Similar to this thread about Intrepid

[http://www.nvnews.net/vbulletin/showthread.php?t=125141](http://www.nvnews.net/vbulletin/showthread.php?t=125141)

This challenge is probably a symlink issue (from my installer log)

> -> Searching for conflicting X files:
ERROR: Unable to open '/usr/lib/nvidia/libglx.so.xserver-xorg-core' for reading
       (No such file or directory)
ERROR: Unable to open '/usr/lib/nvidia/libglx.so.xserver-xorg-core' for reading
       (No such file or directory)
-> done.
-> Searching for conflicting OpenGL files:


EDIT OK after removing 180.16 PPA version, DKMS and nvidia kernel source...  Testing !

---

### Post by ronacc on 2008-12-23
OT I haven't played much with "onboard" graphics , due to a motherboard failure and a good deal on a mobo with an onboard nvidia 8200 gpu I gave it a try , gave it 256mb mem in bios ( I have 4 gig total) and the short story is the frame rate with full screen video was horrible , droping 80>90 % of the frames, though it was ok in a small window . I installed the nvidia 7600le card off of the dead mobo (also 256mb but onboard rather than shared) and the frame rate is perfect no frames dropped on the same video . Is this "normal" for onboard video ?

---

### Post by plun on 2008-12-23
> **ronacc said:**
> OT I haven't played much with "onboard" graphics , due to a motherboard failure and a good deal on a mobo with an onboard nvidia 8200 gpu I gave it a try , gave it 256mb mem in bios ( I have 4 gig total) and the short story is the frame rate with full screen video was horrible , droping 80>90 % of the frames, though it was ok in a small window . I installed the nvidia 7600le card off of the dead mobo (also 256mb but onboard rather than shared) and the frame rate is perfect no frames dropped on the same video . Is this "normal" for onboard video ?

Onboard graphics are often tricky and also adjusted against a specific mobo.

Also the cheapest GPUs such as 6200, 7200, 8200 often got performance trouble.

You can also often find BIOS updates for these onboard graphics... DELL got a disaster with broken nVidia chips...

Costs nVidia a billion or more....

---

### Post by jfernyhough on 2008-12-23
OK, that was weird.

First try installing .18 in the same way as the others appears to succeed but X fails to start.

nvidia-installer --uninstall then a reinstall, same result. Reboot with the nvidia driver disabled in xorg.conf, X works, stop gdm, uninstall, reinstall, uninstall, reinstall. And it works.

Strange, but hey - it's working now... :D

Oh, and the jittery-cursor seems to have been fixed, which is nice.

Ack, just run nvidia-settings and I now have a floating cursor when I scroll. Grr... restart X and don't touch nvidia-settings!

--edit
Spoke too soon - jittery cursor is still here.

---

### Post by Kevbert on 2008-12-23
Just tried installing nvidia driver as per Plun's first post and it removes a large number of xorg drivers (ones I don't need). Installed and wireless disconnected and then reconnected as the install finished. Then did a reboot and the attached was displayed... I'm also using a 7600GS card.  Nothing seems to work apart from a hard reset.

---

### Post by plun on 2008-12-23
> **Kevbert said:**
> Just tried installing nvidia driver as per Plun's first post and it removes a large number of xorg drivers (ones I don't need). Installed and wireless disconnected and then reconnected as the install finished. Then did a reboot and the attached was displayed... I'm also using a 7600GS card.  Nothing seems to work apart from a hard reset.

No Jauntys driver is broken for unknown reasons and its not rebuild yet.

This community walk around works....

[http://ubuntuforums.org/showpost.php?p=6408781&postcount=83](http://ubuntuforums.org/showpost.php?p=6408781&postcount=83)

This is also mentioned in release notes for Alpha 2 > Known Issues !

---

### Post by plun on 2008-12-23
> **jfernyhough said:**
> 
Spoke too soon - jittery cursor is still here.

Slow down both acceleration and sensitivity within the mouse GUI....
(a little)  

I also checked my second install and its for sure important to uninstall before install....nvidia-installer --uninstall

Symlink-mess otherwise...

```
WARNING: Your driver installation has been altered since it was initially
         installed; this may happen, for example, if you have since installed
         the NVIDIA driver through a mechanism other than nvidia-installer
         (such as your distribution's native package management system). 
         nvidia-installer will attempt to uninstall as best it can.  Please see
         the file '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-18018
   (180.18)):
-> Unable to restore symbolic link /usr/lib/nvidia/libGL.so.1.xlibmesa ->
   libGL.so.180.16 (No such file or directory).
-> Unable to restore symbolic link /usr/lib/nvidia/libglx.so.xserver-xorg-core
   -> libglx.so.180.16 (No such file or directory).
ERROR: Unable to create '/usr/lib/nvidia/libnvidia-cfg.so.180.16' for copying
       (No such file or directory)
WARNING: Unable to restore file '/usr/lib/nvidia/libnvidia-cfg.so.180.16'.
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (180.18) is complete.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (180.18):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
```

---

### Post by obsrv on 2008-12-23
I get this:

```
obsrv@PIRATE:~$ sudo su
root@PIRATE:/home/obsrv# aptitude install nvidia-glx-180
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  xserver-xorg-core 
The following NEW packages will be installed:
  nvidia-180-kernel-source{a} nvidia-glx-180 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.5MB of archives. After unpacking 62.1MB will be used.
The following packages have unmet dependencies:
  xserver-xorg-core: Conflicts: xserver-xorg-video-4 which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop
xorg
xserver-xorg
xserver-xorg-core
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-kbd
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-wacom
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-ati
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-fbdev
xserver-xorg-video-i128
xserver-xorg-video-intel
xserver-xorg-video-mach64
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-r128
xserver-xorg-video-radeon
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-v4l
xserver-xorg-video-vesa
xserver-xorg-video-vmware
xserver-xorg-video-voodoo

Leave the following dependencies unresolved:
gdm recommends xserver-xorg
Score is 2610

Accept this solution? [Y/n/q/?] 


```

---

### Post by ronacc on 2008-12-23
@ plun thanks for the info , it's no disaster, I learned something , I'll just do what I have always done and use a dedicated video card , fortunately I had the 7300le that was on the failed board to stick in so that little "experiment" didn't cost me anything .

---

### Post by obsrv on 2008-12-23
I managed to get nvidia driver without removing XOrg. Now I have a problem of somekind of mismatch. It says I have to disable ABI. How do I disable it to automatically start without ABI check?

---

### Post by jfernyhough on 2008-12-23
Have you read this thread?

Anyhow, in /etc/X11/xorg.conf you need the following:
```

Section "ServerFlags"
    Option    "IgnoreABI"    "True"
EndSection

```

---

### Post by zim2dive on 2008-12-24
> **ronacc said:**
> OT I haven't played much with "onboard" graphics , due to a motherboard failure and a good deal on a mobo with an onboard nvidia 8200 gpu I gave it a try , gave it 256mb mem in bios ( I have 4 gig total) and the short story is the frame rate with full screen video was horrible , droping 80>90 % of the frames, though it was ok in a small window . I installed the nvidia 7600le card off of the dead mobo (also 256mb but onboard rather than shared) and the frame rate is perfect no frames dropped on the same video . Is this "normal" for onboard video ?

I'm having the same cr@p performance with full-screen Flash with an 8200, but back on 177.80 (the Intrepid default nvidia driver).. I've tried 180.11,.16 and seen no improvement for Flash, and massive instability, enough that I had to re-install... 

I'm at a loss.. full-screen (1080p) flash is flawless under Vista (but I have no desire to run Vista.. I want to find a way to make Ubuntu work... just so far I can't)

I had considered whether I could get an 8400gs and run in SLI, but I'd need a slimline.. and not at all sure if I'd see any benefits.. ie. even a 100% performance boost would still be dropping 2 out of every 3 frames.. what gives???

---

### Post by ronacc on 2008-12-24
Interesting that vista will play FS ok when Ubuntu won't , I couldn't test that , I havent run anykind of windows in >8 years . I didn't play around much because I had the 7300le sitting there and knew for sure it would work as it had been on the dead mobo and I had pleanty of room because I build my own boxes and always use full atx mobo's and big cases . I disabled the 8200 in bios , the 7000 series cards don't do hybrid sli .BTW that was on intrepid with the 177.80 driver ( thats why I said it was OT ).I may play arround a bit I'm getting ready to stuf in another HD and install Sabayon 3.5.1 and OpenSuse 11.1 I'll see if they do any better since I can switch gpu's in bios without physicaly removing the 7300 , I'll also play with drivers it will be a learning experience .

---

### Post by zim2dive on 2008-12-24
> **ronacc said:**
> Interesting that vista will play FS ok when Ubuntu won't , I couldn't test that , I havent run anykind of windows in >8 years . 

I've done a wubi-based install.. figured that was the quickest way to dive in to my 1st ubuntu install... beginning to wonder if I didn't dive in head 1st and forgot to check if the pool had any water in it tho... (getting sound and video has been an uphill battle).  But yes, under Vista, it flies.  And under Ubuntu, vlc and mplayer are fine in full screen.

---

### Post by alexv75 on 2008-12-24
> **zim2dive said:**
> I'm having the same cr@p performance with full-screen Flash with an 8200, but back on 177.80 (the Intrepid default nvidia driver).. I've tried 180.11,.16 and seen no improvement for Flash, and massive instability, enough that I had to re-install... 

I'm at a loss.. full-screen (1080p) flash is flawless under Vista (but I have no desire to run Vista.. I want to find a way to make Ubuntu work... just so far I can't)

I had considered whether I could get an 8400gs and run in SLI, but I'd need a slimline.. and not at all sure if I'd see any benefits.. ie. even a 100% performance boost would still be dropping 2 out of every 3 frames.. what gives???

I've just tried Space Alone 1080p from Adobe's HD Gallery - on 7950GT with 180.18 and 4.05GHz CPU it uses ~10-25% of one core and runs smooth (64bit flash from the repo). Adobe did great job, i'm happy they released a native 64bit plugin at last :p

---

### Post by LaneLester on 2008-12-30
> **obsrv said:**
> I get this:

```
Remove the following packages
```
Yeah, I got the same thing when I tried to install 173, which is the right one for my old 5500 card. I went ahead and said yes, and as expected, lost video completely.

I don't know how to sneak a driver in manually, so I guess I'll wait until the "official" approach works.

Lane

---

