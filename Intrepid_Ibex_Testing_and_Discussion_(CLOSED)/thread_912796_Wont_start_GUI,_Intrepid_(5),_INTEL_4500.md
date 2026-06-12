---
title: "Wont start GUI, Intrepid (5), INTEL 4500"
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Ub1476 on 2008-09-07
Hi, I received my Thinkpad X200 yesterday and I'm trying to install Intrepid Ibex on it right now. Since I haven't got a external cd reader yet, I boot from an USB (used unetbootin I think). So on first boot Ubuntu get a black a screen after the splash bar has loaded completely. I went away for a few seconds and suddenly it boots Vista (means it rebooted obviously). I tried a second time and removed "quiet", and this time it stops at "loading hardware drivers". The third time however, same results as first, "loading gdm/gui" (last "load"), then black screen and it reboots. 

My comp uses the very new Intel platform with a X4500 integrated. I chose Intrepid cause kernel .27 is supposed to support it. I also noticed that it loaded the VESA driver instead of Intel.. Any tips on how to get this working? Thanks.

---

### Post by klein on 2008-09-07
I'm in the same boat.  On my X200, using the intel driver crashes the computer when X starts.  I've been using the vesa driver with no problems, except of course no hardware acceleration.

My xorg.conf looks like this:
```

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "vesa"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
EndSection

```

---

### Post by Ub1476 on 2008-09-08
Glad to hear I'm not alone.

Hows battery life on Ubuntu compared to Vista on the X200 (I get roughly 7hours, "energy star" settings, on a 9-cell battery in Vista. I hope it will be 2-3 hours better in Ubuntu. :)

Might want to check my [bug report]("https://bugs.launchpad.net/ubuntu/+bug/267375"), if you have something to add.

Ops, mine is a duplicate...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/265119](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/265119)

---

### Post by klein on 2008-09-08
Likewise!

I also get about 7 hours of battery life.  Actually, makes total sense... powertop is showing that I'm drawing 12 watts, and the 9-cell battery is 84 watt hours.

There are still a few power drains that it looks like I could eliminate... I bet we could see 8 hours.

(Woops, forgot to mention that that was with normal brightness.  With the screen down low, I get about 8 hours already.)

---

### Post by simon.sigre on 2008-09-09
Im experiencing the same screen blacking; if i reboot and wait and reboot and wait a few times she comes online; Also after doing the latest round of updates its started hanging on boot again. 
My room mate had an X61 and Ubuntu ran like a dream; this whole 200 saga is making me think fedora... which is a 4 letter word around here!

---

### Post by klein on 2008-09-09
Does Fedora work with intel on your X200?  That might be helpful for fixing Ubuntu...

> **simon.sigre said:**
> this whole 200 saga is making me think fedora... which is a 4 letter word around here!

---

### Post by Ub1476 on 2008-09-09
Have you dried video playback yet, klein? I actually managed to boot just fine with Hardy Heron, with Compiz working live and all. However, video playback completely freeze the (live) system.

Also does all your special keys work (sound, light, pause/play etc).

I'm hoping to get the X200 working perfectly with Intrepid. :)

---

### Post by klein on 2008-09-09
Keep in mind for everything video-related I'm using the vesa X driver on Intrepid.  intel crashes me.

Video playback works fine.  The colors look a bit off sometimes, and it can be blocky.  A 720p video was too slow in Totem but smooth in VLC.

The special keys seem to work... pause/play, volume, screen brightness, the keyboard light, lock, sleep, bluetooth on/off, page left/right all work out of the box.  One little oddity is that though mute works, GNOME doesn't seem to know about it, almost as if the BIOS was muting rather than passing the key through.

I'll note that X is autodetecting my keyboard (evdev?).  If I configure it manually, I seem to lose most of the magic buttons.  So you may need to remove everything about keyboards from your xorg.conf (if there is anything) after upgrading.

Right now I have no option to sleep via the menus or in gnome-power-manager.  I do have a choice to hibernate, but that fails.  Once I tried to #echo S3 > /proc/acpi/sleep, and it slept, but the screen didn't restore properly and I had to reboot.

---

### Post by simon.sigre on 2008-09-10
> **klein said:**
> Does Fedora work with intel on your X200?  That might be helpful for fixing Ubuntu...

No idea if Fedora will work but at the moment i have a very expensive door stop running 8.10; and yes i know alpha alpha alpha.. its more stable than 8.04 on the X200! I had it running fine last night; but after todays round of updates im back to a black screen hang when it boots and no TTY sessions will come up either; it does get past the sshd stage though so im hoping to ssh in and try and work out wtf is happening!

---

### Post by vietseo on 2008-09-10
My xorg.conf
```

Section "Device"
    Identifier  "Configured [Video]("http://www.vietseo.net") Device"
    Driver      "vesa"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
EndSection

```

---

### Post by Ub1476 on 2008-09-11
Anyone bringing this bug upstream on bugs.freedesktop.org?

---

### Post by Ub1476 on 2008-09-13
It looks like the bug has been fixed.. Has this been committed to Intrepid yet?

---

### Post by cprofitt on 2008-10-21
Any update on this thread? I am thinking about buying a new laptop with this video adapter and I am curious to know if the issue was resolved.

---

