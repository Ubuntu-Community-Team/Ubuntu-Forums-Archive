---
title: "black screen after upgrade to gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by andreimatei on 2007-10-19
Hello folks,

I just updated from feisty to gutsy (kubuntu on dell inpiron laptop with ati video card)... Didn't work that well. After I boot, I just get a black screen. I get the kde progress bar, but after it's done, the screen turns completely black (backlight is on, though). ctrl+alt+f1 doesn't work, and neither does ctrl+alt+backspace (but this is not supposed to work anymore in gutsy, right?). Ctrl+alt+del works, it brings the kde progress bar in revers (for shut down), and the systems restarts.
What can I do? How can I at least boot without X?
Please help.

Thank you,

Andrei

---

### Post by andreimatei on 2007-10-19
Ah, I managed to look in x's log (booting in windows an looking at the linux partition). I crashed with sig 11, apparantly in ati driver's code (fglrx). How can I stop using this driver? 

Thank you

---

### Post by cybermatthieu on 2007-10-21
Hi,
I have the same problem... :( It's seems that every upgrade gives me some trouble. You might want to change the driver directly in /etc/X11/xorg.conf. Look for the section "Device", there's where you say which driver to use. You might want to try to set Driver to vesa or ati.
Here's an example of the section Device:
```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

```

Make sure you only have these 3 lines... I know that fglrx has more and you might have troubles if you keep all the config of flgrx.

Hope it helps,

Matt

---

### Post by andreimatei on 2007-10-21
installing gutsy (as opposed to upgrading) fixes this.

---

### Post by jack_teagarden on 2007-10-21
I'm having a similar problem; although my graphics card is a Nvidia 6200 Apg8x.

It's an odd problem, as the "recovery mode" boot works just fine. But with any of the new Gutsy kernels, not in recovery mode, it completes the loading bar, and then freezes to a black screen. 

I could probably reinstall, but with the hundred or so gigs of stuff I have I'd rather fix this without doing something that time consuming. 

Any ideas?

---

