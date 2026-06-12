---
title: "Pulseaudio errors"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-10-10
Are other people gettings these log messages on each boot?

Oct 11 11:04:42 PPP pulseaudio[5872]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 11 11:04:42 PPP pulseaudio[5876]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Oct 11 11:04:42 PPP pulseaudio[5876]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

And I notice that sometimes pulseaduio causes totem to segfault:

Oct 11 12:24:19 PPP kernel: [ 4843.989810] totem[8376]: segfault at 240ba640 ip 00007fec51889b27 sp 000000004391dd40 error 6 in libpulse.so.0.4.1[7fec51851000+4e000]
Oct 11 12:24:50 PPP kernel: [ 4875.066585] totem[8415]: segfault at b5eec30 ip 00007f6f3470cb27 sp 000000004142fd80 error 6 in libpulse.so.0.4.1[7f6f346d4000+4e000]

---

### Post by FuturePilot on 2008-10-10
I can confirm the Operation not permitted errors.

---

### Post by ktp on 2008-10-10
Doesn't the Operation not permitted errors because the user is not in pulse-* groups.

---

### Post by elcman on 2008-10-10
Did this barely start happening with the latest update? If so, I can confirm those errors, too. I'll try adding my user to that group and see what happens, though.

---

### Post by ShirishAg75 on 2008-10-12
nullack, 
 you can find atleast one of the errors even while just looking up the version of pulseaudio. 

```

pulseaudio --version
W: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio 0.9.10

```

:(

---

### Post by Nullack on 2008-10-12
It seems to me these startup bugs have been around for sometime in Intrepid.

---

### Post by ShirishAg75 on 2008-10-12
from where you got the log of the startup ?

---

### Post by plun on 2008-10-13
I have these within /.xsession-errors

```
gnome-session[11179]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```


So my login sound is broken and also the dlopen error

---

### Post by taavikko on 2008-10-13
Confirmed...

If pulseaudio requires user to belong in pulse-groups, why isn't user 
added to them automatically ?


[I] uptime
 12:39:24 up  1:32,  2 users,  load average: 0.11, 0.34, 0.35
jumala@helvetti:~$ LANG=C cat /var/log/messages |grep -i pulse
Oct  7 23:10:41 helvetti pulseaudio[6160]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 04:47:01 helvetti pulseaudio[6160]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 10:31:03 helvetti pulseaudio[6160]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 12:00:08 helvetti pulseaudio[6160]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 13:32:23 helvetti pulseaudio[6262]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct  8 13:32:23 helvetti pulseaudio[6262]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Toiminto ei ole sallittu
Oct  8 13:32:23 helvetti pulseaudio[6262]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Toiminto ei ole sallittu
Oct  8 13:32:24 helvetti pulseaudio[6262]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct  8 13:32:25 helvetti pulseaudio[6262]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct  8 13:32:27 helvetti pulseaudio[6262]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 14:15:16 helvetti pulseaudio[6262]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 18:36:34 helvetti pulseaudio[6262]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct  8 19:04:24 helvetti pulseaudio[6262]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 20:50:03 helvetti pulseaudio[6262]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 21:17:22 helvetti pulseaudio[6435]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct  8 21:17:22 helvetti pulseaudio[6435]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Toiminto ei ole sallittu
Oct  8 21:17:22 helvetti pulseaudio[6435]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Toiminto ei ole sallittu
Oct  8 21:17:23 helvetti pulseaudio[6435]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct  8 21:17:23 helvetti pulseaudio[6435]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct  8 21:17:25 helvetti pulseaudio[6435]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  8 22:49:16 helvetti pulseaudio[6435]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  9 13:04:13 helvetti pulseaudio[6435]: protocol-native.c: Denied access to client with invalid authorization data.
Oct  9 18:31:49 helvetti pulseaudio[6435]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 10 10:15:19 helvetti pulseaudio[6166]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 10 10:15:19 helvetti pulseaudio[6172]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Toiminto ei ole sallittu
Oct 10 10:15:19 helvetti pulseaudio[6172]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Toiminto ei ole sallittu
Oct 10 10:15:19 helvetti pulseaudio[6172]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 10 10:15:19 helvetti pulseaudio[6172]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 10 10:15:19 helvetti pulseaudio[6179]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 10 10:15:21 helvetti pulseaudio[6172]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 10 18:49:01 helvetti pulseaudio[6205]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 10 18:49:01 helvetti pulseaudio[6211]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Toiminto ei ole sallittu
Oct 10 18:49:01 helvetti pulseaudio[6211]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Toiminto ei ole sallittu
Oct 10 18:49:01 helvetti pulseaudio[6211]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 10 18:49:01 helvetti pulseaudio[6211]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 10 18:49:02 helvetti pulseaudio[6218]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 10 18:49:04 helvetti pulseaudio[6211]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 11 21:20:36 helvetti pulseaudio[6211]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 11 21:34:59 helvetti pulseaudio[6211]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 11 21:51:57 helvetti pulseaudio[6211]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 11 22:25:49 helvetti pulseaudio[6211]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 11 23:00:27 helvetti pulseaudio[6211]: protocol-native.c: Denied access to client with invalid authorization data.
Oct 13 11:07:47 helvetti pulseaudio[5869]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 13 11:07:47 helvetti pulseaudio[5879]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Toiminto ei ole sallittu
Oct 13 11:07:47 helvetti pulseaudio[5879]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Toiminto ei ole sallittu
Oct 13 11:07:48 helvetti pulseaudio[5879]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 13 11:07:48 helvetti pulseaudio[5879]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 13 11:07:48 helvetti pulseaudio[5888]: ltdl-bind-now.c: Failed to find original dlopen loader.
jumala@helvetti:~$ groups
jumala adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
[/I]

---

