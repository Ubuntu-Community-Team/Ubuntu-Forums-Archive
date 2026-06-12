---
title: "Resolution stuck on 640x480 after Gutsy upgrade (Card: ATI Radeon 7000 VE)"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by pwest on 2007-10-30
Since upgrading to Gutsy I haven't been able to get my resolution to change beyond 640x480. 
Nothing makes any difference; preferences-> Screenres doesn't list any others option. The Screen and Graphics tool doesn't make any difference either. Even dpkg-reconfigure xserver-xorg hasn't changed anything. 
Trying either the "ati" or the "radeon" driver doesn't make any difference, either.

I seem to see there is in problem with the refresh rates, but don't know what can be done about that.

I am attaching my xorg.conf (plus backup before any reconfig) 

thanks for any tips

About the monitor: 1280x1024 - Hyndai ImageQuest L70S+
details here: [http://www.hyundaiq.de/produkte/tft/l70s+/l70s+.htm](http://www.hyundaiq.de/produkte/tft/l70s+/l70s+.htm)

---

### Post by pwest on 2007-10-31
I have finally managed to find the fix for my problem and am putting it here in case others are having the same issue. It turns out the issue was with the BIOS not report any panelsize for the monitor.

The tipoff was my Xorg.0.log file (in /var/log) which stated the following warning:

```
(WW) RADEON(0): No Panel Info Table found in BIOS!
(II) RADEON(0): Existing panel PLL dividers will be used.
(WW) RADEON(0): Panel size 640x480 is derived, this may not be correct.
If not, use PanelSize option to overwrite this setting
```

So I googled the PanelSize option and ended up adding the following to xorg.conf

```

Section "device" #    
	...	

[INDENT]Option		"PanelSize"	"1280x1024"[/INDENT]
EndSection

```

after which the resolution worked perfectly. :)

I'm not sure if this does or does not relate to [bug #3371: Xorg resolution falling back to 640x480 and/or 800x600 when h/v freqs incorrect]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731"). Can others advise as to whether I should add to that bug report, start a new one or do nothing.
Thanks.

---

