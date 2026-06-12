---
title: "Nvidia 180.18 Working Nicely"
date: 2008-12-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-12-23
Hi folks, I wanted to fiddle around with VDPAU so I manually installed Nvidia's latest 180.18 beta driver.

It required modification to my xorg.conf as per below:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
	Option		"IgnoreABI" "True"
EndSection
```

Now its working well.

---

### Post by plun on 2008-12-24
Yup... excellent driver.


About
[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)


VDPAU supported cards

> Desktop GPUs:
GeForce 200 Series
GeForce 9 Series
GeForce 86xx Series
GeForce 85xx Series
GeForce 84xx Series
GeForce 8300 GS
GeForce 8800 GTS 512
GeForce 8800 GT
GeForce 8800 GS

Mobile GPUs:
GeForce 98xxM
GeForce 9700M
GeForce 96xxM
GeForce 9500M
GeForce 9300M
GeForce 9200M
GeForce 8800M
GeForce 8800M GTS
GeForce 8800M GTX
GeForce 8600M
GeForce 8400M

Motherboard GPUs:
GeForce 9400
GeForce 9300
GeForce 9100
GeForce 8300
GeForce 8200


Latest Mplayer build script including patches  **NOTE! ONLY FOR 180.18** 

[ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3263604.tar.bz2](ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3263604.tar.bz2)


Xine and MythTV SVN supports VDPAU, VLC is coming.

---

### Post by luca_linux on 2008-12-24
Out of curiosity, what does the "IgnoreABI" parameter do? :P

---

### Post by RAOF on 2008-12-24
> **luca_linux said:**
> Out of curiosity, what does the "IgnoreABI" parameter do? :P

Makes the nvidia driver and the X server ignore the fact that the video driver interface of the X server doesn't match the interface the nvidia driver expects.  You get a nice "maybe it'll work, maybe it won't" warning in your Xorg.0.log.

**Edit**: it should go without saying, but you shouldn't file bugs for any form of graphical corruption or glitches or whatever if you do this.  Also, if you want to report a crash bug, please try without these drivers first.

---

### Post by luca_linux on 2008-12-24
> **RAOF said:**
> Makes the nvidia driver and the X server ignore the fact that the video driver interface of the X server doesn't match the interface the nvidia driver expects.  You get a nice "maybe it'll work, maybe it won't" warning in your Xorg.0.log.

**Edit**: it should go without saying, but you shouldn't file bugs for any form of graphical corruption or glitches or whatever if you do this.  Also, if you want to report a crash bug, please try without these drivers first.
Got it. Thank you for the explanation. :)

---

### Post by BGFG on 2009-01-02
Hi Guys, 
i installed the 180.18 driver manually, but i can't get it to work.
Basically when i attempt to 'startx' i get two errors:

1, Failed to load module 'type1'
2, API mismatch, module version is 177.82 and driver component is 180.18

180.17 however works fine. Any suggestions ?

Thanks.

Edit:
Please disregard, wrong forum. all is well now.

---

### Post by ronacc on 2009-01-02
even though VDPAU is not supported for my card (7600gs) the 180.18 driver  works fine with it .

---

### Post by plun on 2009-01-02
Anders has also updated his ppa

[https://launchpad.net/~anders-kaseorg/+archive](https://launchpad.net/~anders-kaseorg/+archive)

just to add it to software sources

180.18 for the moment....

---

### Post by jfernyhough on 2009-01-02
I'm tempted to reinstall using the PPA (so gaining DKMS support) but I just know that when I do Nvidia will release a new version themselves. :D

---

### Post by plun on 2009-01-02
> **jfernyhough said:**
> I'm tempted to reinstall using the PPA (so gaining DKMS support) but I just know that when I do Nvidia will release a new version themselves. :D

Of course.... according to Murphys laws..:D

"Bleeding egde" is playing with 2.6.28-gitx within nVidia forums.

I wait for RC1 until I build one....

---

### Post by pressureman on 2009-01-02
Is anyone else getting weird, intermittent screen updates in gnome-terminal? I have two laptops running Jaunty, one using open source ATI driver, the other using Nvidia 180.18. On the Nvidia one, sometimes if I do a 'ls -l', all I get is a blank space where the filenames should be, then it returns to the bash prompt.

It also seems to have trouble updating the last line at the bottom of the terminal. I don't have any of these problems on the ATI card.

---

### Post by caryb on 2009-01-02
I am back to no entries in my "K" button, It just has a black outline & nada! I had this a couple of Nvidia releases ago:confused:

Cary

Also I have lost my fancy GUI effects as well

---

### Post by vishalrao on 2009-01-02
@pressureman: yes i also see some terminal update problems when doing stuff like ls -l

---

### Post by Gina on 2009-01-03
Having a go at updating my AMD64 Jaunty system with the new xorg and nvidia-180 driver.  I have already altered my xorg.conf as above.  This was a reinstall of Jaunty Alpha 1 and now doing 507 updates.  I'll report back when it's done :)

---

### Post by Gina on 2009-01-03
Well it's working :)  Screen resolution is correct just like it was with the 177 driver but Hardware Drivers shows no Restricted Driver loaded.  I think it's lying :lolflag:

Only problem found so far is that Jaunty returns to login screen when doing some things in Totem.

---

### Post by plun on 2009-01-05
> **FFmpeg Gets Mainline VDPAU Support**
Posted by Michael Larabel on January 05, 2009

When NVIDIA introduced VDPAU support in November for providing excellent GPU playback support on Linux they released a set of patches that enabled the Video Decode and Presentation API for Unix support within the FFmpeg and MPlayer projects. Initially it looked like these patches would not be accepted into the mainline code-base, but committed to the FFmpeg repository last night was support for VDPAU.

This patch adds in support for hardware-accelerated H.264 video decoding using VDPAU. The MPlayer support hopefully isn't far behind. MythTV and Xine have already added support for this video API.

[http://www.phoronix.com/scan.php?page=news_item&px=Njk3MQ](http://www.phoronix.com/scan.php?page=news_item&px=Njk3MQ)




Patch
[http://git.ffmpeg.org/?p=ffmpeg;a=commit;h=d286159ad7620d37b8bfeacdba25686eb68c5046](http://git.ffmpeg.org/?p=ffmpeg;a=commit;h=d286159ad7620d37b8bfeacdba25686eb68c5046)


--------------------------------------------------------------

A 3rd PPA seems also to be up.....:-\"

[https://launchpad.net/~snaury/+archive](https://launchpad.net/~snaury/+archive)


Well, well.. a beta driver on a beta server on an alpha-version.

---

### Post by curtis on 2009-01-05
Anyone else getting random crashes where the screen goes all weird?

---

### Post by plun on 2009-01-05
> **curtis said:**
> Anyone else getting random crashes where the screen goes all weird?

Yup...I have had 2 crashes today and going to check if its the same with a 2.6.28 "Vanilla" kernel. 

It also seems to be kernel-panic... ALt-SysRq-b is also broken...

---

### Post by caryb on 2009-01-06
Have just upgraded my Xorg & now I have Kicker, rotating screen & no psychedelic flashing in Firefox:guitar::guitar:


Cary

---

### Post by taavikko on 2009-01-06
Have to ask before opening my laptop and starting up vacuum cleaner...

anybody experiencing GPU heating up problems?
example, I play urbanterror for a half an hour, temperature 
goes up to ~105c°, And so does mobo, around ~85c° And system starts to crawl (obviously :) )
Issue has persisted since 177-*.

Perhaps I'll just suck up the dust inside the laptop, but that's a drag...
Anyone ever opened a laptop... :(

---

### Post by plun on 2009-01-06
> **taavikko said:**
> Have to ask before opening my laptop and starting up vacuum cleaner...

anybody experiencing GPU heating up problems?
example, I play urbanterror for a half an hour, temperature 
goes up to ~105c°, And so does mobo, around ~85c° And system starts to crawl (obviously :) )
Issue has persisted since 177-*.

Perhaps I'll just suck up the dust inside the laptop, but that's a drag...
Anyone ever opened a laptop... :(

Yup...this photo shows my Acer Laptop...

[[img]http://ubuntu-pics.de/thumb/7994/1eb284beac6a7818702e4ac67e460_FT9kjm.jpg[/img]](http://ubuntu-pics.de/bild/7994/1eb284beac6a7818702e4ac67e460_FT9kjm.jpg)

You can see the problem.........:D, In my case I also must dismantle the cooling fan....

Many Laptops got manuals showing this at support pages....

Then it also depends where you have your "thumb in the hand" ;-), it might be a good idea to let someone which knows how do the job clean a laptop.....:D

Good Luck...!

---

### Post by Gina on 2009-01-06
I've often had laptops apart and they do get clogged up with dust.  But they can be pretty difficult to get into and it is often far from easy.  You need to be very careful and you need the right tools - eg. a small philips screwdriver.  You need good eyesight or a good magnifier and light.  And don't forget the earthing wrist strap to avoid zapping things with static electricity.  If you're not confident in taking delicate things apart and know about cleanliness and heat conducting paste between processor and heatsink, then I would suggest leaving it to an expert.  Things need undoing in the right order and putting back in the right order.

---

### Post by plun on 2009-01-06
> **Gina said:**
> I've often had laptops apart and they do get clogged up with dust.  But they can be pretty difficult to get into and it is often far from easy.  You need to be very careful and you need the right tools - eg. a small philips screwdriver.  You need good eyesight or a good magnifier and light.  And don't forget the earthing wrist strap to avoid zapping things with static electricity.  If you're not confident in taking delicate things apart and know about cleanliness and heat conducting paste between processor and heatsink, then I would suggest leaving it to an expert.  Things need undoing in the right order and putting back in the right order.

Yup...static electricity can be disaster, I always wears a **antistatic armband** when I works with a PC...

But...   $100 for a cleaning when its often is easy done.

---

### Post by ShirishAg75 on 2009-01-07
Another release of the driver on the archive. 

> 
nvidia-graphics-drivers-180 (180.18-0ubuntu1) jaunty; urgency=low

  [ Thomas Cheutz ]
  * Add driver 180.18 (LP: #307791)
   * Fixed an X server hang rendering very large fonts.
   * Added a check to nvidia-installer to not consider Compiz's libglx.so
     a conflicting X extension library.
   * VDPAU updates:
    o Relaxed restrictions on the number of H.264 references frames.
    o Fixed corruption problems in some video bitstreams.
    o Fixed a problem that prevented the presentation queue from working in some
      multi-display or multi-screen configurations when using overlay based presentation.

  [ Alexey Borzenkov ]
  * Fix false positive when generating modaliases

  [ Mario Limonciello ]
  * debian/control:
    - Introduce nvidia-180-libvdpau and nvidia-180-libvdpau-dev packages so that
      applications will be able to build depend and depend on libvdpau without needing
      to depend on nvidia driver itself.
  * debian/rules:
    - Install VDPAU headers and libraries into appropriate packages.
    - Don't run debhelper commands with -s as arch independent packages are ignored

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002657.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002657.html)

Feel free to comment.

---

### Post by gnomeuser on 2009-01-07
> **ShirishAg75 said:**
> Another release of the driver on the archive. 



[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002657.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002657.html)

Feel free to comment.

And a slight update.

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002675.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002675.html)

---

### Post by ShirishAg75 on 2009-01-07
Right. 

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002675.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002675.html)

> 
nvidia-graphics-drivers-180 (180.18-0ubuntu2) jaunty; urgency=low

  * debian/control:
    - Add versioned dependency for libvdpau.


---

### Post by plun on 2009-01-08
Well... according to Murphys laws...

**ver 180.22 stable** is out...:D

32 bit
[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)

64 bit
[http://www.nvidia.com/object/linux_display_amd64_180.22.html](http://www.nvidia.com/object/linux_display_amd64_180.22.html)


It might be a mess with Ubuntus and the ppa drivers.

Rock solid and no freezes for the moment....

---

### Post by Nullack on 2009-01-10
I tried installing the repos nvidia 180 driver but it failed into a mess.

Im manually running the stable 180.22 driver in the meantime before its sorted out. Xorg.conf still requires the ignore ABI version entry.

---

### Post by Twitch6000 on 2009-01-10
how to uninstall 180.17 manually so I can then install 180.22

---

### Post by LordVeovis on 2009-01-11
> **Twitch6000 said:**
> how to uninstall 180.17 manually so I can then install 180.22

I believe you have to add the PPAs for this.  Please look at the x-server breakage thread to get the location.

---

### Post by LordVeovis on 2009-01-11
> **autocrosser said:**
> I just got updates & the path was clear--updated Xorg (all of it) & the driver 180.16 was unblocked...using PPA:

#Restricted PPAs for .28 Kernel
deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main

180.16 driver installed without problems--just added the:

Section "ServerFlags"
Option "IgnoreABI"      "True"
EndSection

as per dinxter's fix.

:popcorn: :guitar: :):):)

Here ya go!

---

### Post by taavikko on 2009-01-11
> **plun said:**
> Yup...this photo shows my Acer Laptop...

Then it also depends where you have your "thumb in the hand" ;-), it might be a good idea to let someone which knows how do the job clean a laptop.....:D

Good Luck...!

Offtopic->
Thanks, Meant by asking, that anyone who's ever opened a laptop, knows it is pain in the a**

Much to my suprise, after opening/dismantling the box, the amount of dust inside, zero to none ??
so the issue lies somewhere else, and it's up to tech guys to work their magic...

---

### Post by plun on 2009-01-11
> **taavikko said:**
> Offtopic->
Thanks, Meant by asking, that anyone who's ever opened a laptop, knows it is pain in the a**

Much to my suprise, after opening/dismantling the box, the amount of dust inside, zero to none ??
so the issue lies somewhere else, and it's up to tech guys to work their magic...

OK...  you posted it within a nVidia thread and its important that these users also visits a support site.. it might be broken GPU chips

[http://en.community.dell.com/blogs/direct2dell/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx](http://en.community.dell.com/blogs/direct2dell/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx)

HP and Lenovo is the same...

---

### Post by ShirishAg75 on 2009-01-11
Btw the nvidia 180.22 is in the [NEW]("https://edge.launchpad.net/ubuntu/jaunty/+queue") queue . Should have it in a day or two. 

The changes file for amd64 and i386 archs. 

[http://launchpadlibrarian.net/21067507/nvidia-graphics-drivers-180_180.22-0ubuntu2_amd64.changes](http://launchpadlibrarian.net/21067507/nvidia-graphics-drivers-180_180.22-0ubuntu2_amd64.changes)

[http://launchpadlibrarian.net/21067459/nvidia-graphics-drivers-180_180.22-0ubuntu2_i386.changes](http://launchpadlibrarian.net/21067459/nvidia-graphics-drivers-180_180.22-0ubuntu2_i386.changes)

---

### Post by ubername on 2009-01-11
Hi all

I am looking for the simplest HOWTO to get Nvidia working with Jaunty. Looking at these posts it seems it is possible, but my *nix knowledge (or Ubuntu knowledge) isn't up to snuff. I have downloaded NVIDIA-Linux-x86_64-180.22-pkg2.run and I know how to edit xorg.conf, but I don't know how to close X server. A real dummies guide would be welcome.

TIA

---

### Post by LordVeovis on 2009-01-11
> **ubername said:**
> Hi all

I am looking for the simplest HOWTO to get Nvidia working with Jaunty. Looking at these posts it seems it is possible, but my *nix knowledge (or Ubuntu knowledge) isn't up to snuff. I have downloaded NVIDIA-Linux-x86_64-180.22-pkg2.run and I know how to edit xorg.conf, but I don't know how to close X server. A real dummies guide would be welcome.

TIA

xorg.conf is located in /etc/  edit it with your favorite editor (as root) and add the lines as mentioned in the x server breakage post.  that is the post you want to read to get it up and running.  If it is beyond you, you may want to familiarize yourself with Linux / Ubuntu a little bit more before jumping into an alpha.  If you really want to go forward, here is the link: [http://ubuntuforums.org/showthread.php?t=1011847](http://ubuntuforums.org/showthread.php?t=1011847)

You need to add the ignore abi command from one of the posts into that xorg.conf file.  Since you have the 180.22 you should be ok without the repositories.

---

### Post by ronacc on 2009-01-11
I have the repo 180.18 driver installed and noticed that I cak't kill X with ctrl>alt> bkspc  and I do have option "DontZap"  "true"  in my xorg.conf . any idea why?

---

### Post by Nullack on 2009-01-11
Ronacc, I think Byrce dud that on purpose.

For the other person asking how I installed the stable .22, I downloaded it from NVIDIA and installed it manually. I do not recommend this process as it detracts from testing efforts in Ubuntu but due to my video setup I needed the .22 revision so it forced my hand. I personally am reluctant to use PPAs.

---

### Post by ShirishAg75 on 2009-01-11
same here (reluctant to use PPAs)

---

### Post by ubername on 2009-01-15
Here's what I did, following advice from 

[http://ubuntuforums.org/showthread.php?t=1011847](http://ubuntuforums.org/showthread.php?t=1011847)
and other threads

1. add

deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main

to your software sources (system>administration> software sources 'third party software' tab

2 Go to Synaptic package manager (system>administration>synaptic package manager)

select nvidia-glx-180 and all other items that this tells you are required.
Also add compizconfig-settings-manager and simple-ccsm if you want compiz.

3. Edit you etc/X11/xorg.conf to look similar to this:

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection



4. Go to System>Preferences> Appearance 'Visual Effects' tab and select 'custom' (or 'extra' if 'custom' does not show.)

5. Reboot.

6. Go and play in CSSM and simple-ccsm (Compiz Config Settings Manager) which appear in System>Preferences> if you have them installed, otherwise get them from synaptic. compizconfig-settings-manager and simple-ccsm are the package names, if you didn't do that in step2 above.

7 If needs be do
compiz --replace 
from a terminal


Seems to work for me. Sorry if I am restating the obvious to people, and sometimes using sledgehammers to crack nuts, but at least I have it working now.

Now to fix my sound!

---

### Post by RAOF on 2009-01-15
Note that both the PPA and the IgnoreABI option are **no longer needed**.  The version of nvidia-glx-180 in the archives now officially supports our X server.

**EDIT:** only one part of this is incorrect.  You still need the IgnoreABI option!  My bad!

---

### Post by Gina on 2009-01-15
Good - thank you for telling us :)

---

### Post by minisori on 2009-01-15
I still need the IgnoreABI :confused:

---

### Post by stefangr1 on 2009-01-15
Yep, it's really improved a lot. Last time, I could play only the provided example movies, but this time quite some of the movies I have worked, including ALL movies I encoded using mencoder!

---

### Post by mgsfan on 2009-01-15
I still need the ignoreabi as well

---

### Post by RAOF on 2009-01-15
Eeep!  Sorry.  I'd removed the IgnoreABI line from my xorg.conf a number of days ago, but hadn't actually restarted X since then!

IgnoreABI *is* still needed.

---

### Post by DeeZiD on 2009-01-15
Anyway - this driver (v.180.22) is amazing.
KDE 4.2 works incredibly well! 
Even Smooth Scrolling in Firefox with composite in KDE4.2 enabled is as smooth as it should be :KS

(still not usable with catalyst 8.12 on a radeon 4850 when composite is enabled...)


Dennis

---

### Post by minisori on 2009-01-16
> **RAOF said:**
> Eeep!  Sorry.  I'd removed the IgnoreABI line from my xorg.conf a number of days ago, but hadn't actually restarted X since then!

IgnoreABI *is* still needed.

lol, i was shocked, since those were exactly the same drivers i was using already from nvidia install :P

---

### Post by garba on 2009-01-16
> **DeeZiD said:**
> Anyway - this driver (v.180.22) is amazing.
KDE 4.2 works incredibly well! 
Even Smooth Scrolling in Firefox with composite in KDE4.2 enabled is as smooth as it should be :KS

(still not usable with catalyst 8.12 on a radeon 4850 when composite is enabled...)


Dennis

what about windows resizing? im running the 180.20 version on hardy but resizing windows on kde 4.1 is still choppy as hell sigh not to mention the flickering

---

### Post by ubername on 2009-02-07
Hi

I am using nvidia-glx-180 from the standard repos, and have xorg.comf like this:

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "false"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "Module"
Load "glx"
Disable "dri2"
EndSection

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection

When I try to enable visual effects the system seems to hang. I get my desktop background and the rolling cursor indicating activity. If I move my mouse around, I can see that the rolling cursor changes to the ordinary mouse pointer outside of an area that is probably the same size as the 'enable visual effects' window (but the window isn't shown). If I then power off and restart I get back my desktop but no visual effects. Any clues?

TIA

---

### Post by plun on 2009-02-07
> **ubername said:**
> Hi

When I try to enable visual effects the system seems to hang. I get my desktop background and the rolling cursor indicating activity. If I move my mouse around, I can see that the rolling cursor changes to the ordinary mouse pointer outside of an area that is probably the same size as the 'enable visual effects' window (but the window isn't shown). If I then power off and restart I get back my desktop but no visual effects. Any clues?

TIA

For the moment it seems that we have a "brown bag" within latest Xorg.

Please also see this thread, it works
[http://ubuntuforums.org/showthread.php?t=1061919](http://ubuntuforums.org/showthread.php?t=1061919)

I have been testing and its just a mess... I have Compiz from source
and also uninstalled Ubuntus nVidia driver and checked it with the driver from nVidia.

Also recompiled Compiz with no success so we probably got a Xorg bug.
GDM > restart also hard crashes Xorg with a total freeze....

Just to make the best out of it...;)

---

### Post by ubername on 2009-02-10
Latest updates have fixed this for me. I can use the main repository software for nvidia and compiz works out of the box.

---

