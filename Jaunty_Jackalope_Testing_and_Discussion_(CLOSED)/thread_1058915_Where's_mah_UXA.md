---
title: "Where's mah UXA?"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-03
According to Bryce and the Ubuntu-X team, UXA will not (as of this moment) be enabled in Jaunty by default due to reports of instability.

To enable it, you'll need to add a small entry in your xorg.conf Device section under the identifier.

```
    Option "AccelMethod" "UXA"
```

If you have enabled UXA, the team could really use your testimonials on performance and reports of any bugs you encounter. You can contact them in numerous ways with your reports:

[Ubuntu-X mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-x")
[Ubuntu-X on IRC]("irc://irc.freenode.net/ubuntu-x")
[Launchpad]("https://launchpad.net/~ubuntu-x-swat")

Note: It doesn't matter if you are using the official packaged Intel driver (2.6.0) or the [newer xorg-edgers PPA driver]("https://launchpad.net/~xorg-edgers/+archive") from Tormod Volden (2.6.99).

---

### Post by adult swim on 2009-02-03
I have an intel 945 gm running intel driver 2.6.99 and until I enabled uxa my framerates were terrible, everything was jerky.   Now all is well.

---

### Post by Starks on 2009-02-03
Same here.

945GM.

Everything is golden except atmosphere mode on Google Earth.

---

### Post by _tom_ on 2009-02-03
I have installed intrepid and jaunty on the same machine (hp nx7400). it's a notebook with a intel 945gm video adapter. subjective video performance with intrepid (kde 4.2, kwin with desktop effects) is very good while the performance in jaunty (same desktop config) is very poor.

---

### Post by biasquez on 2009-02-03
UXA is available only for intel or for radeon too?

---

### Post by RAOF on 2009-02-03
> **biasquez said:**
> UXA is available only for intel or for radeon too?

Only for Intel; radeon should either (a) get good performance with EXA, or (b) be too new to get any open-source acceleration at all.

The plan is apparently to merge some of the UXA work back into EXA, but some is going to be Intel specific.  There's quite a big difference between cards with no onboard VRAM (ie: Intel) and those with onboard VRAM :).

---

### Post by biasquez on 2009-02-03
thanks for info!!!

---

### Post by _tom_ on 2009-02-06
There is one further problem with the new X stack in jaunty (using intel 2.6.x driver): 
Neither I can play starcraft in wine nor Professor Fizzwizzle in native mode. In both cases the apps start fine (no error message, sound indicate that the games run), but the monitor "greys" out. 
Doesn't matter if I use exa or uxa.

Can anyone reproduce this?

---

### Post by castrojo on 2009-02-06
Hi guys,

We're looking for feedback on UXA, please see this page and follow the directions, thanks!

[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

---

### Post by Starks on 2009-02-06
Better and have using it for a week.

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

---

### Post by mc4100 on 2009-02-06
> **Starks said:**
> **Better**

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

+1, same chip.

---

### Post by klange on 2009-02-06
That colormap bug ("transparency artifacts" - it's colormap blending issues, really, not "artifacts" by any definition that I've ever seen) really needs to get fixed. It's the only thing that stands between us and relatively equivalent OpenGL handling to nVidia.

I marked "Much Better" because GEM/DRI2 makes my life (more) complete. Now I can get back to work on both of the two projects I love - Compiz and my game.

---

### Post by Starks on 2009-02-06
I don't know if anyone is experience this, but at least once a day, Jaunty will just freeze and the only thing that will respond is the mouse or the REISUB combo.

---

### Post by klange on 2009-02-06
> **Starks said:**
> I don't know if anyone is experience this, but at least once a day, Jaunty will just freeze and the only thing that will respond is the mouse or the REISUB combo.
This is a typical UXA crash. No log records I assume? (that would be another sign)

---

### Post by Starks on 2009-02-06
> **WindowsSucks said:**
> This is a typical UXA crash. No log records I assume? (that would be another sign)

I wouldn't even know how to take a log.

---

### Post by klange on 2009-02-06
> **Starks said:**
> I wouldn't even know how to take a log.

It's actually a matter of check /var/log/Xorg.0.log[.old]

---

### Post by Jim March on 2009-02-06
What's the situation with this setup (esp. the 2.6.99 Intel driver with UXA) and the Intel 965 chipset?

---

### Post by mewithafez on 2009-02-07
> **Jim March said:**
> What's the situation with this setup (esp. the 2.6.99 Intel driver with UXA) and the Intel 965 chipset?

Was on the first page: [https://wiki.ubuntu.com/X/UxaTesting]("https://wiki.ubuntu.com/X/UxaTesting")

If you click through, it has feedback on many cards and instructions on how to enable it. You can either use the included driver or the xorg-edgers PPA one. Give it a try!

---

### Post by Jim March on 2009-02-07
Ah.  OK...I think I'll give it until beta5 to jump in.  Jaunty looks like it's not going to be the smoothest alpha/beta cycle as there's too many video-related changes going on.  All going in a good direction of course...

Come to think, it seems like the cleanest alpha code we ever saw was Feisty.  Feisty was smooth and clean as early as Alpha3 or so and was hardly more problematic before then.  Nothing like as nice as some newer critters have been :).

---

### Post by PRGUY85 on 2009-02-07
I just tested thison an old HP DV1315cl laptop with Intel 915GM graphic driver.  It makes the Kwin effects on Kubuntu Jaunty Alpha 4 smoother although difference is barely noticeable.  Yet, it's an improvement.

---

### Post by klange on 2009-02-07
Just slapped some formatting into that UXATesting page on the Wiki.
Green means better, red means worse, yellow means mixed, gray means same.

---

### Post by castrojo on 2009-02-07
Wow thanks for the formatting and feedback so far! The response has been excellent. I am sitting next to Bryce at the airport and he was happy to see such good responses so far, keep it up!

---

### Post by Starks on 2009-02-07
> **whiprush said:**
> Wow thanks for the formatting and feedback so far! The response has been excellent. I am sitting next to Bryce at the airport and he was happy to see such good responses so far, keep it up!
You guys just randomly hang out in airports on Saturdays?

---

### Post by dentaku65 on 2009-02-14
In my experience under Jaunty Alpha 4 the uxa wiki instructions are not enough.
My card:
```
Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```
without uxa enabled have really slow performances, 50 FPS with glxgears, and really poor scroll (ie in FF).
With uxa enabled really good performances, 500 FPS with glxgears, but I experienced after 5/10 minutes some font issue (some chars vanished from the video or became distorted, ie: double tt, double dd, uppercase E, uppercase I and so on), and after 60 minutes the system freeze (hard reset is needed).

I changed my xorg.conf in this:
```
Section "Device"
	Identifier	"Configured Video Device"
        Option "AccelMethod" "UXA"
	Option "FramebufferCompression" "true"
EndSection

```
the situation ins better but not "state of art"

---

### Post by zombiepig on 2009-02-14
I'm travelling at the moment so don't have a Jaunty test machine accessible, but could someone with UXA enabled answer a question for me... On intrepid, if two users are logged in on the same machine, only the first can use direct rendering & compiz. Has this situation changed with UXA & DRI2? Can two users logged in simultaneously both use compiz?

---

### Post by mariner09 on 2009-02-14
I just enabled UXA on my T61 and it seems fine at 1st glance...

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

glxgears reports 410fps

---

### Post by dentaku65 on 2009-02-15
Changed my xorg.conf again (seems better):

```
Section "Device"
	Identifier	"Configured Video Device"
        Option "AccelMethod" "UXA"
	Option "FramebufferCompression" "true"
	Option "Legacy3D" "true"
EndSection

```
More stable to me but less FPS (360) than the post before.

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

UPDATE: sorry guys, no story on my machine, the fonts after a couple of hrs became sluggish; revert with no UXA, leaving FB compression.

```
Section "Device"
	Identifier	"Configured Video Device"
	Option "FramebufferCompression" "true"
EndSection

```

---

### Post by mariner09 on 2009-02-15
I started to notice some oddities with the menus.  They would flash a slight transparent prior to stabilizing after sliding open.

---

### Post by TrueTom on 2009-02-16
I'm too lazy to register so...

945GM/GMS [8086:27a2] (rev 03)

Mixed

Performance increase compared to EXA but still twice as slow as Intrepid, Suspend/Resume works, but whole system locks up after a while. GNOME menus look weird for a moment after opening.

---

### Post by klange on 2009-02-16
> **TrueTom said:**
> I'm too lazy to register so...

945GM/GMS [8086:27a2] (rev 03)

Mixed

Performance increase compared to EXA but still twice as slow as Intrepid, Suspend/Resume works, but whole system locks up after a while. **GNOME menus look weird for a moment after opening**.
Do you by any chance use fading windows of some sort? The colormap bugs would explain that.

---

### Post by TrueTom on 2009-02-16
This seems to be the case...

---

### Post by Taiebot65 on 2009-02-16
By enabling that i could use elisa, and compiz again [http://elisa.fluendo.com/]("http://elisa.fluendo.com/")

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

---

### Post by Taiebot65 on 2009-02-16
By enabling that i could use elisa, and compiz again [http://elisa.fluendo.com/]("http://elisa.fluendo.com/")

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

---

### Post by Starks on 2009-02-16
Why is UXA so crash-prone?

---

### Post by Starks on 2009-02-16
It's such a cruel trade-off.

Piss poor, stable, 60fps performance with EXA vs. Amazing, albeit crashy, 500fps performance with UXA.

---

### Post by halfsane on 2009-02-16
working really well for me. 

I was missing the smooth animations :D

---

### Post by Starks on 2009-02-17
(So... What's this framebuffercompression option?)

I am in despair. World of Goo is unplayable without UXA, but UXA crashes.

---

### Post by dentaku65 on 2009-02-18
Unfortunately UXA enabled with the updates of today still in happy crash in about 10 minutes (hard reset needed), here my actual version/conf:

VGA
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

xorg.conf
```
Section "Device"
	Identifier	"Configured Video Device"
#        Option "AccelMethod" "UXA"
	Option "FramebufferCompression" "true"
EndSection
```

Kernel
```
2.6.28-8-generic #23-Ubuntu SMP Wed Feb 18 03:23:10 UTC 2009 i686 GNU/Linux

```

Xorg ver.
```
X.Org X Server 1.5.99.902 (1.6.0 RC 2)
Release Date: 2009-1-30
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux sava-box 2.6.28-8-generic #23-Ubuntu SMP Wed Feb 18 03:23:10 UTC 2009 i686
Build Date: 18 February 2009  01:41:32AM
xorg-server 2:1.5.99.902-0ubuntu7 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
```

Xorg Log warnings (more /var/log/Xorg.0.log |grep WW)
```
	[    0.097140] (WW) warning, [    0.097148] (EE) error, [    0.097157] (NI) not implemented, [    0.097166] (??) unknown.
[    0.175408] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    0.701751] (WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
[    2.702641] (WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
[    2.702686] (WW) intel(0): PP_STATUS before: on, ready, sequencing idle
[    2.702707] (WW) intel(0): PP_STATUS after: on, ready, sequencing on
[    2.745806] (WW) intel(0): DRI2 requires UXA
[    2.868688] (WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
[    2.868715] (WW) intel(0): Allocation error, framebuffer compression disabled
[    2.868744] (WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
[    4.110984] (WW) intel(0): Chosen PLL clock of 66.5 Mhz more than 2% away from desired 65.0 Mhz
[    4.323847] (WW) intel(0):   Hardware claims pipe A is on while software believes it is off

```

Intel driver
```
Jaunty
```

---

### Post by hyperair on 2009-02-20
> **Starks said:**
> (So... What's this framebuffercompression option?)

I am in despair. World of Goo is unplayable without UXA, but UXA crashes.
It seems that other games have similar issues. In my case it's Touhou which runs at 60FPS on Intrepid, but 10FPS on Jaunty. I've only ever tested on a LiveUSB environment though.

---

### Post by Starks on 2009-02-20
ZOMG! Compiz is the culprit!

I have figured out how to consistently and repeatedly crash my system when UXA is enabled: Attempting to disable Compiz

It doesn't matter whether this is done through gnome-appearance-properties, the terminal, or fusion-icon. Disabling Compiz will freeze X.

---

### Post by dentaku65 on 2009-02-21
I disabled UXA and I found this trick to have some good performances:

Install driconf
```
sudo apt-get install driconf
```
Execute driconf
```
sudo driconf
```
and exit without touch anything (say yes if the app asks for save)

Then edit this file
```
gedit ~/.drirc
```
and paste this text:
```
<driconf>
    <device screen="0" driver="[COLOR="Red"]i915[/COLOR]">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>
```
replace the driver with your one.

Reboot the machine.

In my env I get this FPS with the stuff above on metacity (not tested with compiz) running glxgears:
```
2184 frames in 5.0 seconds = 436.638 FPS
2420 frames in 5.0 seconds = 483.925 FPS 
2425 frames in 5.0 seconds = 484.840 FPS
2410 frames in 5.0 seconds = 481.962 FPS
2161 frames in 5.0 seconds = 431.454 FPS
1295 frames in 5.0 seconds = 258.793 FPS
1871 frames in 5.0 seconds = 374.186 FPS
2417 frames in 5.0 seconds = 483.298 FPS
2112 frames in 5.0 seconds = 422.337 FPS
```
Not so brilliant as UXA enabled but at least the system is pretty usable :-)

---

### Post by Starks on 2009-02-21
**WTF! THAT'S ALMOST A 1000% IMPROVEMENT.**

You got that on EXA?!?!?

---

### Post by dentaku65 on 2009-02-21
> **Starks said:**
> **WTF! THAT'S ALMOST A 1000% IMPROVEMENT.**

You got that on EXA?!?!?

I supposed yes, because I commented UXA in xorg.conf and EXA should be the default value for intel at the moment in Jaunty.

---

### Post by Tich666 on 2009-02-21
> **Starks said:**
> ZOMG! Compiz is the culprit!

I have figured out how to consistently and repeatedly crash my system when UXA is enabled: Attempting to disable Compiz

It doesn't matter whether this is done through gnome-appearance-properties, the terminal, or fusion-icon. Disabling Compiz will freeze X.

It's exactly the other way around for me.
I have compiz disabled, but when I enable it via gnome-appearance-properties or the fusion-icon and drag a window outside of the 2048 pixel range (no 3d acceleration) I get pretty artifacts and a lockup which forces me to hard reset (power button).

What bugs me is that it seemed to work fine with kwin until it broke a week or two ago.. guess I'll give KDE another try soon.

Thanks for the tip dentaku, might be worth checking out to see if EXA works with compiz. Although in the long run I'd prefer to stick with UXA seeing as the changes won't be merged back into EXA and UXA apparently has some pretty nifty advantages: see [here](http://www.phoronix.com/forums/showthread.php?p=63239#post63239)

Also compiz 0.8.0 has been released, maybe this will fix the issues I'm having.

---

### Post by mariuz on 2009-02-21
I enabled in xorg.conf seems quite stable and kde4.2 moves a little faster
also i have started openarena and it didn't crashed
I will see later what are the differences with some benchmarks:popcorn:

---

### Post by dentaku65 on 2009-02-21
> **Tich666 said:**
> It's exactly the other way around for me.
I have compiz disabled, but when I enable it via gnome-appearance-properties or the fusion-icon and drag a window outside of the 2048 pixel range (no 3d acceleration) I get pretty artifacts and a lockup which forces me to hard reset (power button).

What bugs me is that it seemed to work fine with kwin until it broke a week or two ago.. guess I'll give KDE another try soon.

Thanks for the tip dentaku, might be worth checking out to see if EXA works with compiz. Although in the long run I'd prefer to stick with UXA seeing as the changes won't be merged back into EXA and UXA apparently has some pretty nifty advantages: see [here](http://www.phoronix.com/forums/showthread.php?p=63239#post63239)

Also compiz 0.8.0 has been released, maybe this will fix the issues I'm having.

It works pretty well in compiz too.
Tried for a couple of hrs without problems except for some refresh annoyances in some fullscreen actions and, just my feels, that using metacity instead of compiz in firefox the refresh (or window response) is a little bit better when many tabs are open.
Here the FPS with compiz:
```
2336 frames in 5.0 seconds = 467.075 FPS
2397 frames in 5.0 seconds = 479.324 FPS
2354 frames in 5.0 seconds = 470.780 FPS
2392 frames in 5.0 seconds = 478.272 FPS
2395 frames in 5.0 seconds = 478.970 FPS
2230 frames in 5.0 seconds = 445.878 FPS

```

Here my Default.ini of compiz
```
[core]
as_active_plugins = vpswitch;core;splash;workarounds;place;move;widget;text;put;png;regex;video;imgjpeg;resize;ring;svg;decoration;shift;animation;wobbly;cube;scale;cubecaps;rotate;cubereflex;expo;ezoom;switcher;
s0_number_of_desktops = 4
as_command_terminal = konsole
as_command_screenshot = 
as_command_window_screenshot = 
s0_refresh_rate = 60
s0_hsize = 4
s0_vsize = 2
s0_opacity_matches = ((type=Unknown | Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer);title=Konsole$ & !type=dialog;
s0_opacity_values = 89;82;
as_cursor_theme = DMZ-White
s0_sync_to_vblank = true

[decoration]
as_mipmap = true
as_command = emerald --replace

[rotate]
s0_zoom = 0.500000

[wobbly]
s0_friction = 1.500000
as_snap_inverted = false

[animation]
s0_close_durations = 300;50;50;
s0_close_matches = (type=Normal | Dialog | ModalDialog | Utility);(type=Tooltip | Notification);(type=Menu | PopupMenu | DropdownMenu);
s0_open_effects = 9;9;
s0_open_durations = 150;50;
s0_open_matches = (type=Menu | PopupMenu | DropdownMenu);(type=Tooltip | Notification);
s0_open_options = ;
s0_magic_lamp_amp_max = 200.000000
s0_minimize_effects = 12;
s0_minimize_durations = 490;

[cube]
s0_skydome_image = /root/skydome/DeathValley1.png
s0_skydome = true
s0_color = #b1c8daff

[cubecaps]
s0_bottom_images = /root/skydome/55865-drops.jpg;
s0_top_images = /root/skydome/55865-drops.jpg;

[shift]

[splash]
as_background = /usr/share/compiz/splash_background.png
as_logo = /usr/share/compiz/splash_logo.png

[workarounds]
as_sticky_alldesktops = true
as_fglrx_xgl_fix = true

[put]

[cubereflex]
s0_mode = 2

[reflex]
s0_file = /usr/share/compiz/reflection.png
s0_window = true
s0_threshold = 5

```

---

### Post by glasen on 2009-02-21
> **dentaku65 said:**
> <option name="vblank_mode" value="0" />

Sorry, but your "super fantastic performance improvement" is nothing more than disabling vertical sync blanking (For all Windows-users "VSYNC disabled").

---

### Post by dentaku65 on 2009-02-21
> **glasen said:**
> Sorry, but your "super fantastic performance improvement" is nothing more than disabling vertical sync blanking (For all Windows-users "VSYNC disabled").

I really said "super fantastic performance improvement"?


Thanks for the info about VSYNC.
:guitar:

---

### Post by tkawa6 on 2009-02-23
Thanks for the tip dentaku65! I tried it on my R60 that has a Intel 945, and this is my glxgears results. 60fps to 1200fps is awesome.

> 5602 frames in 5.0 seconds = 1120.363 FPS
6042 frames in 5.0 seconds = 1208.233 FPS
6020 frames in 5.0 seconds = 1203.888 FPS
6025 frames in 5.0 seconds = 1204.840 FPS
6031 frames in 5.0 seconds = 1206.139 FPS
6031 frames in 5.0 seconds = 1206.048 FPS
6015 frames in 5.0 seconds = 1202.860 FPS
6026 frames in 5.0 seconds = 1205.115 FPS
6021 frames in 5.0 seconds = 1204.145 FPS
5944 frames in 5.0 seconds = 1188.724 FPS
5623 frames in 5.0 seconds = 1124.433 FPS


---

### Post by RAOF on 2009-02-23
> **tkawa6 said:**
> Thanks for the tip dentaku65! I tried it on my R60 that has a Intel 945, and this is my glxgears results. 60fps to 1200fps is awesome.

Although, of course, this isn't indicative of any *actual* performance improvement.  Merely that your card is no longer waiting for your screen to be able to display something before trying to display it.

---

### Post by ace214 on 2009-02-23
Does anyone know if there's a way of enabling this in a LiveCD environment? My laptop has a 915 chip, but I would like to test it before upgrading to/installing Jaunty. Right now if I put in a  Jaunty LiveCD, it just loops failing to load X.

---

### Post by klange on 2009-02-23
Boot to a root terminal, edit xorg.conf, then init to a higher level (or start X manually).

---

### Post by ace214 on 2009-02-23
> **WindowsSucks said:**
> Boot to a root terminal, edit xorg.conf, then init to a higher level (or start X manually).

Is there another way to boot to a terminal on the LiveCD than Ctrl-Alt-F1? When I do this the computer locks up and I get dead X lines.

EDIT: The Safe Graphics mode did the trick to get into the terminal. I added the UXA option, removed the vesa driver item so that it would autodetect the driver, and used "startx". It processes for a minute and then I get a freeze and multiple dead lines....

By the way, I'm on a 915 chipset.

---

### Post by scaine on 2009-03-03
I'm running 9.04 Alpha 5, with latest updates, compiz enabled and everything's working fine.  But when I edit my xorg.conf, it's completely empty.  How can I enable UXA in these circumstances?

---

### Post by Tich666 on 2009-03-03
Your question is answered multiple times on the first page alone, but since I'm s nice guy, here you go.

To enable it, put this in your xorg.conf: 
```

Section "Device"
        Identifier    "Configured Video Device"
        # ...
        Option        "AccelMethod" "uxa"
EndSection

```

[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

---

### Post by scaine on 2009-03-03
I don't think you read my post - my entire xorg.conf is an empty file.  I can't just copy in a single generic entry.  Those dots in the WIKI (yeah, I read it) imply that you simply add one line into your *already existing* device section.

If you can help with an empty xorg.conf, I'd be happy to give UXA a whirl.

Dunno why my xorg.conf is empty - this is possibly the default for intel card based laptops on Jaunty.  I did a fresh install from Alpha 5 about a week ago.

---

### Post by klange on 2009-03-03
> **scaine said:**
> I don't think you read my post - my entire xorg.conf is an empty file.  I can't just copy in a single generic entry.  Those dots in the WIKI (yeah, I read it) imply that you simply add one line into your *already existing* device section.

If you can help with an empty xorg.conf, I'd be happy to give UXA a whirl.

Dunno why my xorg.conf is empty - this is possibly the default for intel card based laptops on Jaunty.  I did a fresh install from Alpha 5 about a week ago.
Everything else should autoconfigure, you shouldn't need anything besides:
```
Section "Device"
        Identifier    "Configured Video Device"
        Option "AccelMethod" "uxa"
EndSection
```

---

### Post by jerrylamos on 2009-03-03
> **scaine said:**
> I don't think you read my post - my entire xorg.conf is an empty file.  I can't just copy in a single generic entry.  Those dots in the WIKI (yeah, I read it) imply that you simply add one line into your *already existing* device section.

If you can help with an empty xorg.conf, I'd be happy to give UXA a whirl.

Dunno why my xorg.conf is empty - this is possibly the default for intel card based laptops on Jaunty.  I did a fresh install from Alpha 5 about a week ago.
Just did a fresh alternate install.  xorg.conf was empty.  Booted in recovery mode, selected "attempt to fix X windows problems" (I forget the exact words, should be obvious) which then put an xorg.conf scaffold in so I could make changes.  One way, select root prompt and then do nano /etc/X11/xorg.conf

Jerry

---

### Post by Taiebot65 on 2009-03-04
I have to say i did have to stop using UXA.because It was too unstable some time my memory jump when loading photos and could crashed x and compiz was found with different color...
So I've stopped using compiz because it s too slow :( with no UXA..

```
L Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by TomaszD on 2009-03-04
> **Taiebot65 said:**
> I have to say i did have to stop using UXA.because It was too unstable some time my memory jump when loading photos and could crashed x and compiz was found with different color...
So I've stopped using compiz because it s too slow :( with no UXA..

```
L Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

Then support fixing this bug, it should fix the instability:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/337697](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/337697)

---

### Post by scaine on 2009-03-04
> **jerrylamos said:**
> Just did a fresh alternate install.  xorg.conf was empty.  Booted in recovery mode, selected "attempt to fix X windows problems" (I forget the exact words, should be obvious) which then put an xorg.conf scaffold in so I could make changes.  One way, select root prompt and then do nano /etc/X11/xorg.conf
Jerry

Awesome - thanks Jerry.  I'll give that a try when I get a hold of my laptop later on.

---

### Post by Tich666 on 2009-03-04
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
That should have the same effect.

Since xorg is mostly auto-configured anyway there's really no point in adding anything besides the section from the wiki I posted on the last page for testing UXA.

---

### Post by scaine on 2009-03-07
> **Tich666 said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```That should have the same effect.

Since xorg is mostly auto-configured anyway there's really no point in adding anything besides the section from the wiki I posted on the last page for testing UXA.

Great stuff - thanks Tich666.  That worked a treat and gave me a really bare bones xorg.conf (attached - oops, no it's not, forum won't let me attach .conf files for some reason...).  Then I added the UXA option.  But it was pretty disappointing, at least in the simplistic terms of running GLXgears :

Without UXA :
```
scaine@GroovyTosh:~$ glxgears
3745 frames in 5.0 seconds = 748.973 FPS
4071 frames in 5.0 seconds = 814.105 FPS
4064 frames in 5.0 seconds = 812.739 FPS
4081 frames in 5.0 seconds = 816.124 FPS
4053 frames in 5.0 seconds = 810.575 FPS
4064 frames in 5.0 seconds = 812.645 FPS
4054 frames in 5.0 seconds = 810.752 FPS
4071 frames in 5.0 seconds = 814.069 FPS
4072 frames in 5.0 seconds = 814.207 FPS
4545 frames in 5.0 seconds = 908.797 FPS
4073 frames in 5.0 seconds = 814.467 FPS
4076 frames in 5.0 seconds = 815.136 FPS
```

With UXA :
```
scaine@GroovyTosh:~$ glxgears 
2474 frames in 5.0 seconds = 494.668 FPS
2725 frames in 5.0 seconds = 544.973 FPS
2718 frames in 5.0 seconds = 543.528 FPS
2708 frames in 5.0 seconds = 541.463 FPS
2699 frames in 5.0 seconds = 539.732 FPS
2709 frames in 5.0 seconds = 541.631 FPS
2712 frames in 5.0 seconds = 542.323 FPS
2717 frames in 5.0 seconds = 543.277 FPS
2723 frames in 5.0 seconds = 544.560 FPS
2380 frames in 5.0 seconds = 475.917 FPS
2818 frames in 5.0 seconds = 563.425 FPS
2198 frames in 5.0 seconds = 439.474 FPS
```

So just over half as fast at rendering the gears.  That's on a GMA4500 card, built into my Tosh U400 laptop.  Maybe UXA gives a boost only for the lower end Intel cards like the 8-series or early 9-series?

I'm happy to run with UXA for a bit for testing purposes though.  My screen seems marginally darker when running UXA too - is this just my imagnation though?

---

### Post by Tich666 on 2009-03-07
I too have a 4500MHD but for me UXA seems better than EXA.

I'm using the xorg-edgers driver (2.6.3) and kernel 2.6.29 and I get about 300fps in glxgears, used to be higher iirc.

I'm using metacity compositing rather than compiz because 3d-acceleration only works up to a screen size of 2048, which is is too small for my dual monitor setup. Running compiz with UXA also seems to be a sure way to make the X crash for me.

Can only hope for gradual improvements in time. :(

---

### Post by RAOF on 2009-03-07
> **scaine said:**
> ...
So just over half as fast at rendering the gears.  That's on a GMA4500 card, built into my Tosh U400 laptop.  Maybe UXA gives a boost only for the lower end Intel cards like the 8-series or early 9-series?
...

Say after me: *glxgears is not a benchmark*.  At most, it's a tool for checking that your 3D stack isn't totally broken.  The numbers which come out are *not* a measure of general 3D performance - glxgears stresses only a tiny part of the 3D pipeline, and a part which generally *isn't* stressed by actual 3D applications.  One obvious difference is that UXA will enable DRI2, which will make 3D play nice with a composite manager.  This means that glxgears will no longer draw straight to the screen, and since drawing the rendered scene to the screen is generally the bottleneck glxgears hits, it makes sense to me that UXA will show a lower glxgears score.

[This](http://www.phoronix-test-suite.com/) is a benchmark.  Numbers this produces are a more appropriate measurement of real-world performance.

---

### Post by scaine on 2009-03-08
> **scaine said:**
>   But it was pretty disappointing, at least in the simplistic terms of running GLXgears :


@RAOF : you slightly misquoted me there, I think.  I never claimed that GLXgears was a "benchmark".  But I do believe it to be, in simplistic terms, a feasible measure of raw output.  I know it's not the whole story.  Only further testing will give me that.

[EDIT : Reading your reply again, I think you're going so far as to say that GLXgears isn't even a feasible  measure of raw output.  Bugger.  But I've just noticed that the Phoronix-test-suite you link to is in the repos, so that's getting a dust down in the near future.  Thanks.]

Thanks for the info about how it works - does this mean that it will work better with the likes of Google Earth, Second Life and such like?  I mean, I'll be completely honest here, I know *nothing* about UXA, it's advantages or disadvantages.  I'll do some research, but if you have any good links, I'd like to know more.

---

### Post by yelo3 on 2009-03-08
For those using the xorg edgers ppa, and have the 4500mhd. Does suspend-resume still crash the X server?

---

### Post by Tich666 on 2009-03-09
Suspend kind of works. The x-server isn't crashing anymore on suspend but it seems it is restarted upon resume, because I'll get thrown back to the GDM screen.

I'm using kernel 2.6.29-rc7 btw, latest version of xorg-edgers intel driver on my 4500mhd.

---

### Post by Jay_Bee on 2009-03-09
I am using Jaunty regular kernel and drivers and with UXA I get the same as Tich666, suspend works fine, but on resume I am thrown back to GDM login screen.
Other than that I am happy with UXA because of it's better performance, but I disabled all opacity/fading compiz plugins because the transparency bug is very annoying.

---

### Post by Halow on 2009-03-11
Aha. This seems to have been why things had been crawlingly slow. Turned UXA on and now things work great! According to lspci I have: ```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

---

### Post by klange on 2009-03-11
> **Halow said:**
> Aha. This seems to have been why things had been crawlingly slow. Turned UXA on and now things work great! According to lspci I have: ```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

GMA 945 sees major improvements with UXA, contrary to most of the other cards...

**e**: It seems that Intel is prepping for another driver release, which I fear has no chance of making it in here, even in future backports, but it corrects an important issue with the current UXA implementation: Windows don't have the correct colormap / alpha blending mode, so they look strange under a number of circumstances in Compiz.

---

### Post by crjackson on 2009-03-11
> **klange said:**
> GMA 945 sees major improvements with UXA, contrary to most of the other cards...

**e**: It seems that Intel is prepping for another driver release, which I fear has no chance of making it in here, even in future backports, but it corrects an important issue with the current UXA implementation: Windows don't have the correct colormap / alpha blending mode, so they look strange under a number of circumstances in Compiz.

Would there be an easy way for a lay user to update this driver after the Jaunty release? I'm using Hardy right now on my laptop because of the really cruddy performance I get with Intrepid. I would REALLY love to upgrade to Jaunty without losing performance as compared to Hardy.

---

### Post by Jay_Bee on 2009-03-12
Compiz 0.8 is now very slow when UXA is enabled (unusable).
That's a shame because before the update it was working, I hope the devs will fix it.

---

### Post by noworry on 2009-03-13
After upgrading Kubuntu Intrepid to Jaunty, desktop effects were very sluggish. Even switching between applications was very slow. 
I thought of going back to Intrepid for now, but enabling uxa by adding 'Option        "AccelMethod" "uxa"', greatly improved the general responsiveness and it is visibly fast.
Previously Xorg used to take nearly 100% of cpu for application switches (!!), but that has gone down to nearly 10-20% after enabling uxa.

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

I ll using uxa and also wait for any new intel drivers, which fix the X problems that are present in 945GM.

Thanks a lot...

---

### Post by RacerII on 2009-03-16
> **Jay_Bee said:**
> Compiz 0.8 is now very slow when UXA is enabled (unusable).
That's a shame because before the update it was working, I hope the devs will fix it.

Same here  , any news on this?

---

### Post by vredley on 2009-03-16
> **RacerII said:**
> Same here  , any news on this?

Here's the fix: [http://ubuntuforums.org/showpost.php?p=6904097&postcount=49](http://ubuntuforums.org/showpost.php?p=6904097&postcount=49)

---

### Post by Starks on 2009-03-16
Will a more formal fix be released in the form of an updated package?

---

### Post by Halow on 2009-03-16
Not a week ago, I was happy to enable it. Now it seems to be the cause of my boot-up woes. Every time I enable it now, and reboot, I end up with funky colors at the GDM login. Running xfix from recovery mode fixes it. I wonder what happened.

---

### Post by Mindless Automata on 2009-03-16
I'm getting system stability issues with UXA enabled.

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)

---

### Post by adult swim on 2009-03-17
> **Mindless Automata said:**
> I'm getting system stability issues with UXA enabled.

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
me too.  i will randomly get hard freezes and the only way to recover is reisub

---

### Post by RacerII on 2009-03-17
> **vredley said:**
> Here's the fix: [http://ubuntuforums.org/showpost.php?p=6904097&postcount=49](http://ubuntuforums.org/showpost.php?p=6904097&postcount=49)

Doesnt fix it for me , still slow when its disabled.

---

### Post by Mindless Automata on 2009-03-17
> **adult swim said:**
> me too.  i will randomly get hard freezes and the only way to recover is reisub

Yep, hard freezes :(

---

### Post by Starks on 2009-03-17
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

Still getting hard crashes with UXA.

---

### Post by noworry on 2009-03-18
I have xserver-xorg-video-intel/jaunty uptodate 2:2.6.3-0ubuntu1 installed today, but still it doesn't seem to fix the slow performance issues with my Intel 945 GM. 

So, I have to re-enable UXA again to make my Kubuntu Jaunty usable.

I just noticed that glxgears with UXA gives around 250 FPS. If I don't use UXA, I get around 1100 FPS !!
This seems very strange to me, because enabling UXA fixes the performance issues with my desktop effects (like window switch, minimize/maximize etc) !!

Can anybody explain why this is happening ?

Thanks a lot...

---

### Post by raggari on 2009-03-18
> **noworry said:**
> I have xserver-xorg-video-intel/jaunty uptodate 2:2.6.3-0ubuntu1 installed today, but still it doesn't seem to fix the slow performance issues with my Intel 945 GM. 

So, I have to re-enable UXA again to make my Kubuntu Jaunty usable.

I just noticed that glxgears with UXA gives around 250 FPS. If I don't use UXA, I get around 1100 FPS !!
This seems very strange to me, because enabling UXA fixes the performance issues with my desktop effects (like window switch, minimize/maximize etc) !!

Can anybody explain why this is happening ?

Thanks a lot...

Maybe it's related to DRI2 issues:
[http://qa-rockstar.livejournal.com/7869.html](http://qa-rockstar.livejournal.com/7869.html)

---

### Post by amano on 2009-03-18
I wouldn't care about glxgears. If performance is important just use more real world test suits like those from the phoronix test suit. glxgears just doesn't tell you anything, at least not at those high fps rates (120+ fps).

---

### Post by frigaut on 2009-03-18
For information: since the march 10 updates, I had problems with suspend when using UXA. Suspend was working allright, but when resuming, the X server would crash -most of the time but not always- and thus after resume I was presented with a new login screen. Kind of annoying.

I found a patch that (at least in the past hours) seems effective: I set a vga mode at boot time (add vga=### to the boot parameters, I use 789 or 792 in my case). This I believe loads the frame buffer driver which apparently plays nicer with UXA. Bottomline, this fixed my problem and X does not crash anymore after resume (cross fingers).

Note: I have a Mobile 945GM 8086:27a2.

---

### Post by jerrylamos on 2009-03-18
> **amano said:**
> I wouldn't care about glxgears. If performance is important just use more real world test suits like those from the phoronix test suit. glxgears just doesn't tell you anything, at least not at those high fps rates (120+ fps).

O.K., downloaded and installed phoronix test suite.  Tons and tons of tests.  Even in x11perf there seem to be well over 300 tests.  Any clue what might be useful?

Thanks, Jerry

---

### Post by binbash on 2009-03-23
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)

It is working perfect, i got a super speed : )

---

### Post by hyperair on 2009-03-23
Using what to benchmark? As far as I could tell (using a 3d game) the framerate was still pretty low using that hardware.

---

### Post by binbash on 2009-03-23
> **hyperair said:**
> Using what to benchmark? As far as I could tell (using a 3d game) the framerate was still pretty low using that hardware.

You do not need a benchmark tool because without UXA, i can't even move the mouse  :)

---

### Post by hyperair on 2009-03-23
Compiz has pretty smooth animations on both EXA and UXA for me in Jaunty. But compared to Intrepid where I can play Touhou smoothly, Lunatic mode in Jaunty ends up lagging so much it's easier than easy mode in Intrepid.

---

### Post by Starks on 2009-03-23
> **hyperair said:**
> Compiz has pretty smooth animations on both EXA and UXA for me in Jaunty. But compared to Intrepid where I can play Touhou smoothly, Lunatic mode in Jaunty ends up lagging so much it's easier than easy mode in Intrepid.
Thanks for reminding me that I need to finish Perfect Cherry Blossom in Wine.

---

### Post by hyperair on 2009-03-23
Haha. But it's really no fun if you're in Jaunty. FPS drops from ~60 to ~20 =(

---

### Post by jerrylamos on 2009-03-23
> **hyperair said:**
> Haha. But it's really no fun if you're in Jaunty. FPS drops from ~60 to ~20 =(
What hardware, VGA. memory, etc. are you using?  Depending on which pc I'm using I get 200 to 300 or better on glxgears, youtube video pretty smooth, etc.  That's with:
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009
and pc's with 1.5 gHz pentium, 1.0, 2.0, and 3.3 gHz celeron, Intel & ATI VGA.

Jerry

---

### Post by hyperair on 2009-03-24
Intel X3100 965GMA GPU. 2GB RAM, 2GHz C2D.. Either way, glxgears is not a good benchmark. That gets somewhere around 500FPS on Jaunty. And Youtube video is fine and everything. Get something REALLY 3d to test, not glxgears, and not Youtube video, and you'll see the performance hit. The game runs pretty smoothly on Intrepid.

---

### Post by zevans on 2009-03-25
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
```

Now fairly stable for me on the following stack:

Kernel 2.26.28-11.37 - wasn't stable at all on earlier -11 updates so quite pleased with that. I think this is the latest Jaunty kernel we will have by the look of it?
xorg-server 2:1.6.0-0ubuntu4 
Intel module version 2.6.3

BUT when I suffer the occasional lockup, it's a hard lockup and I can't switch VCs at all. If I log in from elsewhere to shut the box down cleanly sometimes it will come down and sometimes it will panic on the way down.

Performance is WAY better with kernel 2.6.**29**-020629rc8-generic but this combo isn't stable. There is a reproducible problem whereby X appears to carry on invisibly, so if I click on icons etc stuff still happens, but the real screen is no longer refreshed. If I switch consoles away and back again the screen will "connect" again, and then I'm OK for a few minutes until exactly the same thing happens again. Anyone else seen this?

---

### Post by tjeremiah on 2009-03-28
Intel GM965/GL960 (rev 0c) So far so good. Increase in performance and things are running cooler. Though, the menus flicker, this is the only problem I am seeing. (ubuntu 9.04)

---

### Post by tomchiverton on 2009-03-30
X performance fell of a cliff for me using 9.04 beta over 8.10 (with KDE4 from backport or experimental) with X consuming 30% CPU: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/350844](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/350844)
Swapping to UXA has got that to under 10%, stock kernel and X packages.
Dell inspirion 1525 laptop.
$ lspci -nn|grep -i VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

---

