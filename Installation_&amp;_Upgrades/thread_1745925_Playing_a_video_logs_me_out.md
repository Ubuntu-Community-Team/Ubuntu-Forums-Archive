---
title: "Playing a video logs me out"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by kartik_vad on 2011-05-01
When  I try to play a video in vlc, totem or banshee, it immediately logs me out. Sometimes this happens when I try to full screen the video. This seems to happen only after upgrading to ubuntu 11, and happens for multiple kinds of files, like avi and m4v. The motherboard is Asus a8v-mx. Please help me fix my ubuntu installation. Thanks.

Here are the relevant entries from syslog:

 21:12:27 enlightenment kernel: [  488.157457] powernow-k8: Hardware error - pending bit very stuck - no further pstate changes possible
May  1 21:12:27 enlightenment kernel: [  488.158634] powernow-k8: transition frequency failed
May  1 21:12:27 enlightenment kernel: [  488.264015] powernow-k8: failing targ, change pending bit set
May  1 21:12:27 enlightenment kernel: [  488.306466] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
May  1 21:12:27 enlightenment kernel: [  488.306489] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
May  1 21:12:27 enlightenment kernel: [  488.306562] pci 0000:01:00.0: putting AGP V3 device into 8x mode
May  1 21:12:27 enlightenment kernel: [  488.372044] powernow-k8: error - out of sync, fix 0x2 0xa, vid 0x4 0x4
May  1 21:12:27 enlightenment kernel: [  488.372055] powernow-k8: ph2 null fid transition 0xa
May  1 21:12:30 enlightenment rtkit-daemon[1304]: Successfully made thread 1987 of process 1987 (n/a) owned by '105' high priority at nice level -11.
May  1 21:12:30 enlightenment rtkit-daemon[1304]: Supervising 1 threads of 1 processes of 1 users.
May  1 21:12:30 enlightenment rtkit-daemon[1304]: Successfully made thread 1988 of process 1987 (n/a) owned by '105' RT at priority 5.
May  1 21:12:30 enlightenment rtkit-daemon[1304]: Supervising 2 threads of 1 processes of 1 users.
May  1 21:12:30 enlightenment rtkit-daemon[1304]: Successfully made thread 1989 of process 1987 (n/a) owned by '105' RT at priority 5.
May  1 21:12:30 enlightenment rtkit-daemon[1304]: Supervising 3 threads of 1 processes of 1 users.
May  1 21:12:32 enlightenment gdm-simple-greeter[1975]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
May  1 21:12:32 enlightenment gdm-simple-greeter[1975]: WARNING: Unable to load CK history: no seat-id found
May  1 21:12:34 enlightenment gdm-session-worker[1978]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  1 21:12:38 enlightenment gdm-session-worker[1978]: pam_sm_authenticate: Called
May  1 21:12:38 enlightenment gdm-session-worker[1978]: pam_sm_authenticate: username = [rama]
May  1 21:12:39 enlightenment rtkit-daemon[1304]: Successfully made thread 2108 of process 2108 (n/a) owned by '1000' high priority at nice level -11.
May  1 21:12:39 enlightenment rtkit-daemon[1304]: Supervising 4 threads of 2 processes of 2 users.
May  1 21:12:39 enlightenment pulseaudio[2108]: pid.c: Stale PID file, overwriting.
May  1 21:12:39 enlightenment rtkit-daemon[1304]: Successfully made thread 2111 of process 2108 (n/a) owned by '1000' RT at priority 5.
May  1 21:12:39 enlightenment rtkit-daemon[1304]: Supervising 5 threads of 2 processes of 2 users.
May  1 21:12:39 enlightenment rtkit-daemon[1304]: Successfully made thread 2112 of process 2108 (n/a) owned by '1000' RT at priority 5.
May  1 21:12:39 enlightenment rtkit-daemon[1304]: Supervising 6 threads of 2 processes of 2 users.

---

### Post by enriqueenforo on 2011-06-30
It seems that I am experiencing a similar problem each time I try to enlarge or move de video window. I am using ubuntu 11 and VLC or Banshee

---

### Post by jerrrys on 2011-06-30
is your video card supported?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=video+card+support+natty+11.04&sa=Search&cof=FORID:9#1061](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=video+card+support+natty+11.04&sa=Search&cof=FORID:9#1061)

---

### Post by enriqueenforo on 2011-07-14
> **jerrrys said:**
> is your video card supported?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=video+card+support+natty+11.04&sa=Search&cof=FORID:9#1061](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=video+card+support+natty+11.04&sa=Search&cof=FORID:9#1061)


I could not find information about my card in the link you kindly sent me.
VGA compatible controller [0300]: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] [1106:3108] (rev 01)

Any idea would be appreciated. I am not an expert enjoying my first contact with ubuntu!

---

