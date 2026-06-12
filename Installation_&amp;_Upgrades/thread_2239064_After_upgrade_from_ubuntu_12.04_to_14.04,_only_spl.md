---
title: "After upgrade from ubuntu 12.04 to 14.04, only splash screen is visible after login"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by manickam2 on 2014-08-11
Pls help. My system seems to be compeltely hosed. The following things are happening:

* "system program problem detected" alert pops up repeatedly 5/6 times
* only blank splash screen is visible. No launcher is visible.
* In syslog, Iam getting these errors repeatedly continuously:

Aug 12 04:19:16 manickam-Aspire-5738 rtkit-daemon[1607]: Successfully made thread 4212 of process 4212 (n/a) owned by '1000' high priority at nice level -11.
Aug 12 04:19:16 manickam-Aspire-5738 rtkit-daemon[1607]: Supervising 1 threads of 1 processes of 1 users.
Aug 12 04:19:16 manickam-Aspire-5738 pulseaudio[4208]: [pulseaudio] main.c: Daemon startup failed.
Aug 12 04:19:18 manickam-Aspire-5738 pulseaudio[4366]: [pulseaudio] authkey.c: Failed to open cookie file '/home/manickam/.config/pulse/cookie': No such file or directory
Aug 12 04:19:18 manickam-Aspire-5738 pulseaudio[4366]: [pulseaudio] authkey.c: Failed to load authorization key '/home/manickam/.config/pulse/cookie': No such file or directory
Aug 12 04:19:18 manickam-Aspire-5738 rtkit-daemon[1607]: Successfully made thread 4370 of process 4370 (n/a) owned by '1000' high priority at nice level -11.
Aug 12 04:19:18 manickam-Aspire-5738 rtkit-daemon[1607]: Supervising 1 threads of 1 processes of 1 users.
Aug 12 04:19:18 manickam-Aspire-5738 pulseaudio[4370]: [pulseaudio] pid.c: Stale PID file, overwriting.
Aug 12 04:19:18 manickam-Aspire-5738 pulseaudio[4366]: [pulseaudio] main.c: Daemon startup failed.

---

### Post by manickam2 on 2014-08-12
Also Iam getting "Unknown Job: unity-panel-service" If I run unity from cmdline... Pls help

---

### Post by kansasnoob on 2014-08-13
I'm clueless but I'll give you a free bump in hopes a pair of fresh eyes may be able to help.

---

### Post by interglossa on 2014-08-13
May I assume you did this from the update manager (clicking the Upgrade button next to the 'New Ubuntu release 14.04.1 LTS is available' message)?

---

### Post by ubfan1 on 2014-08-13
Do you get a normal login through the guest account?  A quick and dirty fix might be to rename your .config directory to .config-old, make an empty .config directory and see if that gives you the launcher, then move or copy back the subdirectories in .config-old a few at a time to see where the problem lies.  You should still be able to login via one of the virtual terms (Alt-Crtl-Fn1  through Fn6), getting back to the X screen with Alt-F7 (note, no ctrl here).

---

