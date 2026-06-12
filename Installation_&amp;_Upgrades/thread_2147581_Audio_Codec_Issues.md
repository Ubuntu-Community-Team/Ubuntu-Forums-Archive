---
title: "Audio Codec Issues"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by throese on 2013-05-22
Long story short, I missed ONE step for yasm and I get the error in the screen shot. I'm remoted into my PC at home via teamviewer. Any ideas as to what I can do to fix whatever the problem is?

[ATTACH=CONFIG]242885[/ATTACH]

Currently at work in the office with my boss, but he's busy and is the Windows specialist of the group. I'm the UNIX/Linux specialist between the two of us, yet I cannot figure this out. XD

---

### Post by dino99 on 2013-05-22
sorry, cant see what that screenshot show (its too small)
dont your log complaint about something ? (.xsession-errors)  or run it from a terminal to get the warning/error(s)

---

### Post by throese on 2013-05-22
The terminal says the following:

[Reading database...259527 files and directories currently installed.]
Unpacking yasm (from .../x264/yasm_1.3.0-1_amd64.deb) ...
dpkg: error processing /home/kenny/Desktop/yasm-1.2.8/x264/yasm_1.2.0.1_amd64.deb (--install):
 trying to overwrite 'usr/local/include/x264.h' , which is also in package x264 310.133.2+gltajac04b - I
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/kenny/Desktop/yasm-1.2.0/x264/yasm_1.2.0-1_amd64.deb
/var/tmp/tmp.4bKegxbLSw/dpkginstall.log (END)

And I don't know how to check that stuff, yet.

---

