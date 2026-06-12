---
title: "Never before had a problem Ubuntu desktop graphical display; Trying to use nvidia GT6"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by focaccio on 2012-10-18
I've been using ubuntu since 9.04 and never had a problem with Ubuntu bringing up the desktop graphical user interface.  However I am currently not able to see anything graphical past the install screens.

I have an Intel DP55KG motherboard and just installed an nvidia gt630 graphics card (zotac), since the old graphics card failed.

I can install the server and see text.  So I do a apt-get install ubuntu-desktop...or apt-get install kubuntu-desktop...or apt-get install xubuntu desktop, but after the reboot there is no display...it is like something is hung up.  I tried using the live quantal dvd and I do see the graphical prompt to try without installing, but after selecting that the screen goes blank.  I've tried two monitors and the same thing happens.  There is a faint "glow" on the screen and I do not get a "no input signal" from the monitor, so something is happening.

I can install an old OEM of XP so I know the video card and motherboard are at least semi functional.

Any help is appreciated.

Thanks,
Greg

---

### Post by focaccio on 2012-10-19
I am able to get to a GUI desktop with Live FreeBSD.   So again, it appears the video card and motherboard are functional.


[B]So what I would like to know now is: How, exactly, can I boot/install ubuntu using generic VGA?
[/B]

 I'm assuming that is why I see the splash install screen for quantal and then it goes blank when I select...try without installing...because the splash screen is generic VGA.

Any help is appreciated.

Thanks,
Greg

---

### Post by focaccio on 2012-10-19
**SOLVED**

[B]This was an issue with the boot process hanging not with anything video related!
[/B]
At first my video card failed, which I replaced.  When I could not boot to desktop, I used recovery mode to see the boot process hang at intel e1000.  So I disabled internal lan in bios.

Still the thing wouldn't boot to desktop.  I used the recovery mode again and found the boot process hanging on rt2800pci !  So I removed my airlink wireless card and...presto!...I can boot to GUI desktop.

Strange to me that some OSs (Live FreeBSD) don't get hung up on hangs while others do.   Also strange to me that Ubuntu server doesn't get hung up, but when overlaying ubuntu-desktop or kubuntu-desktop or xubuntu desktop it does!

[B]Lesson: Always start trouble-shooting the recovery mode issue!  
[/B]
This event was two network hardware failures.  I got distracted thinking it was a video issue because of the different behavior of server boot and server with gui overlay boot.

---

