---
title: "boot problem"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by Kaparen on 2005-10-05
two days ago I manually installed my Nvidia drivers and everythign worked ok, I rebooted twice just to see if Ubuntu would startup correctly. Everything worked ok. Yesterday I never booted Ubuntu, only using my XP Pro. Today I start up Ubuntu and everything is OK until the moment where the Nvidia splash usually comes up, instead the screen flickers three times and finally leaves me with a blank screen. I press some random keys and the blue screen comes up telling me (never read it so Im only guessing) that something is wrong with the X-server, probably some settings.

So I rolled back my xorg.conf to my xorg.conf.backup and made the changes again:

#dri
"nvidia"
and so on...

and now everything is working allright again.
My question is, how can something that works allright one day, not work the next day? No changes were made in any files so I cant really see how this could be. :rolleyes: 

thanks!

---

### Post by Kaparen on 2005-10-06
well it happened again. The screen just flickers three times and then halts.
Ubuntu worked great yesterday when I shut off the computer, gf have been using XP  today so nothing has been altered.

when I check the logfile i come up with these warning:

(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) NV(0): config file hsync range 30-68kHz not within DDC hsync ranges.
(WW) NV(0): config file vrefresh range 50-70Hz not within DDC vrefresh ranges.
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

update:

(EE)NVIDIA(0) Failed to load the NVIDIA kernel module
(EE)NVIDIA(0)***Aborting***
(EE)Screen(s) found, but none have a usuable configuration

someone must have had this problem before me.

---

