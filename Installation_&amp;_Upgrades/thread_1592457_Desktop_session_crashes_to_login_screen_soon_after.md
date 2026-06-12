---
title: "Desktop session crashes to login screen soon after logging in"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by scottywz on 2010-10-10
After upgrading my netbook (Eee 1005HA) from Ubuntu Lucid to Maverick, I can log in okay, but it crashes back to the login screen a couple of minutes after logging in, after the desktop has loaded.  I haven't been able to find anything in syslog/dmesg/etc. about why this is happening, but it isn't happening on my other laptop which I just upgraded to Maverick as well.  Any ideas as to what's going on?

Edit:  memtest86+ showed no errors and the live USB desktop works fine.

---

### Post by mörgæs on 2010-10-10
How does the machine work when booted with the live CD?

---

### Post by scottywz on 2010-10-10
I don't know; I'm running memtest right now.

---

### Post by scottywz on 2010-10-10
memtest finished without errors.  The Live USB does not exhibit this problem.

---

### Post by scottywz on 2010-10-10
Any ideas?

---

### Post by mionescu on 2010-10-10
Check to see if you have a hidden file in your home folder named .xsession-errors (something like that) and see if it contains any useful information.

---

### Post by scottywz on 2010-10-10
I did:  [http://www.pastie.org/1212146.txt]("http://www.pastie.org/1212146.txt")

Seeing stuff about Docky (which was weird because it's on my other computer which upgraded fine), I decided to update my sources and do an update via SSH, and the following packages were updated:
```
  dockmanager docky docky-dbg handbrake-cli handbrake-gtk libndesk-dbus1.0-cil
  mencoder mplayer python-dockmanager ttf-symbol-replacement virtualbox-3.2
  wine wine1.2 winetricks
```

The problem still exists.  So here's another xsession-errors:  [http://pastie.org/1212167.txt]("http://pastie.org/1212167.txt")

---

### Post by scottywz on 2010-10-11
So I decided to run tail -fn0 .xsession-errors over SSH to see when/where it crashes, and this appeared when it crashed:

```
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

** (gnome-settings-daemon:11580): WARNING **: Connection failed, reconnecting...
** Message: Got disconnected from the session message bus; retrying to reconnect every 10 seconds
** Message: <info>  disconnected by the session bus.

nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
SWT: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 11301 requests (11298 known processed) with 0 events remaining.
Do: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Docky: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 944 requests (943 known processed) with 0 events remaining.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 0 (Success) on X server :0.0.
```

And here's syslog starting at the crash: (**edit**ed with better log @ 00:37 CDT)
```
Oct 11 00:34:28 fomhar bonobo-activation-server (scottywz-12905): could not associate with desktop session: Error connecting: Connection refused
Oct 11 00:34:28 fomhar NetworkManager[805]: <error> [1286775268.759262] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Oct 11 00:34:28 fomhar acpid: client 12126[0:0] has disconnected
Oct 11 00:34:28 fomhar acpid: client connected from 12931[0:0]
Oct 11 00:34:28 fomhar acpid: 1 client rule loaded
Oct 11 00:34:28 fomhar kernel: [ 3405.017464] Skipping EDID probe due to cached edid
Oct 11 00:34:29 fomhar kernel: [ 3405.049347] Skipping EDID probe due to cached edid
Oct 11 00:34:29 fomhar NetworkManager[805]: <error> [1286775269.846456] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Oct 11 00:34:30 fomhar kernel: [ 3406.472193] Skipping EDID probe due to cached edid
Oct 11 00:34:30 fomhar kernel: [ 3406.513663] Skipping EDID probe due to cached edid
Oct 11 00:34:30 fomhar kernel: [ 3406.552218] Skipping EDID probe due to cached edid
Oct 11 00:34:30 fomhar kernel: [ 3406.588274] Skipping EDID probe due to cached edid
Oct 11 00:34:31 fomhar rtkit-daemon[1376]: Successfully made thread 12978 of process 12978 (n/a) owned by '105' high priority at nice level -11.
Oct 11 00:34:31 fomhar rtkit-daemon[1376]: Supervising 1 threads of 1 processes of 1 users.
Oct 11 00:34:31 fomhar kernel: [ 3407.452741] Skipping EDID probe due to cached edid
Oct 11 00:34:31 fomhar rtkit-daemon[1376]: Successfully made thread 12979 of process 12978 (n/a) owned by '105' RT at priority 5.
Oct 11 00:34:31 fomhar rtkit-daemon[1376]: Supervising 2 threads of 1 processes of 1 users.
Oct 11 00:34:32 fomhar rtkit-daemon[1376]: Successfully made thread 12980 of process 12978 (n/a) owned by '105' RT at priority 5.
Oct 11 00:34:32 fomhar rtkit-daemon[1376]: Supervising 3 threads of 1 processes of 1 users.
Oct 11 00:34:32 fomhar gdm-simple-greeter[12969]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 88.
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: snd_pcm_dump():
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: Soft volume PCM
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: Control: PCM Playback Volume
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: min_dB: -51
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: max_dB: 0
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: resolution: 256
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: Its setup is:
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   stream       : CAPTURE
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   access       : MMAP_INTERLEAVED
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   format       : S16_LE
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   subformat    : STD
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   channels     : 2
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   rate         : 44100
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   exact rate   : 44100 (44100/1)
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   msbits       : 16
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   buffer_size  : 88192
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   period_size  : 44096
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   period_time  : 999909
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   tstamp_mode  : ENABLE
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   period_step  : 1
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   avail_min    : 87310
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   period_event : 0
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   start_threshold  : -1
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   stop_threshold   : 1444937728
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   silence_threshold: 0
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   silence_size : 0
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   boundary     : 1444937728
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c: Its setup is:
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   stream       : CAPTURE
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   access       : MMAP_INTERLEAVED
Oct 11 00:34:33 fomhar pulseaudio[12978]: alsa-util.c:   format       : S16_LE
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   subformat    : STD
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   channels     : 2
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   rate         : 44100
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   exact rate   : 44100 (44100/1)
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   msbits       : 16
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   buffer_size  : 88192
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   period_size  : 44096
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   period_time  : 999909
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   tstamp_mode  : ENABLE
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   period_step  : 1
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   avail_min    : 87310
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   period_event : 0
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   start_threshold  : -1
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   stop_threshold   : 1444937728
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   silence_threshold: 0
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   silence_size : 0
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   boundary     : 1444937728
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   appl_ptr     : 87416
Oct 11 00:34:34 fomhar pulseaudio[12978]: alsa-util.c:   hw_ptr       : 87416
```

---

### Post by mörgæs on 2010-10-11
A lot of problems happened in the upgrade, it seems. Wouldn't a clean install of 10.10 be faster?

---

### Post by scottywz on 2010-10-11
It would be, and I plan on doing that, but I want to get to the bottom of this.  I'm trying to get an X backtrace right now.

---

### Post by scottywz on 2010-10-11
Filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/658139](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/658139)

---

### Post by metricus on 2010-10-12
this is not really the same behaviour but it's related:
I have an eee 701 (first batch :) )and I tried to install Maverick from usb.
Installer crashes somewhere at 77% while "configuring APT".

I tried to install directly without booting first from usb and after booting from usb.
BTW it works fine just of usb.

When installing directly it crashes to a blank screen and all I can do is cold reboot. After rebooting I get a grub error.

When installing after boot I get to re-login with ubuntu as username.

could be that in both cases the X-server crashes.
NOTE: I used Kubuntu image

---

### Post by X-Seti on 2011-01-04
Your not the only one having problems.

I have upgraded from 10.04?, 3 of my machines seem to crash the same way a part from my ATI box that does not seem to be affected in any way??

With me it seems to be where sound actions are used, so i've tried disabling window sound actions.

Also does the same crash reset to login with the TV tuner or VM player.

I've attached a session-error txt, maybe this might help/ assist others.

---

### Post by mörgæs on 2011-01-04
How do the machines behave when running a 10.10 live CD?

---

### Post by X-Seti on 2011-01-05
> **mörgæs said:**
> How do the machines behave when running a 10.10 live CD?

Runs ok for the most part, however I install Kaffeine and some Media extras + TV tuner firmware, and the crashes start to happen where the box resets back to the login screen?

---

### Post by mörgæs on 2011-01-07
I don't know much of TV tuners on Ubuntu, but in the first place what made you leave 10.04? It is supported until april 2013.

---

