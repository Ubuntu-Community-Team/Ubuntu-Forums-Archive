---
title: "gnome-settings-daemon fails to start"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by getaboat on 2008-08-14
This has been a painful upgrade from Feisty to Hardy - with lots of problems along the way but I now have a Hardy system - but with a few problems:

The first is that the gnome-settings-daemon fails to start. On start up this causes me to have to log in twice - after going through various attempts at restarting I get a - seemingly working - desktop (I haven't tried everything yet). Going into terminal and trying to start manually gives:
```

Shutdown failed or nothing to shut down.
[1218694977,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the applicationCould not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

The other is with the nvdia glx drivers needed for desktop effects. I am sure this caused the feisty to gutsy upgrade to fail - but left me able to start the upgrade from gutsy to hardy. I have previously used envy to sort out my nvidia issues. When trying to install with apt-get I get this
```

Unpacking nvidia-glx (from .../nvidia-glx_1%3a96.43.05+2.6.24.13-19.45_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13

```

Finally (for the time being I expect) with two upgrades that failed to run their full course I find that quite a bit of disk space seems to have disappeared and I suspect that they failed to clean up - how can I do that manually? 

Thanks

---

### Post by Partyboi2 on 2008-08-14
> The other is with the nvdia glx drivers needed for desktop effects. I am sure this caused the feisty to gutsy upgrade to fail - but left me able to start the upgrade from gutsy to hardy. I have previously used envy to sort out my nvidia issues. When trying to install with apt-get I get this
     Code:
     Unpacking nvidia-glx (from .../nvidia-glx_1%3a96.43.05+2.6.24.13-19.45_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13 
Finally (for the time being I expect) with two upgrades that failed to run their full course I find that quite a bit of disk space seems to have disappeared and I suspect that they failed to clean up - how can I do that manually? You could give [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=415957") a try.

Edit: for the other problem you could try downgrading the liboil package, have a look at [[COLOR=Blue]this bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/72814")

---

### Post by getaboat on 2008-08-14
Thanks yes I have done lots of searching and I have been to that post and it was along the lines - but dpkg would not break the divert.

The daemon problems and the nvidia problem are linked. I tried loads of things to get rid of the diversion problem as I had a hunch that was causing me problems. 

In the end I think it was a re-install ovidia_glx_new and then a purge of the same that seemed to fix it. I had installed envyng (envy has dug me out of nvidia holes before) and this seems to make thing worse.

When running with the restricted drivers for desktop effects my screen looks Yuk so I am going to give envy another go.

---

