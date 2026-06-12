---
title: "Video problem while booting Edgy install CD"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by hofer on 2006-10-29
Hello Ubuntu folks,

I have a Dell machine running Windows XP, and I'm hoping to install Ubuntu on it.  I burned an Ubuntu Edgy CD and tried to boot from it today.  It seemed to load the kernel and mount filesystems, but then at some point the screen went blank except for a message saying there was something wrong with displaying in d-sub mode.

This problem seems similar to the one described here, especially because I have a widescreen Dell monitor:  [http://ubuntuforums.org/archive/index.php/t-217481.html](http://ubuntuforums.org/archive/index.php/t-217481.html)

If my sales receipt is to be trusted, my video card is an Intel GMA 950.

Is anyone aware of a workaround?  I'm sad that this magical boot image didn't work.

Oh and FWIW, I also tried this with a Kubuntu Dapper CD--same result.

Thanks,
David Hofer

---

### Post by .t. on 2006-10-29
Do you mean D-Bus?

Is your CD perfect? Run a check at the boot menu. Download and burn again. If that doesn't work, try the alternate CD.

---

### Post by hofer on 2006-10-30
No, I meant D-SUB.  The specific message is:

1: D-SUB
   Can not display this mode

This is message from my monitor, not the kernel.  So my guess is that it's a video or X11 issue, as in the link I referenced.

I ran the CD check you mentioned from the boot menu--it's fine.  Same with the Kubuntu CD--it's fine, but I have the same problem.

Thanks,
David

---

### Post by .t. on 2006-10-30
OK.

Have you tried running in low graphics mode (don't know if that's the specific term, but I'm sure I recall something like that), then setting the resolution?

---

### Post by hofer on 2006-10-30
I tried booting in safe graphics mode (2nd option from top of the boot menu), but I still get the same problem.  I suppose the next thing to try is to boot in standalone user mode?

---

### Post by .t. on 2006-10-31
I'm not sure what you mean by that... As I said, I've forgotten what the Desktop CD is like. Have you tried the alternative CD?

---

### Post by Pengwin on 2006-11-04
I can confirm the same problem with my system (Dell 2405 monitor). It's not a CD media problem. The monitor doesn't like something about the default xorg.conf. Don't know how to fix it though.

---

### Post by hofer on 2006-11-04
Yes, I get the same problem with the Kubuntu Dapper (6.06) CD.  By "standalone user mode" I meant that there are command-line options you can boot the kernel with that let you bypass X windows or whatever graphical system Ubuntu uses, and give you a shell prompt.  Not sure if that would help here anyway, though.

Thanks for confirming this problem, Pengwin.

So what's the next step?  It seems like this is a bug that should be dealt with.

David

---

### Post by .t. on 2006-11-05
Weird, as there is no default xorg.conf (it's generated automagically). File a [bug]("http://bugs.ubuntu.com") and use the alternate CD; hopefully it'll get fixed for Feisty.

---

### Post by hofer on 2006-11-18
I was able to boot in recovery mode from the alternate CD.  After a lot of trial and error, I was able to change my xorg.conf file to fix this problem.  The important lines seem to be:
```

Section "Monitor"
        Identifier      "DELL 2405FPW"
        HorizSync       30.0-81.0
        VertRefresh     56.0-76.0
        Modeline        "1920x1200_60.00" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -VSync
        Option          "DPMS" "CalcAlgorithm"
        UseModes        "Modes[0]"
EndSection

Section "Modes"
        Identifier      "Modes[0]"
        Modeline        "1920x1200" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +Hsync -Vsync
        Modeline        "1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 +Hsync -Vsync
EndSection

```

Unfortunately I have no idea why this works.  It is close to the configuration reported by someone with a similar hardware setup in another thread.  IIRC they still had the problem that they were getting a 1600x1200 display, so I'm kind of surprised that it works for me.  My vague understanding is that the Dell 2405 has a 1920x1200 resolution, and displays at 60.00 Hertz, and these settings specify this, and the config provided by Ubuntu does not.

This is with what is autodetected as an Intel i810 card and an Intel 945G graphics controller.  Hope that helps others with a similar setup.  I'll do a little more experimenting and report the bug tomorrow.

Apart from this (significant) issue, I've been pretty impressed with Ubuntu.  I'm still trying to configure a wireless USB device, but other than that everything works.  Very nice.

David

---

