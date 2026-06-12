---
title: "Total freeze after login (with custom kernel)"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by mindhaq on 2005-05-23
Hello everybody,

I just got into Ubuntu, and installed it on my PC at home. The install worked just fine, and I already installed some extra software (mostly following the unofficial kickstart guide).

Now I wanted to use a custom kernel, optimized for my hardware. I managed to build and install this custom kernel (using the latest universe version, I think 2.6.11). The boot process seems to go rather normal, and the Gnome-login-screen appears. When I login then, the desktop appears, the messages (starting services etc.) pass through and disappear, and the I am left with a brown desktop with the (empty) grey bars top and bottom. The mouse cursor stops responding, and it seems like the PC hangs; I can't even switch to a text login with ALT-CTRL-F1.

When I boot with the original kernel, everything works just fine.

I already scanned various logfile in /var/log, but can't find anything unusual, except that at freeze-time, no new log-messages appear. All those messages also appear when booting with the original kernel.

The last few in Xorg.0.log:
```
Could not init font path element unix/:7100, removing from list!
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```
The last few in syslog (I'm using a german locale):
```
May 23 13:18:11 localhost gconfd (rue-5706): (Version 2.10.0) wird gestartet, Prozesskennung 5706, Benutzer »rue«
May 23 13:18:11 localhost gconfd (rue-5706): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle aufgelöst
May 23 13:18:11 localhost gconfd (rue-5706): Die Adresse »xml:readwrite:/home/rue/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst
May 23 13:18:11 localhost gconfd (rue-5706): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle aufgelöst

```

Now, this obviously is a problem with the custom kernel, but I have absolutely no idea where I should start looking for problems. I already looked through the kernel-config, but didn't discover anything wrong.

Could anyone help me, or at least offer some direction?
Thanks a lot in advance!

My hardware:
CPU: Celeron 1000
Mainboard: MSI BX Master (has onboard Promise Ultra66 controller)
Graphic: Matrox G400 DH
Sound: Soundblaster Live5.1 Player
Mouse: MS Wireless Intellimouse Explorer

---

