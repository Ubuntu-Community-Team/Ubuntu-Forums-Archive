---
title: "No internet after dist-upgrade"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by viking777 on 2016-01-29
Hello again Ubuntuers! Haven't been here in a while as 14.04 LTS has been running without problems for ages. But today it isn't. I did a fairly big upgrade including the following packages:


```
libnl-genl-3-200 , libstdc++-4.8-dev , libasan0 , libsystemd-login0 , mysql-server-core-5.5 , libx32stdc++-4.8-dev , libquadmath0 , gcc-4.8-base , mysql-client-core-5.5 , systemd-services , gcc-4.8-multilib , lib32stdc++6 , libx32gcc-4.8-dev , firefox-locale-en , cpp-4.8 , libgomp1 , lib32gcc-4.8-dev , libtsan0 , libx32asan0 , firefox , openssh-server , libsystemd-daemon0 , libgudev-1.0-0 , libx32itm1 , lib32stdc++-4.8-dev , chromium-codecs-ffmpeg-extra , libpam-systemd , openssh-sftp-server , libx32gomp1 , libx32atomic1 , udev , libnl-3-200 , curl , libatomic1 , chromium-browser-l10n , gir1.2-gudev-1.0 , g++-4.8 , lib32asan0 , libudev1 , openssh-client , libgcc-4.8-dev , mysql-common , gcc-4.8 , libsystemd-journal0 , libmysqlclient18 , libx32quadmath0 , lib32gomp1 , lib32atomic1 , lib32itm1 , libcurl3 , passwd , libgfortran3 , login , libx32stdc++6 , g++-4.8-multilib , libnl-route-3-200 , libstdc++6 , chromium-browser , lib32quadmath0 , libitm1 , libcurl3-gnutls , yad 

```

Since then all traces of internet connection have gone. I don't just mean I can't connect to 'google.com' it is far deeper than that. For example if I attempt to run 'NetworkManager' I get the following error:

```
sudo NetworkManager 

(NetworkManager:2831): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Key file does not have group 'connectivity'
```

If I attempt to run nm-applet I get the following error:
```

sudo nm-applet

** (nm-applet:2878): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

(nm-applet:2878): nm-applet-WARNING **: Error connecting to ModemManager: Error calling StartServiceByName for org.freedesktop.ModemManager1: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file not found or permissions invalid

(nm-applet:2878): nm-applet-WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
nm-applet-Message: using fallback from indicator to GtkStatusIcon

```

If I attempt to run ifup I get the following errors:

```
sudo ifup eth0
Ignoring unknown interface eth0=eth0

sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0
```

In the absence of any of those programs I have no idea how to proceed. 

Let me tell you what I can do. 

I can restore a disk image from 5 days ago and all is well again, everything works perfectly, but I am faced with the same upgrades as posted above and as soon as I install them the situation returns. 

I am able to chroot into 14.04 from another distro and update it that way, but at the time of writing there are no further updates available. 

The problem is certainly in one of the upgrades posted earlier, though I have no idea which one. I see the name 'systemd' rears its ugly head in that list so maybe I have my suspicions, but my prejudices are not conclusive evidence. 

Anybody got any ideas as to what I can do about this?

---

### Post by ajgreeny on 2016-01-29
Do you have the proposed repos enabled?

See [http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705) if so, and see if disabling them and then forcing a downgrade of those packages mentioned helps.

---

### Post by viking777 on 2016-01-30
@ajgreeny - Thanks very much for pointing out the link to that thread, that fixed the issue for me. Posting this reply from Ubuntu:D

---

### Post by ajgreeny on 2016-01-30
Brilliant!

Please mark as SOLVED from the Thread Tools menu at thr top.
Done on your behalf.

---

