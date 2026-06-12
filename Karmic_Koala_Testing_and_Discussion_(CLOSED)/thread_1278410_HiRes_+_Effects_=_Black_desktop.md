---
title: "HiRes + Effects = Black desktop"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LittleKoy on 2009-09-29
I just upgraded to Koala. It works great so far, except for an issue.
I have a 22" and use a 1680x1050 res. My vga is an Ati Radeon 9200SE, so I'm using opensource ati radeon driver.

The problem is that, when I try to activate effects, my desktop becomes black, and I can't see anything on it, not the wallpaper nor the icons. Same with windows: if I maximize them, or make them too big, they become all black.

With small windows it works fine. Same if I lower to resolution down to 1280x960 (1280x1024 already gives the issue).

Anyone experiencing this?

---

### Post by LittleKoy on 2009-09-30
No one? Sounds strange, since radeon + compiz + high resolution should be pretty common..

---

### Post by Menthu_Rae on 2009-09-30
I'm running Compiz at 1920x1200 with no ill effects although on an nVidia 8800 Ultra with the nvidia closed-source drivers.

It possibly sounds like either a driver issue or texture memory issue, though former is much more likely than the latter.

Personally I haven't had much luck with ATi + Ubuntu and switched all my PCs over to nVidia or at the worst (for integrated stuff), Intel.

Sorry this isn't much help, but I don't think it's resolution related only.

---

### Post by Amaranth on 2009-09-30
Please give the output of `CM_DRY=yes compiz`.

---

### Post by LittleKoy on 2009-09-30
> **Amaranth said:**
> Please give the output of `CM_DRY=yes compiz`.

I'm at work right now, but I'll post it as soon as I get home.

Thanks

---

### Post by LittleKoy on 2009-09-30
Ok, here is the output:

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Dry run finished: everything should work with regards to Compiz and 3D.
Execute: /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering   move resize place decoration animation ccp
```

---

### Post by NRDNick on 2009-10-01
sorry to hijack the thread, but recently I updated my Karmic install after a few days of not updating. Update manager notified me a of a partial upgrade, so I went to synaptic and it told me the only thing it was uninstalling was the ubuntu software store to install the software center in it's place. Afterward on reboot, I was left with a black screen with my cursor on it. I ran top and nothing seemed to be locking my cpu, so I just rebooted again. This time the desktop came up but compiz is not enabled. I tried choosing to enable desktop effects via the appearance menu, but after searching for a driver, it says that it cannot enable 3D effects. 

Here is the output of CM_DRY=yes 

compiz nrd@nrd-desktop-ubuntu:~$ CM_DRY=yes compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
Dry run failed: Problems detected with 3D support.'nnrd@nrd-desktop-ubuntu:~$ 

Any ideas what may be wrong? I'm going to reinstall my nvidia 190.32 drivers and see if that helps. But any info would be appreciated. 

Thank you.

Edit: Reinstalling my proprietary drivers solved the issues that I was having, although I did have to change some of my compiz preferences, to re-enable the desktop cube and rotation. Hope that helps someone :)

---

### Post by danwood76 on 2009-10-01
I run the open source drivers, though with a slightly newer card, on my 3200 x 1080 desktop area with no problems.
This is obviously quite a bit bigger than yours and across two screens but I have no issues like you speak of. (My card is a X1950 PRO as in my sig)

The 9200 is getting quite old now, do you have access to a slightly newer ATI card you could test with the same setup?

---

### Post by LittleKoy on 2009-10-01
> **danwood76 said:**
> I run the open source drivers, though with a slightly newer card, on my 3200 x 1080 desktop area with no problems.
This is obviously quite a bit bigger than yours and across two screens but I have no issues like you speak of. (My card is a X1950 PRO as in my sig)

The 9200 is getting quite old now, do you have access to a slightly newer ATI card you could test with the same setup?

I'm sorry but I don't. My others pc all have (fortunately) nVidia cards.. Btw, yesterday night updates screwed my installation, and I can't boot anymore. I'm waiting for the beta to come out to make a clean install, so let's see what comes out of it.

---

### Post by danwood76 on 2009-10-01
Theres nothing wrong with the ATI cards to be fair to them.
But the 9200 was released in 2003, its entirely possible that your card cannot quite handle the larger desktop areas with compositing in the new driver. On the other hand your card could be faulty.

Could your try the beta 9.10 and also Jaunty with the same settings?

---

### Post by LittleKoy on 2009-10-01
> **danwood76 said:**
> Theres nothing wrong with the ATI cards to be fair to them.
But the 9200 was released in 2003, its entirely possible that your card cannot quite handle the larger desktop areas with compositing in the new driver. On the other hand your card could be faulty.

Could your try the beta 9.10 and also Jaunty with the same settings?

ATI cards themselves are fine, but drivers sometimes are not. A lot of my colleagues have newer ATI cards, and fglrx has a lot of issues, while opensource has poor support. But I hear that a lot is going on in the video area of Linux, especially for ATI users.

Btw, Jaunty, with the same resolution and compiz, was flawless.

---

### Post by danwood76 on 2009-10-01
FGLRX has always sucked but the opensource drivers are great right now, especially for the older cards.

I think you will have to test with a fresh install of the beta and if the problem persists report a bug against the xorg driver and compiz.

---

### Post by LittleKoy on 2009-10-01
> **danwood76 said:**
> FGLRX has always sucked but the opensource drivers are great right now, especially for the older cards.

I think you will have to test with a fresh install of the beta and if the problem persists report a bug against the xorg driver and compiz.

Yes, the opensource drivers are great and I can even play games (a bit old, like Deus Ex for instance) at high quality settings, which surprised me. They've always been great to me, but I know they are not to newer cards.

---

### Post by LittleKoy on 2009-10-01
Ok, writing from beta livecd, and the problem is still here.

I would like to file a bug, but I'm leaving for Munchen tomorrow. I'll file it when I'll be back (if I still remember who I am :D)

---

### Post by do1fmd on 2009-10-06
Exactly same problem here...

Window gets black if I size it is bigger than 1280x960...
Desktop-background and desktop-icons are black, too.
My resolution is 1400x1050.

Using IBM T40p with ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02) and ati driver.

This just happens if I have compiz activated.

Anyone any idea?

Output of 'CM_DRY=yes compiz':
> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Dry run finished: everything should work with regards to Compiz and 3D.
Execute: /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering   move resize place decoration animation ccp Greets, do1fmd.

---

### Post by tsikpemoise on 2009-10-07
Same problem here. Black screen. Panels are present, but icons are not.
Output of CM_DRY=yes compiz :

> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Dry run finished: everything should work with regards to Compiz and 3D.
Execute: /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering   move resize place decoration animation ccp

---

### Post by danwood76 on 2009-10-08
Are you all using the xorg ati driver?
(Not the radeon driver)

It could be an issue with that driver or with the cards age.

---

### Post by do1fmd on 2009-10-08
I have already tested radeon instead of ati driver in xorg.conf.

But this problem still exists.

Changed back to ati driver again.

Greets, do1fmd.

---

### Post by danwood76 on 2009-10-08
It would be interesting if there are some xorg errors.

Can you run the following commands in the terminal after you make it do the bug and post all output in seperate code blocks here:
```

cat /var/log/Xorg.0.log | grep '(EE)'

```
```

cat /var/log/Xorg.0.log | grep '(WW)'

```
```

cat /var/log/Xorg.0.log | tail

```

---

### Post by do1fmd on 2009-10-08
Hi again!

```
cat /var/log/Xorg.0.log | grep '(EE)'
``````
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to load module "freetype" (module does not exist, 0)
``````
cat /var/log/Xorg.0.log | grep '(WW)'
``````
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Warning, couldn't open module freetype
(WW) RADEON(0): LVDS Info:
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe3ffe000 is: 0xe3ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd07fd000
``````
cat /var/log/Xorg.0.log | tail
``````
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
```Thanks.

Greets, do1fmd.

---

### Post by danwood76 on 2009-10-08
Well I get pretty much the same warnings on my working radeon.

Could we also see any system messages?
```

dmesg | tail

```

---

### Post by do1fmd on 2009-10-08
Of course.

```
[   22.374982] type=1505 audit(1254988751.018:21): operation="profile_replace" pid=858 name=/usr/bin/evince-previewer
[   22.381955] type=1505 audit(1254988751.026:22): operation="profile_replace" pid=858 name=/usr/bin/evince-thumbnailer
[   22.392857] type=1505 audit(1254988751.038:23): operation="profile_replace" pid=860 name=/usr/lib/cups/backend/cups-pdf
[   22.393836] type=1505 audit(1254988751.038:24): operation="profile_replace" pid=860 name=/usr/sbin/cupsd
[   22.397115] type=1505 audit(1254988751.042:25): operation="profile_replace" pid=861 name=/usr/sbin/dhcpd3
[   26.465399] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.468406] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   26.468818] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.552365] ADDRCONF(NETDEV_UP): ath1: link is not ready
[   30.265723] ttyS1: LSR safety check engaged!
[   33.390365] __ratelimit: 12 callbacks suppressed
[   33.390371] type=1502 audit(1254988762.036:30): operation="open" pid=1207 parent=1206 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   33.390402] type=1502 audit(1254988762.036:31): operation="file_perm" pid=1207 parent=1206 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   33.390428] type=1502 audit(1254988762.036:32): operation="file_perm" pid=1207 parent=1206 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   34.229320] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   34.229343] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   34.229383] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   34.560951] [drm] Setting GART location based on new memory map
[   34.560964] [drm] Loading R200 Microcode
[   34.561020] [drm] writeback test succeeded in 2 usecs
```I post "dmesg | grep drm" also:
```
[   14.154135] [drm] Initialized drm 1.1.0 20060810
[   15.836630] [drm] radeon default to kernel modesetting DISABLED.
[   15.837430] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[   34.560951] [drm] Setting GART location based on new memory map
[   34.560964] [drm] Loading R200 Microcode
[   34.561020] [drm] writeback test succeeded in 2 usecs
```and "dmesg | grep agp"
```
[    0.098407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   11.264615] Linux agpgart interface v0.103
[   12.438675] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   12.458548] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   34.229320] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   34.229343] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   34.229383] pci 0000:01:00.0: putting AGP V2 device into 4x mode
```
Greets.

---

### Post by danwood76 on 2009-10-08
Well I cannot see any errors from the drivers in both sets of logs so this must be a compiz issue.
Could you file a bug against compiz?

---

### Post by do1fmd on 2009-10-08
> **danwood76 said:**
> Well I cannot see any errors from the drivers in both sets of logs so this must be a compiz issue.
Could you file a bug against compiz?How can I do this?
I have never filed a bug before!

Greets.

---

### Post by danwood76 on 2009-10-08
Check the sticky at the top of this forum:
[http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570)

---

### Post by do1fmd on 2009-10-08
Thanks a lot!

The bug is already filed at
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444139](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444139)
and there is a workaround which works for me perfectly:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444139/comments/3](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444139/comments/3)

Greets, do1fmd.

---

### Post by do1fmd on 2009-10-09
Well, now I get a other very strange problem.

After I had made the changes mentioned in Post above and activate compiz my text rendering is broken.

When I boot the laptop everything is fine.
After a short while letters disappear or are displayed wrong (see attachment).

This only happens if compiz is activated. If I deactivate compiz the broken letters stay there till restart of X server.

Same problem with "ati" and "radeon" driver in xorg.conf.

Greets.

Edit: Last picture added afert 1 hour uptime.

---

### Post by do1fmd on 2009-10-10
Found a workaround.

AGP in KMS-driver is buggy for now.

Add kernel parameter ```
radeon.agpmode=-1
``` or change /etc/modprobe.d/radeon-kms.conf like this ```
##enable KMS Radeon
options radeon modeset=1
options radeon agpmode=-1
```But this reduces performance significantly.

Greets, do1fmd.

---

### Post by SeePU on 2009-10-10
That's no good, then.

It's not just a black desktop screen either.  The entire system crashes and locks up.  It requires a restart of the machine.  That's serious (when all you're doing is enabling desktop effects).  I found some similar bug reports on the issue and there's been virtually no updates.  *shrugs and shakes head*

Note: 1400x1050 resolution.

Using IBM T41 with ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02) and ati driver

---

### Post by do1fmd on 2009-10-11
Found an other workaround.

If you don't or can't activate KMS you can reduce colour depth to 16 in xorg.conf-"screen"-section.```
        DefaultDepth    16
```

The big advantage: This doesn't reduce performance.

Greets.

---

### Post by danwood76 on 2009-10-12
> **do1fmd said:**
> 
The big advantage: This doesn't reduce performance.


Reducing colour depth does degrade the image so does infact reduce performance.

---

### Post by nukie77 on 2009-10-22
Any new updates to this bug?  We are getting close to the launch.

---

### Post by Amaranth on 2009-10-22
[https://bugs.launchpad.net/bugs/444139](https://bugs.launchpad.net/bugs/444139)

Looks like it won't be fixed for karmic. :/

---

