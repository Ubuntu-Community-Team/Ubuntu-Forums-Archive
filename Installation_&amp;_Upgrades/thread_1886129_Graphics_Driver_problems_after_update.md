---
title: "Graphics Driver problems after update"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by learning_ on 2011-11-24
So I ran an update a couple weeks ago then rebooted, made sure everything was ok, then didnt touch it until last night. Well once I turned it on, my grub list was loaded with 8 new entries of new ubuntu kernel versions, and with any of them when I go to boot up ubuntu I get an error before login saying something along the lines of "Graphics driver failed, what do you wanna do about it?" It gives me four options, I can't remember any except the last option (restart X). Furthermore, after login, all the graphics are on the lowest settings (resolution stays the same), my compiz features are disabled, and in general the graphical features are just abnormally clunky.

tl;dr graphics driver and features are screwed up after an update, why?

---

### Post by raja.genupula on 2011-11-24
reinstall the graphics drivers . If it not solved the issue then
do 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by learning_ on 2011-11-24
pretty much solved. the compiz features i'm having to go back in and enable manually & individually. it seems as though with anything related to the graphics, my system just reverted back to total default settings. Could you provide insight as to why this might have happened?

---

### Post by MAFoElffen on 2011-11-24
> **learning_ said:**
> So I ran an update a couple weeks ago then rebooted, made sure everything was ok, then didnt touch it until last night. Well once I turned it on, my grub list was loaded with 8 new entries of new ubuntu kernel versions, and with any of them when I go to boot up ubuntu I get an error before login saying something along the lines of "Graphics driver failed, what do you wanna do about it?" It gives me four options, I can't remember any except the last option (restart X). Furthermore, after login, all the graphics are on the lowest settings (resolution stays the same), my compiz features are disabled, and in general the graphical features are just abnormally clunky.

tl;dr graphics driver and features are screwed up after an update, why?
- What version of Ubuntu are you running?
- What video card do you have?
```

lspci -vnn | grep VGA

```Please post your /var/log/apt/history.log so that we can see what packages were updated with what.

Please post your /var/log/Xorg.0.log for me to see what graphics error it might be getting.
> tl;dr graphics driverWhat are you trying to say there?

---

### Post by learning_ on 2011-11-24
I am running 10.04 Ubuntu, nVidia Corporation G92 [GeForce GTS 250]

as for the /var/log/apt/history.log:
```

Start-Date: 2011-11-14  10:53:20
Install: linux-headers-2.6.32-35 (2.6.32-35.78), linux-image-2.6.32-35-generic (2.6.32-35.78), linux-headers-2.6.32-35-generic (2.6.32-35.78)
Upgrade: libgtk2.0-common (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), libgail18 (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), linux-headers-generic (2.6.32.34.40, 2.6.32.35.41), xulrunner-1.9.2 (1.9.2.23+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.24+build2+nobinonly-0ubuntu0.10.04.1), libgail-common (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), linux-image-generic (2.6.32.34.40, 2.6.32.35.41), gtk2-engines-pixbuf (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), apache2.2-bin (2.2.14-5ubuntu8.6, 2.2.14-5ubuntu8.7), linux-libc-dev (2.6.32-34.77, 2.6.32-35.78), firefox (3.6.23+build1+nobinonly-0ubuntu0.10.04.1, 3.6.24+build2+nobinonly-0ubuntu0.10.04.1), adobe-flashplugin (11.0.1.152-0lucid1, 11.1.102.55-0lucid1), libgtk2.0-bin (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), multisystem (1.0145, 1.0151), libgtk2.0-dev (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), tzdata-java (2011m-0ubuntu0.10.04, 2011n-0ubuntu0.10.04), adobe-flash-properties-gtk (11.0.1.152-0lucid1, 11.1.102.55-0lucid1), firefox-gnome-support (3.6.23+build1+nobinonly-0ubuntu0.10.04.1, 3.6.24+build2+nobinonly-0ubuntu0.10.04.1), tzdata (2011m-0ubuntu0.10.04, 2011n-0ubuntu0.10.04), libmodplug0c2 (0.8.7-1ubuntu0.2, 0.8.7-1ubuntu0.3), libservlet2.5-java (6.0.24-2ubuntu1.7, 6.0.24-2ubuntu1.9), firefox-branding (3.6.23+build1+nobinonly-0ubuntu0.10.04.1, 3.6.24+build2+nobinonly-0ubuntu0.10.04.1), google-chrome-stable (15.0.874.106-r107270, 15.0.874.120-r108895), linux-generic (2.6.32.34.40, 2.6.32.35.41), libgtk2.0-0 (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1)
End-Date: 2011-11-14  10:56:44
``` then ```
Start-Date: 2011-11-17  09:11:10
Upgrade: bind9-host (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), icedtea6-plugin (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), dnsutils (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), libdns64 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), icedtea-6-jre-cacao (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), google-talkplugin (2.3.2.0-1, 2.4.5.0-1), libisccc60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), liblwres60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), openjdk-6-jre-headless (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), multisystem (1.0151, 1.0152), openjdk-6-jre (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), openjdk-6-jre-lib (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), libbind9-60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), libisccfg60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), google-chrome-stable (15.0.874.120-r108895, 15.0.874.121-r109964), python-papyon (0.4.8-0ubuntu2, 0.4.8-0ubuntu2.1), libisc60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4)
End-Date: 2011-11-17  09:12:02
```
and the /var/log/Xorg.0.log
i'll add as an attachment because of its length

---

### Post by MAFoElffen on 2011-11-24
> **learning_ said:**
> I am running 10.04 Ubuntu, nVidia Corporation G92 [GeForce GTS 250]
The apt history has a GLX update, but Your Xorg log shows that GLX (and everything else xorg and graphics driver related) is currently loading just fine...

If it was compiz related, then 
```

sudo dkg-reconfigure compiz

```
will take care of that.

The one thing I didn't see in your xorg log was anywhere where it see's your display.  It does say it is using the port CRT-1, where it see's "Acer X193W" as a display.  You might probe it from nvidia-settings... If you have a resolution problem, tell me and we'll work on that.

---

