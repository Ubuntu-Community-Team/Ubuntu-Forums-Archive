---
title: "Lucid Won't Auto-mount USB Drives or Discs"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by chris1379 on 2010-04-24
Using Lucid Beta 2. When a USB flash drive or hard drive is connected, it will not auto-mount. It shows up in Nautilus and I can just click on it and it mounts and opens. CD's and DVD's do the same thing but video DVD's won't play. I just see the files when the disc is mounted. The strange part is this only happens if I have my computer set to auto-login. If I log out and back in or log in as a guest, everything works as it should. I'm about to try Lucid RC1 so let's see what happens.

---

### Post by chris1379 on 2010-04-24
I just finished installing RC1 and have the same results with one strange twist. I didn't enable auto-login this time. So even if I manually log in when Lucid starts, USB devices won't mount automatically. However, if I log out and back in, they will auto-mount. Am I the only one with this problem? Do I have to login twice every time I want to use the computer?

---

### Post by wilee-nilee on 2010-04-24
Are you sure, maybe you have the show mounted disc on desktop off. As far as the DVD you need libdvdcss2 in synaptic, and really the medibuntu dvd codecs doesn't hurt, and the restricted extras for your distro. Also totem does not always play some media, so install vlc or smplayer.

---

### Post by chris1379 on 2010-04-24
Everything is fine after I log out and back in. DVD's play, USB drives show on the desktop. everything is fine. I use VLC for all my multimedia but the USB issue was there before VLC was installed. Everything worked perfectly in Karmic.

---

### Post by chris1379 on 2010-04-27
I  think I just found the problem. Checking the log files I found:

kern.log
Apr 26 22:01:33 chris-vaio580 kernel: [  178.360607] end_request: I/O error, dev fd0, sector 0
Apr 26 22:01:33 chris-vaio580 kernel: [  178.360630] Buffer I/O error on device fd0, logical block 0
Apr 26 22:01:46 chris-vaio580 kernel: [  191.364631] end_request: I/O error, dev fd0, sector 0
Apr 26 22:01:46 chris-vaio580 kernel: [  191.364655] Buffer I/O error on device fd0, logical block 0
Apr 26 22:01:59 chris-vaio580 kernel: [  204.384347] end_request: I/O error, dev fd0, sector 0
Apr 26 22:01:59 chris-vaio580 kernel: [  204.384370] Buffer I/O error on device fd0, logical block 0

This laptop has a removable floppy drive that is not inserted most of the time. The bay is usually used for a second battery. I booted with the floppy drive inserted and everything works fine. USB drives mount automatically, DVD's play, birds are singing in the trees, and life is happy again. So, is there a way I can get Ubuntu to check the floppy drive once, determine whether it exists or not, and then go on accordingly? The floppy drive is only swapped with the power off.

Chris

---

