---
title: "Intrepid freeze problem"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by rstoya05-lx on 2008-11-02
I upgraded from 8.04 to 8.10 yesterday on my Lenovo T60. I am running KDE and have been enjoying the upgrade to 4.1. However I have experienced freezing 3 times now and have had to reboot because the keyboard was completely unresponsive. 

One time I was experimenting with widgets on the desktop, another time I was typing text in Firefox and I can't recall the what 3rd one was.

This is quite disconcerting since each time it happens I have boot off of a GParted CD, check the disks to correct any issues, and then boot again from the main harddrive.

Any suggestions on where to look to find out what is causing this? Has a similar issue been reported (tracked) already? I looked around the forums briefly but didn't find anything yet.

Thanks

---

### Post by rstoya05-lx on 2008-11-03
I had two more freezes when I plugged in an external VGA connector for an overhead projector. I checked /var/log/syslog and saw messages like these:

```
[drm:radeon_cp_idle] *ERROR* radeon_cp_idle called without lock held, held  0 owner f771fac0 f771fa00

[drm:radeon_cp_reset] *ERROR* radeon_cp_reset called without lock held, held  0 owner f771fac0 f771fa00
```

There were also many, many lines containing this kernel message:

```
hheldhheheld  0 hehheld  0 ohheheld  0 hehheld  0 ohheheld  0 ohheheld  0 hehheld  0 ohheheld  0 hehhe ld  0 hehheld  0 hehheld  0 ohhelheld  0 owhheheld  0
```

The amount of output related to the above message was so great that within a matter of a few seconds that syslog filled up 134,412 lines (as opposed to the previous syslog.0, which was only 6,641 lines). 

I was able to connect without problems to the external projector with GNOME. Also I am using an ATI card with the open-source Radeon driver. This looks like an issue related Radeon and KDE (at least the last freeze was). Where is the best place to log this issue?

---

### Post by rstoya05-lx on 2008-11-14
Is no one else using Intrepid with KDE experiencing this problem? The freezes are too frequent and disruptive for me. I've switched over to GNOME and I'm starting to believe Ubuntu is not widely used with KDE.

---

### Post by PeonDevelopments on 2009-05-11
I'm using Intrepid and KDE 4.2; Everytime I have an external hard drive hooked up, the computer will freeze generally every 1-3 hours. This is especially common when listening to music that is located on the hard drive.

Using usb flash drives does not seem to affect the computer that I can tell.

EDIT: My laptop uses a Radeon HD 3870 video card and frglx drivers.

---

### Post by Doug77 on 2009-05-11
I think I'm having a similar problem (even though we're using different distributions).  I'm using Mandriva 2009.1 (with KDE 4.2.2) on a Dell Inspiron laptop.  I find that it freezes when I configure desktop widgets and run Firefox at the same time.  You mentioned one time you were using Firefox, and another time experimenting with widgets.  It sounds like the same thing - one time when it crashed, I wasn't even configuring widgets, but Firefox was running and the widgets were unlocked.  

The freeze is pretty brutal - I can move the mouse, but nothing else responds, and I have to hold the power button for 5 seconds to turn off and reboot.  Although the magic keys do seem to work.  

I don't know what to do about it, except avoid configuring widgets and using Firefox.  I use Opera anyway (my favorite browser).  

Anyone else have any suggestions on what I can do about this, how to report it?

Edit: After more research, it appears to be a problem with the Intel video drivers.  And it freezes still randomly... not necessarily firefox/widgets combo.

---

### Post by PeonDevelopments on 2009-05-20
Back again. After some more freezes, I have some more suspicions.

1. It seems to freeze more often when I have Firefox open, possibly a flash issue?
2. I can unmount my drives and it still tends to freeze soon after
3. I use Catalyst 8.12 64-bit drivers because everything else seems to kill my display
4. Could be a plasma issue, as I don't find it all too stable.
5. My computer never freezes while playing WoW on 1920x1200 mode w/ high graphic settings, so I doubt it's overheating. (Have temp monitor as well)

Either the graphic drivers are randomly erroring, or its a firefox issue is the conclusion I've come to. (My Catalyst drivers also handle the audio I believe, as the Intel HD Audio is using the ATI drivers.)

---

### Post by PeonDevelopments on 2009-06-18
I think I found the problem. Or, at least, a fix based on a particular setting.

I run a 2.26 Ghz Dual 2 Core and ATI 3870.
My problem with the computer freezing up is generally when my 4 port usb or portable hdd is plugged in, although it freezes otherwise too.

It doesn't freeze when playing wow.

AS IT TURNS OUT, it kept freezing when my Power Manager was set to Dynamic Mode. Why? I don't know. Perhaps my usb drives sucked out too much power and caused the crashes. Maybe it stopped the fans from running to meet the cooling requirements (except when playing wow), also instigated by running firefox and flash videos because of the cpu intensive processes and possible memory leaks, even moreso by running amarok attached to a MySql database with my large collection of audio files.

Anyway, I switched to Performance and I have not had a freeze since.
When battery is unplugged I get it to go to powersave, but I have not tested that. And I don't usually have a portable usb hdd plugged in on-the-go.

I hope this helps.

Since switching to a Performance

---

