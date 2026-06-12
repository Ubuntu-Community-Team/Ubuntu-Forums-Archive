---
title: "Serous stability issues in recent Hardy Upgrades"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by ExecutorE on 2008-02-08
This may be in the wrong forum; I'm new at this, and Hardy seems like it's an upgrade. I seem to be suffering a whole gamut of stability problems, following the upgrades installed by the upgrade manager a couple days ago. I'm running Xubuntu on an Acer Aspire 7250.Here's the short summay:

1) external mouse buttons only register as doubre-clicks. Manual workarounds posted here and in the bug system have no effect. Touchpad buttons work fine.
2) nVidia driver does not load, defaulting me to VESA at 640x480 on every boot. Workarounds, such an manually rewriting xorg.conf, have no effect. The process goes as follows:
   2a)reboot. WM tells me it's running in "low graphics mode." Clicking "configure," and cofiguring, has no effect.
   2b) login screen is 800x640. Upon login, it defaults to 640x480.
   2c) in terminal, run displayconfig-gtk as root (as normal user has no effect). Set monitor, driver (driver is nv, nvidia fails). Am told to logout.
   2d) upon re-login, screen downshfts to non-widescreen version with same vertical resorution. Must re-set resolution in displayconfig-gtk again. this time it stays, until next reboot.
3) Sound does not come out of the headphone jacks for my nvidia/intel-HDA soundcard (only speakers). manually re-writing alsasound following posted workarounds has no effect.
4) Thunar occasionally cannot close windows. If I manually end the process in the system monitor, they close. If I force kill them in a terminal, xfwm4 crashes. I can manually restart xfwm4 in a terminal.
5) deluge-torrent crashes out with no errors in the terminal, but output to dmesg (see below), after a maximum of about a minute running time.
6) running audacity sometimes hard-freezes the WM, with no error in the terminal, and no output to dmesg. CTRL-ALT-BACK is the only way to get the WM back returning me to the state of 2d).
7) for many of these errors, the crash reporter itself crashes, so I cannot submit proper bug reports.
eight) gxine - but not the xine-provided UI - cannot play more than about three seconds into a file before hard-freezing. Occasionally this locks th WM as well. 

Here are the errors from deluge and xfwm4 (and perhaps gxine):

```
[10676.103927] npviewer.bin[7895]: segfault at f5cb5030 rip f78de540 rsp ff9663fc error 4
[10717.037600] deluge[8529] general protection rip:7f2469444d1b rsp:7fff7b493f50 error:0
[10768.110186] deluge[8721] general protection rip:7fe3041fed1b rsp:7fff1624bd00 error:0
[10814.928400] deluge[8918] general protection rip:7ff82f854d1b rsp:7fff418a4360 error:0
[11141.193727] xfwm4[8863] trap int3 rip:7f7954e62f97 rsp:7fff604aedd0 error:0
[11146.131940] npviewer.bin[9076]: segfault at f5d2a030 rip f7953540 rsp ffd9e82c error 4
[11147.714497] apport-gtk[9367]: segfault at 8 rip 7ff8e641b040 rsp 7ffff1d683b0 error 4
[11187.869672] deluge[9749] general protection rip:7fd0c5897d1b rsp:7fffd78e73a0 error:0
[11720.552438] audacity[10539]: segfault at 62 rip 504906 rsp 7ffffa098738 error 4
[15895.387669] deluge[11013] general protection rip:7f550b727d1b rsp:7fff1d777230 error:0
[15955.319107] deluge[11051] general protection rip:7fcf90261d1b rsp:7fffa21aa730 error:0
[16128.500186] deluge[11124] general protection rip:7fb659abad1b rsp:7fff6bb0a5c0 error:0
[16228.517467] xfwm4[9673] trap int3 rip:7f95a04b9f97 rsp:7fffabb08e30 error:0
[16248.875398] npviewer.bin[10093]: segfault at f5ca5030 rip f78ce540 rsp ffcbbf4c error 4

```

These are, I'm sure, many unrelated errors, but - aside from 2) and 3), which have been present from the base Gutsy install - all began within the last couple days. Being new to Ubuntu (my normal system is Gentoo), I'm not sure where to start debugging. I hope some of you can help, as these are all serious frustrations.

Thanks,

EE

---

### Post by jasmuz on 2008-02-08
You MUST REMEMBER, Hardy Heron is still under alpha development, wich isnt meant to be on used on production day-to-day machines, because of the propensity to give such errors.

If you want to be using a stable version, then install Gutsy Gibbon aka 7.10 and have it updated.

---

### Post by zvacet on 2008-02-08
Don´t be frustrated.Hardy will be stabile in april.Until then you will face this kind of problems regulary,because Hardy is still under development(alpha release).If you wish to try ubuntu install Gutsy and when Hardy becomes stable you can upgrade.

---

### Post by ExecutorE on 2008-02-09
Hi both,

yes, I'm well aware that HH is unstable. Isn't the purpose of an alpha release to test for bugs? Well, here are some. But if you're unwilling to help with those, can you give some advice on 2 and 3? Both of those predate my update to Hardy, so I don't think they have to do with it. The workarounds posted here don't help. GG, after all, is nominally stable, and neither audio nor video worked properly.

Thanks,

EE

---

### Post by Partyboi2 on 2008-02-09
[Here]("http://ubuntuforums.org/forumdisplay.php?f=305") is a good place to get assistance with hardy related problems. (Just in case you didn't know :))
> 2) nVidia driver does not load, defaulting me to VESA at 640x480 on every boot. Workarounds, such an manually rewriting xorg.conf, have no effect. The process goes as follows:
   2a)reboot. WM tells me it's running in "low graphics mode." Clicking "configure," and cofiguring, has no effect.try booting into recovery mode from grub and choose the option to fix xserver.

---

### Post by buntunub on 2008-05-08
> **zvacet said:**
> Don´t be frustrated.Hardy will be stabile in april.Until then you will face this kind of problems regulary,because Hardy is still under development(alpha release).If you wish to try ubuntu install Gutsy and when Hardy becomes stable you can upgrade.

[PHP]May  8 16:39:26 desktop kernel: [25396.300782] Xorg[8379]: segfault at 8 rip 7f7be68db850 rsp 7ffff28fd540 error 4
May  8 16:40:38 desktop kernel: [25468.615307] gdm[5986]: segfault at 268 rip 7f86064bdbcb rsp 7fff1225b7a0 error 4[/PHP]

:lolflag:

As you can see, this just happened. Not the first time either on what was a rock solid system in Gutsy. There is indeed some extremely serious stability issues with Hardy, and this is now post release. I hear Canonical is going to release a major patch with fixes for "Hardy's Hurtin", formerly known as Hardy Heron. That is what everyone I know who used to be Ubuntu fans are calling it.

---

