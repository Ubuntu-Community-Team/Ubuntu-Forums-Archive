---
title: "Loud noise at shutdown/reboot"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2010-03-05
Does anyone else get a loud noise for a second or two when rebooting/shutting down in Lucid?

---

### Post by yelo3 on 2010-03-05
Yes, I get it, but I don't know the package to bug

---

### Post by Technoviking on 2010-03-05
My guess would be linux or pulseaudio.

---

### Post by sports fan Matt on 2010-03-05
Agreed I thought it was just me.

---

### Post by psyke83 on 2010-03-05
Rather than anything related to sound, is it possible that you're listening to the hard disk head abruptly parking as the power to the drive gets cut?

It's happening on my system (and I thought this bug was fixed a *long* time ago).

---

### Post by yelo3 on 2010-03-05
No, it's the sound. you can mute it if you like, using alsamixer.
Anyway using alsamixer should not be needed in a default install

---

### Post by opethfan89 on 2010-03-16
Has a solution to this been found yet? I've tried commenting out the line options snd-hda-intel power_save=10 power_save_controller=N in the file /etc/modprobe.d/alsa-base.conf  but I still have this rather annoying noise.

Using an hp pavillion dv7-3060US laptop, dual booting with win 7 home premium. windows gives no such noise so I know it is linux-specific and not hardware related (this is a brand new laptop, after all)

I eagerly await a response :)

**EDIT** Actually, commenting out that line DID work, and I'm not running lucid, I'm on Karmic atm. So for any HP user looking for a fix, comment out the line in my post, works perfect for me and now my laptop doesn't sound like it is farting when I shut down.

*EDIT* Well, as it turns out, the problem ISN'T gone. It now shows up  even with speakers muted, so I'm really not sure what more to do. Rather  annoying to have my laptop fart during class.

---

### Post by andersgb1 on 2010-04-20
For reasons still unknown to me, the suggestion in [http://ubuntuforums.org/showthread.php?t=1367499](http://ubuntuforums.org/showthread.php?t=1367499) solved the problem for me:
> I seem to have found a workaround... I turned of the splash screen (edited /etc/default/grub and changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet", and ran update-grub, both with sudo), and now after that my laptop didn't beep. So far I tested it only once, but the laptop used to beep every time, and now it didn't.
I don't have a splash screen anymore, but if those beeps go away I'm more than happy with that solution.

---

