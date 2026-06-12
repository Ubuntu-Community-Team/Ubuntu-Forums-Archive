---
title: "Two kernel version and uninstalling ALSA killed Linux..."
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Natume on 2007-05-22
Yes, the title really isn't very great, but it explains the problem I had fairly well.  And I say had, because it's pretty much a thing of the past ; I reinstalled Linux promptly and had no real issues doing so after the system crashed.  What my real question is is : how can uninstalling ALSA cause Linux to not boot into GUI?

My situation was roughly that I had the 2.6.17-11-generic kernel on my system, (Edgy) and it wasn't meeting my needs, so I compiled a new 2.6.21.1 kernel with a real-time patch applied to it to run in the stead of the former kernel.  I kept both, of course, just so that I wouldn't end up without a functioning kernel.  After installing the newly compiled kernel, I booted in just fine (and booted it down several times, booting into the old kernel several times as well - all in all, things were still fine there).  

Only issue was that Beryl and XGL didn't work for crap (rather, XGL was ungodly slow, to the point where it was painful to watch the windows refresh as I dragged them around), but booting into Gnome everything except for the sound worked just fine.  I hadn't installed ALSA with the kernel by default, seeing as I wanted a more up to date version, so I got the 1.0.14rc... whatever the rc number was sources from the ALSA site, compiled, and installed, ran modprobe and set everything up.  Sound cards were detected fine, but there wasn't any sound in either kernel after this point... past the login screen (there was definitely sound there, however).  Now I'm pretty sure that was a matter of audio group and the permissions therein.

Since I wanted to get sound working on the old kernel at the very least, I booted into it and uninstalled the version of ALSA that I had using make uninstall in the reverse order that I installed everything (so that I could just reinstall the old packages).  Everything seemed to work fine... except that gnome basically died : I couldn't open any windows by using the icons on the screen, though the ones I was in at the time worked fine, and when I logged out, logging back in just plain failed, every time (in both kernels).

What I want to know is how my actions could have caused failure like this.  Perhaps it was because I uninstalled from a different kernel than I had installed in.  Perhaps it was because something's inherently flawed compiling for one kernel and having it install (for one reason or another, accidentally if nothing else) on both.  But I don't really know anything for sure, and I want to avoid this sort of issue next time I try to get another kernel up and running.

Thanks for taking the time to read that.  Any ideas would be appreciated, as well as ways to perhaps segregate programs so that they install only for one kernel instead of another (then again.. since both kernels share the same root directory... that may be flawed thinking period).

~Natume

---

### Post by eric02138 on 2008-04-14
I'm having the *exact same problem*: I installed ALSA, it killed my sound, so I tried uninstalling.  But now gnome is gone - I get a text-only interface on reboot.  Before I resort to re-installing the system (and losing a bunch of files), does anyone have any suggestions as to how to recover?

Thanks!
Eric

---

