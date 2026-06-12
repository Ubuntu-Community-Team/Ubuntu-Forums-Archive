---
title: "No GMA 500(PSB) Support in 9.10 Is this True?"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sammyboy405 on 2009-08-09
I Came Across this
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html)


> I'm quite sorry to say that the Poulsbo drivers will not be in Karmic
Koala. The Poulsbo chipset has a proprietary section to the driver and
Intel has said they are not supporting Karmic Koala, so its out of my hands.

Cheers,

David


This makes me Very Sad. There are so Many Netbooks out there that have the GMA500 in it. I was really hoping when I first Heard that 9.10 would have Better support for Intel PSB / 500 That Finally You could run Ubuntu with out doing a Song and Dance to get it to work.

---

### Post by overdrank on 2009-08-09
Moved to Karmic Koala Testing and Discussion

---

### Post by sammyboy405 on 2009-08-09
> **overdrank said:**
> Moved to Karmic Koala Testing and Discussion

Oh Sorry about that.

Anyways.. How about this folks? Is my netbook doomed to be stuck on 9.04 / 8.04?

---

### Post by skierkyles on 2009-08-09
Do you have compiz/3D on 9.04 or 8.04, or even anything else?

Edit: 
Nvm just saw your guide

---

### Post by Starks on 2009-08-10
This news sucks.

Karmic is supposed to be netbook friendly and it pains me to see Intel screwing a niche percentage of their clientèle.

---

### Post by andrewabc on 2009-08-10
Umm, GMA 500 was not developed by intel, and thus not same as other stuff. I thought people knew not to buy gma 500 netbooks if you plan on using linux?

If you do your research, says so on wiki article
[http://en.wikipedia.org/wiki/Intel_GMA#GMA_500](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500)

So stay away from gma 500.

Sounds great (specs), but not supported by any(?) linux distro :(

---

### Post by xens on 2009-08-10
this article describe the problem...

[http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg](http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg)

It's a shame from intel...

---

### Post by kingborel on 2009-08-10
> **Starks said:**
> This news sucks.

Karmic is supposed to be netbook friendly and it pains me to see Intel screwing a niche percentage of their clientèle.

And it is, if you didnt get one with a chip that Intel doesn't support

---

### Post by sammyboy405 on 2009-08-10
The GMA500 May not of been Created by Intel. Most everyone knows that. However, Intel is the one who bought the Knowledge from Imgtek there for should support it. After all it has Intels name all over it.

Im just hoping someone out there that has some knowledge of how drivers work and whatnot can create some sorta way around this so 9.10 will be more netbook friendly.  A Nice Chuck of netbooks out there Use the PSB/GMA500 . 

Then again I Know the Flip side is the Majority of thoses users dont use Ubuntu I Know.   

and the Re-Flip side to that is Maybe if Ubuntu where able to fix this issue with the PSB/GMA500 We would have more of a userbase on Netbooks.

A little Devils Advocate there..  But I See both sides of the story.  Im just a little bummed that I wont be able to use my netbook on 9.10

---

### Post by andrewabc on 2009-08-10
@ people blaming ubuntu or wanting them to fix it:

I don't see how ubuntu can fix gma500 when it is intels fault, and the people responsible for drivers (for all distributions) would have to implement it. I don't think intel drivers are made by canonical employees, so nothing ubuntu can do about it.

---

### Post by sammyboy405 on 2009-08-11
What About xorg.  xorg makes Open source type drivers.
[http://www.mydellmini.com/forum/dell-mini-10-discussion/11501-has-intel-abandonned-poulsbo-chipset.html](http://www.mydellmini.com/forum/dell-mini-10-discussion/11501-has-intel-abandonned-poulsbo-chipset.html)

was mentioned in that forum.

---

### Post by xens on 2009-08-11
Some news for fedora users, still no luck for ubuntu users :(

[http://www.phoronix.com/scan.php?page=news_item&px=NzQ0NA](http://www.phoronix.com/scan.php?page=news_item&px=NzQ0NA)

Hope next Intel GPU'll sucks less...

---

### Post by lucazade on 2009-08-12
I've patched the Psb kernel module to make it work on 2.6.31-5..
Haven't tried it on my poulsbo device yet but only to compile the module locally.

To be used with the ubuntu-mobile-ppa for jaunty.
I'll try to upload it on my ppa repository asap.

let me know if ok!

kernel patch from: [http://ubuntuforums.org/showthread.php?p=7680966](http://ubuntuforums.org/showthread.php?p=7680966)

---

### Post by kingborel on 2009-08-12
> **sammyboy405 said:**
> What About xorg.  xorg makes Open source type drivers.
[http://www.mydellmini.com/forum/dell-mini-10-discussion/11501-has-intel-abandonned-poulsbo-chipset.html](http://www.mydellmini.com/forum/dell-mini-10-discussion/11501-has-intel-abandonned-poulsbo-chipset.html)

was mentioned in that forum.

Yes, which works best when the manufacturer releases the specs and things needed to develop the drivers. Otherwise, it's just a guessing game trying to reverse-engineer drivers

---

### Post by cdufour on 2009-08-13
Good news!

GMA500 (on Asus T91) works On Ubuntu 9.04/Jaunty with Ubuntu linux-image-2.6.31-5-generic (from 9.10/Karmic) and psb-kernel-source from Lucazade (THANX MAN!)

In summary:
 - Install Poulsbo drivers according to [http://ubuntuforums.org/showthread.php?t=1213416](http://ubuntuforums.org/showthread.php?t=1213416) (but do NOT install the proposed psb-kernel-* packages)
 - AND use the psb-kernel-* packages from [http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13](http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13)
 - AND add the following in your /etc/X11/xorg.conf[INDENT]```
Section "Device"
  Identifier "GMA500"
  Driver "psb"
  Option "MigrationHeuristic" "greedy"
  Option "IgnoreACPI" "yes"
EndSection
```[/INDENT]Issues:
 - No more /proc/acpi/video entry (?!?...), thus the "IgnoreACPI" option above
 - Keyboard brightness control (Fn+F3/F4) doesn't work anylonger once X has started (but does work through Gnome applet)

Pros of 2.6.31 (OT, but worth mentioning for Asus T91 users):
 - The Asus Super Hybrid Engine can now be controlled via /sys/devices/platform/eeepc/cpufv (since 2.6.30, actually)
 - WLAN on/off status can now be controlled via /sys/devices/platform/eeepc/rfkill/rfkill0/state (and with Fn+F2 key)
 - Bluetooth on/off status can now be controlled via /sys/devices/platform/eeepc/rfkill/rfkill1/state (and with Fn+F2 key)

Also:
 - Suspend (to RAM) works
 - glxgears (fullscreen @ 1024x600) reports 115 FPS (with occasional glitches)
 - flash movie ([http://tsr.ch](http://tsr.ch) 19:30 news) is not smooth, but watchable (with cpufv=0, governor=ondemand)
 - HD movie (Big Buck Bunny MP4 @ 1080p) is not watchable (even with cpufv=0, governor=ondemand)
 - SD movie (Big Buck Bunny MP4 @ 720p) is (really!) smooth (with cpufv=2, governor=powersave)
 - Unable to verify whether the USB/3D-driver occasional freezes still happen
   (nothing happened while performing the tests mentioned here, including transfering >1GB of movie to the SD card in the USB-driven slot)

---

### Post by lucazade on 2009-08-13
I'm glad to hear it works for you on Jaunty 2.6.31-5!
On karmic there is an issue with libdrm-poulsbo to make it work properly.. i'll see if i can do anything in the next days.

---

### Post by cdufour on 2009-08-13
About the missing /proc/acpi/video directory

Looking at [http://lxr.linux.no/linux+v2.6.30/drivers/acpi/video.c#L2336](http://lxr.linux.no/linux+v2.6.30/drivers/acpi/video.c#L2336) - ACPI Video code as per kernel 2.6.30, where /proc/acpi/video seems to have gone missing (cf. tested 2.6.30 mainline PPA kernel) - explains the disappearance: GMA500 is reported as an Intel VGA device, which prompts the ACPI Video to skip the registration.

The following (quick and dirty) patch solves the issue:[INDENT]```
--- linux-2.6.31/drivers/acpi/video.c.orig    2009-08-13 22:59:13.000000000 +0200
+++ linux-2.6.31/drivers/acpi/video.c    2009-08-13 23:00:06.000000000 +0200
@@ -2391,8 +2391,8 @@
 {
     dmi_check_system(video_dmi_table);
 
-    if (intel_opregion_present())
-        return 0;
+//    if (intel_opregion_present())
+//        return 0;
 
     return acpi_video_register();
 }

```[/INDENT]The /proc/acpi/video directory then re-appears, and the "IgnoreACPI" option can be removed from /etc/X11/xorg.conf

TO BE CLARIFIED: does this behavior occurs only when using 2.6.31 on 9.04/Jaunty (my setup), or does it also occur in 9.10/Karmic?

Also, once X started, the LCD brightness MUST be modified via XRandR:[INDENT]```
xrandr --output LVDS0 --set BACKLIGHT <value between 0 and 100>
```(iow. /proc/acpi/video/GFX0/LCDD/brightness won't work)
[/INDENT]Hope this helps ;-)

---

### Post by sammyboy405 on 2009-08-13
Unrelated to 9.10 but thanks for the info on getting gma500 to work on 9.10

in fact your information has helped me fix 9.04 Lock up issues while using 3d.

xorg.conf file needs this.
```
  Option "IgnoreACPI" "yes"

```

Throw that in there and Lockups magically disappear.!

---

### Post by xens on 2009-08-13
thanks for your work lucazade!

I'll try this on the netbook of one of my friend, hope to see a simpler solution from canonical until the final karmic!

Romain

---

### Post by lucazade on 2009-08-14
> **cdufour said:**
> 
TO BE CLARIFIED: does this behavior occurs only when using 2.6.31 on 9.04/Jaunty (my setup), or does it also occur in 9.10/Karmic?


This behavior occurs with both Jaunty and Karmic (missing /proc/acpi/video directory).

In Karmic there is something different in the drm management (don't know if depends on drm.ko or libdrm.so or other) so it fails to load (i haven't got the netbook here to try it now and to report the dmesg errors)

---

### Post by lucazade on 2009-08-14
just fyi there are other 2 repository for poulsbo:
[https://launchpad.net/~dobey/+archive/ppa](https://launchpad.net/~dobey/+archive/ppa)
[https://launchpad.net/~albertomilone/+archive/poulsbo-graphics](https://launchpad.net/~albertomilone/+archive/poulsbo-graphics)

i've used libdrm-poulsbo-2.3.0-0ubuntu3netbook7 from Milone's ppa on karmic because the ubuntu-mobile one was not installable (dependencies problem).

---

### Post by Svartalf on 2009-08-14
> **andrewabc said:**
> Umm, GMA 500 was not developed by intel, and thus not same as other stuff. I thought people knew not to buy gma 500 netbooks if you plan on using linux?

The largest issue is that the bulk of the newer netbooks happen to sport this stupid GPU.  Everything worth having in the netbook space has it.

If it weren't for my policy of ascribing group stupidity to things instead of malice aforethought, I'd almost say there was a fix in on things in this space.  Not that the ARM story's going to be any better.  Unless Qualcomm's giving us good drivers or tech info to make 'em, we're going to be very stuck with what Imagination gives to TI and then TI cautiously doles out on the 3D support front.  And it's not all rosy there either right at the moment.  X11 and ES don't get along all too well with the current drivers.  Hope holds out that ImgTec will get it straightened out or that someone will manage to get enough DirectFB 1.4/1.5 driver support in there to make it work nicer.

---

### Post by TrueTom on 2009-08-14
Good luck with Gnome 3 on this machine... :P

---

### Post by Svartalf on 2009-08-14
> **sammyboy405 said:**
> I Came Across this
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html)




This makes me Very Sad. There are so Many Netbooks out there that have the GMA500 in it. I was really hoping when I first Heard that 9.10 would have Better support for Intel PSB / 500 That Finally You could run Ubuntu with out doing a Song and Dance to get it to work.

Which goes to show [this is thoroughly true]("http://www.phoronix.com/scan.php?page=article&item=850&num=1")...  Unfortunately, that claim also makes this revelation highly ironic at the same time.  Closed source doesn't work in the big picture scheme of things.  Intel should've known better and DONE better.

---

### Post by excogitation on 2009-08-18
So is it now also working with Karmic?

---

### Post by lucazade on 2009-08-18
No, no way to make it work on Karmic atm... :(

---

### Post by Starks on 2009-08-18
> **Svartalf said:**
> Which goes to show [this is thoroughly true]("http://www.phoronix.com/scan.php?page=article&item=850&num=1")...  Unfortunately, that claim also makes this revelation highly ironic at the same time.  Closed source doesn't work in the big picture scheme of things.  Intel should've known better and DONE better.
PowerVR has a long-running hostility towards FLOSS.

---

### Post by cdufour on 2009-08-19
> **Starks said:**
> PowerVR has a long-running hostility towards FLOSS.

Then I'll do what I have already done a few years ago with ATI (for their Linux driver really gave me too much trouble): stay away from their products! Meaning my own computers (~5 since that decision) and all (Linux) workstations where I work (~100 PCs, with a 3-year average lifetime) are equipped with nVidia, as well as all PCs I recommended to my Linux-interested co-workers. :-P

---

### Post by bodhi.zazen on 2009-08-21
> **lucazade said:**
> No, no way to make it work on Karmic atm... :(

I can not get it working on 9.10 Alpha either.

Hoping there is a fix soon as the newer kernels are better.

---

### Post by jbernardo on 2009-08-26
Any news on poulsbo support on karmic? I'd really like to remove XP from the asus 1101HA I just got.
Thanks!

---

### Post by excogitation on 2009-08-26
> **bodhi.zazen said:**
> 
Hoping there is a fix soon as the newer kernels are better.

Unfortunately I can't say that. I'm getting hard lockups on my P11z after leaving it idle for some time.

---

### Post by Leed on 2009-08-28
Can't we just have it as proprietary driver? Like many other hardware drivers in Ubuntu?

I got the driver running from the backport repos in Jaunty, will that not be available in Karmic anymore?

---

### Post by bodhi.zazen on 2009-08-28
> **Leed said:**
> Can't we just have it as proprietary driver? Like many other hardware drivers in Ubuntu?

I got the driver running from the backport repos in Jaunty, will that not be available in Karmic anymore?

Do you mind posting detailed instructions on how you did that on Karmic (Ubuntu 9.10) ?

I have tried but can not enable the psb driver in Ubuntu Karmic (9.10 alpha).

But yes, if it works as a back port there is no problem. Otherwise we rely on people who maintain the ppa provide an updated driver for Karmic (9.10).

So there is a difference between "official" support (provided by Canonical), which is not possible as the driver is closed source, an availability via 3rd party options, such as a ppa or other 3rd party repos.

---

### Post by Leed on 2009-08-28
sorry, not Karmic, it's Jaunty I use and that's why I'm interested in knowing if that "trick" will still work with Karmic.

Instructions were taken from 
[http://www.hilbig.id.au/t91/index.html](http://www.hilbig.id.au/t91/index.html)

---

### Post by jbernardo on 2009-08-29
> **Leed said:**
> sorry, not Karmic, it's Jaunty I use and that's why I'm interested in knowing if that "trick" will still work with Karmic.

Instructions were taken from 
[http://www.hilbig.id.au/t91/index.html](http://www.hilbig.id.au/t91/index.html)

Well, even in Jaunty the support is woefully incomplete - no 3D, compositing is broken (no screen effects with kde), etc. If the GMA500 driver for windows XP wasn't also very bad, some people would be crying "conspiracy" by now.

---

### Post by bodhi.zazen on 2009-08-29
> **jbernardo said:**
> Well, even in Jaunty the support is woefully incomplete - no 3D, compositing is broken (no screen effects with kde), etc. If the GMA500 driver for windows XP wasn't also very bad, some people would be crying "conspiracy" by now.

compositing works fine in XFCE. compositing is built into xfce so not need for compiz (I only use transparency).

---

### Post by taavikko on 2009-08-29
> **bodhi.zazen said:**
> compositing works fine in XFCE. compositing is built into xfce so not need for compiz (I only use transparency).

But what about us GNOME users?
Well, we can resort to use metacity and compositing.
```
gconftool-2 --set /apps/metacity/general/compositing_manager --type bool true
```

---

### Post by bodhi.zazen on 2009-08-29
Thanks, that is a nice tip. I do not use gnome enough to know all it's rich features.

So is it only KDE that is out of luck ?

Hopefully a KDE master will weigh in.

---

### Post by taavikko on 2009-08-29
> **bodhi.zazen said:**
> Thanks, that is a nice tip. I do not use gnome enough to know all it's rich features.

So is it only KDE that is out of luck ?

Hopefully a KDE master will weigh in.

Not an KDE master, but AFAIK kwin has this build-in as long as direct rendering is working.
Running KDE on my Desktop unit but it has nvidia binary blob installed.

---

### Post by Leed on 2009-08-30
the psb drivers from ubuntu-mobile (mentioned in the site I linked to above) do support 3d, I can get compiz-fusion running normally on my t91. You have to add psb to the whitelist in the compiz config file. It's not the best in performance I've ever seen, but its sure ok.

The only pain is that you have to manually add the driver source to the kernel after each release.

---

### Post by jbernardo on 2009-08-30
> **Leed said:**
> the psb drivers from ubuntu-mobile (mentioned in the site I linked to above) do support 3d, I can get compiz-fusion running normally on my t91. You have to add psb to the whitelist in the compiz config file. It's not the best in performance I've ever seen, but its sure ok.

AFAIK, compiz can work without composite/3D, using the CPU for the efects. Kwin can't - uses OpenGL or XRender; the first seems to not be fully supported, the second even less, at least using kwin diagnostics.

---

### Post by psyke83 on 2009-08-30
> **taavikko said:**
> Not an KDE master, but AFAIK kwin has this build-in as long as direct rendering is working.
Running KDE on my Desktop unit but it has nvidia binary blob installed.

If the poulsbo driver supports the Composite/RENDER extension, then you may be able to get compositing working. In KWin there are two compositing engines - OpenGL (chosen by default) and XRender. The XRender engine may work, so find it in the preferences and change to that.

Another option is to use xcompmgr (which is quite basic).

---

### Post by jbernardo on 2009-08-30
The driver claims to support the Composite extension, but kwin disagrees. Trying to use OpenGL for the effects just shows black squares (where windows should be) on a white background, choosing XRender fails immediately.

---

### Post by psyke83 on 2009-08-30
> **jbernardo said:**
> The driver claims to support the Composite extension, but kwin disagrees. Trying to use OpenGL for the effects just shows black squares (where windows should be) on a white background, choosing XRender fails immediately.

Try installing xcompmgr and running it from the terminal without any options. If that fails, try:

```
$ xcompmgr -a
```

---

### Post by jbernardo on 2009-08-30
No luck. Every time I try to enable kwin effects, this is what I get:
```
$ xcompmgr
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 15052 requests (15052 known processed) with 0 events remaining.
$ xcompmgr -a
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 42 requests (42 known processed) with 0 events remaining.
```

---

### Post by psyke83 on 2009-08-30
Well then I guess it's time to buy new hardware :). It seems that the driver doesn't support even the most basic compositing.

---

### Post by jbernardo on 2009-09-02
> **psyke83 said:**
> Well then I guess it's time to buy new hardware :). It seems that the driver doesn't support even the most basic compositing.

The hardware is new... And it seems it all works well in Hardy. It is just that Intel doesn't seem to be able to get PowerVR to provide them with a updated driver, even the XP drivers are crap.

Anyway, I am using Marko Helenius' [howto]("http://ubuntuforums.org/showthread.php?p=7885128"), will see if the "section DRI" makes any difference to the outcome.

---

### Post by Kazade on 2009-09-02
Just wondering, is there an attempt at an open source driver for this GPU underway anywhere?

---

### Post by gururise on 2009-09-22
Any updates on the GMA500 (Poulsbo) driver front?  Many of the new netbooks being released now sport this chipset.  Will Ubuntu 9.10 really be unusable on nearly half the available netbooks when its released?

Intel are able to release new Vista/Win7 drivers, I'm sure if they really wanted to, they could get some updated Linux drivers too. Perhaps someone with connections inside Intel can help move things along.

---

### Post by TrueTom on 2009-09-22
> **gururise said:**
> Any updates on the GMA500 (Poulsbo) driver front?  Many of the new netbooks being released now sport this chipset.  Will Ubuntu 9.10 really be unusable on nearly half the available netbooks when its released?

Intel are able to release new Vista/Win7 drivers, I'm sure if they really wanted to, they could get some updated Linux drivers too. Perhaps someone with connections inside Intel can help move things along.

The chip isn't made by Intel, therefore you're out of luck.

---

### Post by excogitation on 2009-09-22
> **gururise said:**
> Any updates on the GMA500 (Poulsbo) driver front?

You can get it working:
[http://ubuntuforums.org/showthread.php?t=1253406]("http://ubuntuforums.org/showthread.php?t=1253406")

---

### Post by teatimest on 2009-09-22
That's the curse of Poulsbo.... by imagenation technologies.

---

### Post by AdamWill on 2009-09-24
lucazade: a note: you've been versioning your 'lucazade' PPA packages wrong. When you update your package, you're bumping the version that should apply to the *upstream code*, not your package. So you uploaded your first psb driver package as 0.32.0, your second as 0.33.0, your third as 0.34.0 and so on. This is wrong and confusing and led me to think for a while that Intel had been releasing newer versions of the driver somewhere that I was missing. :) 

You should be bumping the versions at the end of the name - the -0ubuntu1~910um1 stuff. I'm not sure which of those numbers you should increment, as I'm not familiar with Ubuntu packaging conventions, but you definitely shouldn't be bumping the version of the upstream source. Thanks :)

---

### Post by AdamWill on 2009-09-24
> **cdufour said:**
> About the missing /proc/acpi/video directory

Looking at [http://lxr.linux.no/linux+v2.6.30/drivers/acpi/video.c#L2336](http://lxr.linux.no/linux+v2.6.30/drivers/acpi/video.c#L2336) - ACPI Video code as per kernel 2.6.30, where /proc/acpi/video seems to have gone missing (cf. tested 2.6.30 mainline PPA kernel) - explains the disappearance: GMA500 is reported as an Intel VGA device, which prompts the ACPI Video to skip the registration.

The following (quick and dirty) patch solves the issue:[INDENT]```
--- linux-2.6.31/drivers/acpi/video.c.orig    2009-08-13 22:59:13.000000000 +0200
+++ linux-2.6.31/drivers/acpi/video.c    2009-08-13 23:00:06.000000000 +0200
@@ -2391,8 +2391,8 @@
 {
     dmi_check_system(video_dmi_table);
 
-    if (intel_opregion_present())
-        return 0;
+//    if (intel_opregion_present())
+//        return 0;
 
     return acpi_video_register();
 }

```[/INDENT]The /proc/acpi/video directory then re-appears, and the "IgnoreACPI" option can be removed from /etc/X11/xorg.conf

TO BE CLARIFIED: does this behavior occurs only when using 2.6.31 on 9.04/Jaunty (my setup), or does it also occur in 9.10/Karmic?

Also, once X started, the LCD brightness MUST be modified via XRandR:[INDENT]```
xrandr --output LVDS0 --set BACKLIGHT <value between 0 and 100>
```(iow. /proc/acpi/video/GFX0/LCDD/brightness won't work)
[/INDENT]Hope this helps ;-)

Hi, folks. For anyone who doesn't know, I'm Adam Williamson, I maintain a port of the Ubuntu psb driver over to Fedora for Fedora users, you may have seen some of my Poulsbo-related posts on my [blog](http://www.happyassassin.net).

So the above stuff piqued my interest, as I've always needed the IgnoreACPI thing on my Fedora builds, so I followed it up a bit.

The opregion patch comes from Matthew Garrett. It catches the GMA 500 chips because all it does is look for any Intel graphics adapter (as you can see if you follow its logic). I asked Matthew about this problem, and this is what he said:

<mjg59> adamw: It looks like it implements opregion, to be honest
<mjg59> adamw: In which case the workaround is correct, but the poulsbo DRM
driver is deficient

(...confirmatory diagnosis)

<mjg59> adamw: Would actually be pretty easy - you just need to pull in the
intel opregion code from the i915 drm, and change the backlight register writes
<mjg59> Oh, and add support to the interrupt handler
<mjg59> I've no idea how poulsbo would doorbell
<mjg59> adamw: 0x7f6a3010 (the contents of PCI conf register 0xfc on your
device) is ACPI non-volatile storage
<mjg59> adamw: So it certainly looks like opregion. You get to keep both
pieces.
<mjg59> The kernel behaviour is correct, the poulsbo DRM is just ****. Sorry.
<mjg59> adamw: Heh. The opregion spec is open and downloadable from the Intel graphics site somewhere. Beyond that, 8ee1c3db9075cb3211352e737e0feb98fd733b20 is basically what you want to implement in the Poulsbo DRM
<mjg59> The interrupt setup will be different, and the registers that you have to write to for the backlight update will be different. But beyond that, it should just work.

So it is actually technically correct that GMA 500 chips get caught by this workaround, but the psb kernel module should be patched to add opregion support. Matthew provided some pointers above as to how this should be done; for a sufficiently skilled hacker with access to the hardware it should be quite easy, apparently. I am nowhere near being such a thing, though, so all I can do is point up the issue and hope someone else can do it :)

---

### Post by lucazade on 2009-09-24
> **AdamWill said:**
> lucazade: a note: you've been versioning your 'lucazade' PPA packages wrong. 

Hi AdamWill! I know my versioning was wrong but at that moment I was only trying to get the whole working in a single ppa :) 
(btw i wasn't able to compile the xorg driver in the ppa repo but only locally)

I hope as well to find a "sufficiently skilled hacker" to fix these terrible drivers :)

---

### Post by jack_mcdowell on 2009-09-25
Is there added support in the 2.6.31-11 kernel or should I rebuild it like I did the 10 version? Thanks, Jack

---

### Post by excogitation on 2009-09-26
> **jack_mcdowell said:**
> Is there added support in the 2.6.31-11 kernel or should I rebuild it like I did the 10 version? Thanks, Jack

reinstall psb-kernel-source
(I only managed to get it to work by reinstalling that from 2.6.31-11's recovery console: "dpkg -i psb-kernel-source_4.41.2-0ubuntu1~910um1_all.deb")

---

### Post by argor on 2009-09-28
> **jbernardo said:**
> The hardware is new... And it seems it all works well in Hardy. It is just that Intel doesn't seem to be able to get PowerVR to provide them with a updated driver, even the XP drivers are crap.

well the problem is Intel is not using driver writing by powervr but by Tungsten graphics and Word has it that Tungsten isn't using the onboard firmware of the chip and it naturally falls back to software rendering.
[http://forum.beyond3d.com/showpost.php?p=1306944&postcount=35](http://forum.beyond3d.com/showpost.php?p=1306944&postcount=35)

---

### Post by dmitry.platonov on 2009-10-08
I propose start of reverse engineering effort to bring opensource GMA 500 support to Linux. Would anyone join?

---

### Post by jbernardo on 2009-10-08
> **dmitry.platonov said:**
> I propose start of reverse engineering effort to bring opensource GMA 500 support to Linux. Would anyone join?
  
I applaud the idea, unfortunately I am no coder. At most I can do testing...

---

### Post by dmitry.platonov on 2009-10-08
There are other tasks other than coding: research, wiki/svn/bugtracker/m-list setup, testing, packaging.
I have the hardware (Asus T91), but didn't  install linux [on it] yet.

---

### Post by zevans on 2009-10-08
I just had a look-see on Launchpad. The Canonical team are most definitely aware of these issues and are posting to the bugs there, so that's a good start. The master bug is in "wishlist" status so at least it hasn't been marked "WONTFIX" :-)

Does Ubuntu MOBLIN Netbook Remix support Phoronix? (This is not the same as plain Ubuntu Netbook Remix, it's a collaboration between Canonical and Intel)

---

### Post by zevans on 2009-10-08
Everyone on this thread should read 

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

This says it works, but it looks like there are some hoops to jump through.

---

### Post by lucazade on 2009-10-08
> **dmitry.platonov said:**
> There are other tasks other than coding: research, wiki/svn/bugtracker/m-list setup, testing, packaging.
I have the hardware (Asus T91), but didn't  install linux [on it] yet.

I would join this adventure, count on me!

---

### Post by dmitry.platonov on 2009-10-09
PM sent

---

### Post by ssombra on 2009-10-09
> **lucazade said:**
> I would join this adventure, count on me!

I am a final user (no coding or programming knowledge). If i can help doing something like testing count on me.

(dell mini 10)

---

### Post by dmitry.platonov on 2009-10-10
Ok, we'll announce once we have something to talk about

---

### Post by 31d1 on 2009-10-10
```

rupa@zoidberg:~/Downloads$ sudo dpkg -i psb-kernel-source_4.41.2-0ubuntu1~910um1_all.deb 
(Reading database ... 117331 files and directories currently installed.)
Preparing to replace psb-kernel-source 4.41.2-0ubuntu1~910um1 (using psb-kernel-source_4.41.2-0ubuntu1~910um1_all.deb) ...
Unpacking replacement psb-kernel-source ...
Removing old module source...
Setting up psb-kernel-source (4.41.2-0ubuntu1~910um1) ...
Loading new psb-kernel-source-4.41.2 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.41.2 does not exist.
dpkg: error processing psb-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 psb-kernel-source

```

I'm getting this error when trying to install (on karmic), using the instructions at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo). Any ideas?

---

### Post by jbernardo on 2009-10-11
> **31d1 said:**
> I'm getting this error when trying to install (on karmic), using the instructions at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo). Any ideas?
Try adding Lucazade's ppa:
```
deb http://ppa.launchpad.net/lucazade/gma500/ubuntu karmic main # lucazade psb kernel ppa
deb-src http://ppa.launchpad.net/lucazade/gma500/ubuntu karmic main # lucazade psb kernel ppa source

```

Instead of installing the DEBs directly, then after adding the PPA key and doing a apt-get update just try "sudo aptitude install psb-kernel-source". Then tell us the results so we can update the wiki... :)

---

### Post by 31d1 on 2009-10-11
**Edit:** Nevermind the below - looks like I can't compile anything with gcc, so something is broken outside of this...


Well, adding the PPA gets me farther, but I've still got problems:

```

Setting up psb-kernel-source (4.41.6-0ubuntu1~910um1) ...
Removing old psb-kernel-source-4.41.6 DKMS files...

------------------------------
Deleting module version: 4.41.6
completely from the DKMS tree.
------------------------------
Done.
Loading new psb-kernel-source-4.41.6 DKMS files...

Creating symlink /var/lib/dkms/psb-kernel-source/4.41.6/source ->
                 /usr/src/psb-kernel-source-4.41.6

DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-13-generic LINUXDIR=/lib/modules/2.6.31-13-generic/build DRM_MODULES=psb".......(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-13-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/psb-kernel-source/4.41.6/build/ for more information.
0
0
dpkg: error processing psb-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 psb-kernel-source

```

and here's the contents of make.log:

```
DKMS make.log for psb-kernel-source-4.41.6 for kernel 2.6.31-13-generic (i686)
Sun Oct 11 20:17:06 EDT 2009
sh ./create_linux_pci_lists.sh < ./drm_pciids.txt
make -C /lib/modules/2.6.31-13-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-13-generic'
/usr/src/linux-headers-2.6.31-13-generic/arch/x86/Makefile:80: stack protector enabled but no compiler support
  CC [M]  /var/lib/dkms/psb-kernel-source/4.41.6/build/drm_auth.o
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[2]: *** [/var/lib/dkms/psb-kernel-source/4.41.6/build/drm_auth.o] Error 1
make[1]: *** [_module_/var/lib/dkms/psb-kernel-source/4.41.6/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-13-generic'
make: *** [modules] Error 2

```

I did install build-essentials and a couple other packages that I thought might be necessary for this, but I still end up with this error.

---

### Post by loserveg on 2009-10-11
i can test as well (dell mini 10)

---

### Post by joey-elijah on 2009-10-11
Am i missing something? Compiz etc work fine in Karmic NBR...

---

### Post by cdufour on 2009-10-12
What about petitioning Intel?  So far, a bunch of excellent people are volunteering to hack their way though the available stuff to have it ported on newer versions of the kernel/distro (a big thanx to theim)... but in the long term, without support from the hardware vendor, they'll get stuck... and we (users) along.  A pity when considering the specs of this GPU, which ARE very good (look at the comparison table on [http://en.wikipedia.org/wiki/Intel_GMA#GMA_500](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500) ).  So, what do you think?  PS: I know Intel is not the producer... but I don't care. Officially, they are the vendor. Let THEM put pressure on the producer (well, let's try to...).

---

### Post by 31d1 on 2009-10-13
> **jbernardo said:**
> Try adding Lucazade's ppa:
```
deb http://ppa.launchpad.net/lucazade/gma500/ubuntu karmic main # lucazade psb kernel ppa
deb-src http://ppa.launchpad.net/lucazade/gma500/ubuntu karmic main # lucazade psb kernel ppa source

```

Instead of installing the DEBs directly, then after adding the PPA key and doing a apt-get update just try "sudo aptitude install psb-kernel-source". Then tell us the results so we can update the wiki... :)

OK, after reinstalling my system cause it was so massively broken, I can confirm that adding the PPA and following the instructions at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) worked nicely.

---

### Post by lokutus25 on 2009-10-14
I fell like I'm near the Finish line but something is missing. I installed psb-kernel-source from "http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu" (thx Alberto!) and it worked with kernel 2.6.31-11-generic on karmic. Now, after the upgrade to 2.6.31-13-generic gdm is no more working.
I'd like to try to install the lucazade work (thx Luca!) but I can't find the keys.
"apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30" is giving me keyserver error. Which is the right key? Where am I wrong?
BTW I have an eeePC 1101HA with Ubuntu Karmic.

---

### Post by AdamWill on 2009-10-14
dmitriy: you may want to contact Greg Kroah-Hartman at Novell, who started on a similar effort himself a while back, and Olivier Blin at Mandriva, who packages the psb driver for that distribution. I can provide their email addresses via PM if you like.

The kernel module and X driver that provide basic 2D functionality are already F/OSS. The proprietary package is xpsb-glx, which provides 3D acceleration and video playback acceleration functionality. That's what would need reverse engineering. The kernel module would also need to be improved to meet upstream standards so it could get into the upstream kernel, ideally.

I'm happy to help with testing and Fedora packaging of anything you come up with.

---

### Post by 31d1 on 2009-10-14
> **lokutus25 said:**
> I fell like I'm near the Finish line but something is missing. I installed psb-kernel-source from "http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu" (thx Alberto!) and it worked with kernel 2.6.31-11-generic on karmic. Now, after the upgrade to 2.6.31-13-generic gdm is no more working.
I'd like to try to install the lucazade work (thx Luca!) but I can't find the keys.
"apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30" is giving me keyserver error. Which is the right key? Where am I wrong?
BTW I have an eeePC 1101HA with Ubuntu Karmic.

The psb-kernel-source package uses dkms, and needs to get recompiled with every kernel upgrade. However, it is not set up to automatically install in its dkms.conf file, so when you get a new kernel, it won't compile itself automatically.

One workaround is: when you get a new kernel, 'sudo aptitude remove psb-kernel-source; sudo aptitude install psb-kernel-source', and it should compile for the new kernel.

As far as the apt-key error, the correct key will be reported and complained about when you do 'aptitude update'. Also, you must run apt-key as root or with sudo, maybe that's your problem, I don't know.

---

### Post by Jonathanius on 2009-10-14
> **lokutus25 said:**
> I fell like I'm near the Finish line but something is missing. I installed psb-kernel-source from "http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu" (thx Alberto!) and it worked with kernel 2.6.31-11-generic on karmic. Now, after the upgrade to 2.6.31-13-generic gdm is no more working.
I'd like to try to install the lucazade work (thx Luca!) but I can't find the keys.
"apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30" is giving me keyserver error. Which is the right key? Where am I wrong?
BTW I have an eeePC 1101HA with Ubuntu Karmic.

the key is 6699F3D9 (went to [https://launchpad.net/~lucazade/+archive/gma500](https://launchpad.net/~lucazade/+archive/gma500) and clicked "Technical details..." its the second part)[               ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x65EE4E74BF0DA88F4D1E7587F5F2A6FE6699F3D9&op=index")

---

### Post by lokutus25 on 2009-10-15
> **Jonathanius said:**
> the key is 6699F3D9 (went to [https://launchpad.net/~lucazade/+archive/gma500](https://launchpad.net/~lucazade/+archive/gma500) and clicked "Technical details..." its the second part)[               ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x65EE4E74BF0DA88F4D1E7587F5F2A6FE6699F3D9&op=index")

Here I am. Thanks all. I managed to remove all the previous *psb* and *poulsbo* package.
After a reboot and added the lucazade repo and updated the package list, I followd the [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) procedure.
I am receiving an error when I try to install the poulsbo-driver-2d package saying:
> 
The following packages have unmet dependencies:
  poulsbo-driver-2d: Depends: xserver-xorg-video-psb which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  poulsbo-driver-2d

Do you think it's possible?

---

### Post by lokutus25 on 2009-10-15
I forgot to mention that before to try, I upgraded the karmic to last packages release. This means kernel 2.6.31-14-generic. Not a good idea I guess but If I'm not wrong it shold work anyway using dkms.
Thx

---

### Post by lokutus25 on 2009-10-15
Ok...after removing, purging, cleaning and all I managed to install everything. Seems to works, at least the 2D, I'm not using compiz. glxgears say 900-1000 frames per secons. I'll write if I notice something very weird. Thanx you all.

---

