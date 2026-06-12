---
title: "brightness issues"
date: 2009-05-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jon.reeve on 2009-05-31
Almost every time I log in or wake up from from suspend, the brightness on my laptop starts to freak out, oscillating between different brightness levels, and using a lot of CPU power. A box appears on the desktop where the old (circa Intrepid) brightness indicator would have been. Switching to a console (ctrl+alt+f2) while this is happening logs me out for some reason. 

I can fix this by logging out and logging back in a couple times. Usually it works by about the third time or so I log out and log back in. 

This doesn't seem to be related to exa/uxa or kernel mode setting, because changing these configurations doesn't seem to affect the problem. I also don't think it's something with Power Management settings, because this happens on both AC and battery power, and changing the preferences there doesn't seem to affect anything. 

Here are some logs that may or may not be relevant: 

May 30 15:04:48 pia kernel: [   36.520173] integrated sync not supported
May 30 15:04:48 pia kernel: [   36.804170] integrated sync not supported
May 30 15:04:48 pia kernel: [   37.080175] integrated sync not supported
May 30 15:04:52 pia kernel: [   41.136237] integrated sync not supported
May 30 15:05:26 pia kernel: [   74.736338] gvfs-gdu-volume[4741]: segfault at c ip 0065ffda sp bfdf6c10 error 4 in libgdu.so.0.0.0[657000+22000]
May 30 15:05:38 pia kernel: [   87.120151] gvfs-gdu-volume[5034]: segfault at c ip 0050bfda sp bfe725b0 error 4 in libgdu.so.0.0.0[503000+22000]
May 30 15:05:44 pia kernel: [   92.772304] mixer_applet2[4058]: segfault at aaaaaaac ip 00230be2 sp bfaf1a90 error 4 in libglib-2.0.so.0.2100.0[20d000+c3000]
May 30 15:05:46 pia kernel: [   94.956223] integrated sync not supported
May 30 15:05:46 pia kernel: [   95.240227] integrated sync not supported
May 30 15:05:48 pia kernel: [   96.452239] integrated sync not supported
May 30 15:05:51 pia pulseaudio[5334]: pid.c: Stale PID file, overwriting.
May 30 15:05:53 pia kernel: [  101.876205] integrated sync not supported
May 30 15:05:53 pia kernel: [  102.156170] integrated sync not supported
May 30 15:05:54 pia kernel: [  102.436207] integrated sync not supported
May 30 15:05:57 pia kernel: [  105.448172] integrated sync not supported
May 30 15:06:14 pia kernel: [  123.376261] integrated sync not supported
May 30 15:06:15 pia kernel: [  123.652237] integrated sync not supported
May 30 15:06:16 pia kernel: [  124.836227] integrated sync not supported
May 30 15:06:20 pia pulseaudio[5981]: pid.c: Stale PID file, overwriting.
May 30 15:06:22 pia kernel: [  130.436180] integrated sync not supported
May 30 15:06:22 pia kernel: [  130.716174] integrated sync not supported
May 30 15:06:22 pia kernel: [  130.996176] integrated sync not supported
May 30 15:06:25 pia kernel: [  134.256363] integrated sync not supported
May 30 15:06:30 pia bonobo-activation-server (jon-6227): could not associate with desktop session: Failed to connect to socket /tmp/dbus-A933wHNT6o: Connection refused
May 30 15:07:17 pia kernel: [  185.424992] gvfs-gdu-volume[7108]: segfault at c ip 006ccfda sp bfe12650 error 4 in libgdu.so.0.0.0[6c4000+22000]
May 30 15:07:23 pia kernel: [  192.085630] mixer_applet2[6171]: segfault at aaaaaaac ip 0039dbe2 sp bf87d150 error 4 in libglib-2.0.so.0.2100.0[37a000+c3000]
May 30 15:07:25 pia kernel: [  194.144226] integrated sync not supported
May 30 15:07:26 pia kernel: [  194.420241] integrated sync not supported
May 30 15:07:27 pia kernel: [  195.604226] integrated sync not supported
May 30 15:07:31 pia pulseaudio[7427]: pid.c: Stale PID file, overwriting.
May 30 15:07:33 pia kernel: [  201.572191] integrated sync not supported
May 30 15:07:33 pia kernel: [  201.852172] integrated sync not supported
May 30 15:07:33 pia kernel: [  202.136270] integrated sync not supported
May 30 15:07:36 pia kernel: [  205.316192] integrated sync not supported
May 30 15:07:57 pia kernel: [  226.235963] gvfs-gdu-volume[7681]: segfault at c ip 00544fda sp bf903440 error 4 in libgdu.so.0.0.0[53c000+22000]

Does anyone know what is causing this and how to fix it?

---

### Post by excogitation on 2009-06-01
I also have had that issue on my MSI Wind U100 a few times when trying to change brightness levels ... thought it stopped after some update - need to check if it still happens.

Edit: Yeah, whenever I try to change brightness with the hotkeys this flickering happens and the machine becomes unusable (can't shutdown) - also flickers when switching to the console (e.g. ctrl+alt+f1).

No dmesg output while it's happening though.

---

### Post by jon.reeve on 2009-06-01
I tried submitting this as a bug but I don't know if I listed it under the right packages or with all the information necessary to get the bug taken seriously. : 

[https://bugs.launchpad.net/bugs/381461](https://bugs.launchpad.net/bugs/381461)

---

