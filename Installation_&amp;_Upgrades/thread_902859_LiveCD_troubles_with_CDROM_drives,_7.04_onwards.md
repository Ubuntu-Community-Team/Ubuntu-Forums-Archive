---
title: "LiveCD troubles with CDROM drives, 7.04 onwards"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by Chaotic Stupid on 2008-08-27
So, hello folks. I'm currently running 6.10 on my computer, dual booted with XP. I've since had troubles installing, and even booting, from the 7.04, 7.10 and 8.04 LiveCDs and until recently, I've had no clue whatsoever as to why. I would download the iso, md5sum check it and everything, burn it and pop it in. However, on the boot screen, after selecting either the "try out" or "check the integrity" option, the kernel would load and then my DVD drive would just read, then stop, then read, and so on. Eventually Busybox would show up and spit out some error messages that weren't very helpful. Also, my floppy drive would click a lot.

I've since then learned the fine art of troubleshooting, and with the help of some of the usual boot options (striking out "quiet" and adding "nosplash"), I gathered that the kernel didn't seem to like neither my floppy drive (claiming constant I/O-errors) nor my CDROM drive (claiming "model number mismatch"). I then disabled my floppy drive through BIOS, but still have these two problems:

[LIST]
[*]My DVD drive (a Light-On DVDRW SHW-16H5S)  doesn't read the LiveCDs properly after booting them, despite same discs working fine on other computers
[*]Busybox claims "model number mismatch" on my CDROM drive (A HP cd16f if I believe (it doesn't really work on 6.10 either. I noticed just now that the Device Manager doesn't even recognize it. Works fine in XP though)
[/LIST]

So, is there some other magical boot option that I could test and see? Thanks for reading through :)

---

### Post by Partyboi2 on 2008-08-27
Have you tried replacing the cdrom drive to see if that helps? Another thing you could look at maybe is to install using [[COLOR=Blue]netbootin [/COLOR]]("http://lubi.sourceforge.net/unetbootin.html")or from [[COLOR=Blue]usb[/COLOR]]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html").

---

### Post by Chaotic Stupid on 2008-08-27
No, I haven't tried that yet, though it's naturally an option. It's a decent drive, and I wouldn't want to change it if I didn't need to. I'm just confused as to why it works fine and dandy in 6.10 but acts like a cranky old man cussing at the youngsters in 7.04. I guess that's computers for ya :P

Hmm, I guess I can try USB-booting. Must check in the BIOS first whether it's an accepted boot medium for my old comp, though. Thanks for the answer by the way.

EDIT: Ooohh, I didn't know netbootin existed before. Kudos on that, looks interesting

---

