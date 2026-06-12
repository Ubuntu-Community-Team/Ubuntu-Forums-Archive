---
title: "[SOLVED] Update Manager may have broken my programs"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by DancemasterGlenn on 2007-09-21
Hi, I hope this is the correct category to post this in, and that the title was accurate. I've been using Ubuntu for about a year with no major problems (none that I couldn't solve myelf/with help from the interwebs), but I've finally run into something pretty frustrating that I can't figure out for the life of me. Here's what happened...

To the best of my knowledge, this began on the 20th, when my update manager ran and found the following package updates:

cupsys (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
cupsys-bsd (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
cupsys-client (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
debconf (1.4.72ubuntu9) to 1.4.72ubuntu10
debconf-i18n (1.4.72ubuntu9) to 1.4.72ubuntu10
hal (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3
hal-device-manager (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3
libcupsimage2 (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
libcupsys2 (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
libcurl3 (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
libcurl3-dev (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
libcurl3-gnutls (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
libcurl3-openssl-dev (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
libhal-storage1 (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3
libhal1 (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3
update-manager (0.42.2ubuntu22) to 0.42.2ubuntu22.1

Naturally I upgraded these parts, and was prompted to restart my computer. I restarted, opened Pidgin (not really related, this keeps happening without Pidgin being on) and went to class. When I got back, Pidgin wasn't running. Something had restarted my computer, and I didn't know what. Turns out my screen had started to go into my screensaver (the matrix one that is provided in Dapper), crashed GNOME (maybe?) and restarted the computer for some reason. Upon trying to get into my screensaver preferences to turn it off so I could leave my computer on, the computer crashed and restarted itself again (really quickly, it wasn't a full restart, which is why I think it just crashes GNOME).

So now I'm worried, and I try some other programs. ZSNES crashes the computer, GENS crashes the computer, Quake3 crashes the computer... trying to open a video crashes the computer, and when I open up tvtime it runs, but tells me there is no signal, and that it "cannot open capture device /dev/video0." There are probably more things that would crash, but I don't know if these crashes are going to hurt my computer somehow. So for now, my whole system is sort of useless to me.

I was hoping maybe it was related to one of the packages I updated, but if it is no fixes have been put out yet. Does anyone have any idea what's going on with my computer? Thank you very much in advance for reading all that... if you need to know any particular specs let me know.


Oh, also it might help to mention that my graphics card and my tv capture card are separate, and that my audio card seems to be working fine...

---

### Post by dcstar on 2007-09-21
> **DancemasterGlenn said:**
> 
..........
To the best of my knowledge, this began on the 20th, when my update manager ran and found the following package updates:

cupsys (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
cupsys-bsd (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
cupsys-client (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
debconf (1.4.72ubuntu9) to 1.4.72ubuntu10
debconf-i18n (1.4.72ubuntu9) to 1.4.72ubuntu10
[B]hal (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3
hal-device-manager (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3[/B]
libcupsimage2 (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
libcupsys2 (1.2.2-0ubuntu0.6.06) to 1.2.2-0ubuntu0.6.06.3
libcurl3 (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
libcurl3-dev (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
libcurl3-gnutls (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
libcurl3-openssl-dev (7.15.1-1ubuntu2.1) to 7.15.1-1ubuntu3
[B]libhal-storage1 (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3
libhal1 (0.5.7-1ubuntu18.2) to 0.5.7-1ubuntu18.3[/B]
update-manager (0.42.2ubuntu22) to 0.42.2ubuntu22.1
..........
I was hoping maybe it was related to one of the packages I updated, but if it is no fixes have been put out yet. Does anyone have any idea what's going on with my computer? Thank you very much in advance for reading all that... if you need to know any particular specs let me know.

Oh, also it might help to mention that my graphics card and my tv capture card are separate, and that my audio card seems to be working fine...

The highlighted packages may be the ones that are no longer compatible with your hardware, you can go into Synaptic and try to do a "Force Version" on all of these back to the previous version and see if that makes any difference.

---

### Post by DancemasterGlenn on 2007-09-22
> **dcstar said:**
> The highlighted packages may be the ones that are no longer compatible with your hardware, you can go into Synaptic and try to do a "Force Version" on all of these back to the previous version and see if that makes any difference.

Thanks for your quick reply, it's very much appreciated. Today I tried forcing the packages (which I didn't know I could do, so thank you):

Downgraded the following packages:
libhal1
hal
libhal-storage1
hal-device-manager

This seems to have completely fixed my tv card (thank you!), but my screensaver, emulators and video playing still seem to be broken... any advice on what I could do?

EDIT: For clarification, web videos work (or at least, youtube works), videos on my computer don't.

EDIT2: I don't know if this is important, but the downgraded packages are older than the versions I had before the update that (seems to have) broken things: My old libhal1 was 18.2, for example, but to force the package I was only able to downgrade from the seemingly broken 18.3 to a straight 18 (what I assume was the base version distributed with Dapper). Should I bother searching for 18.2 .debs?

---

### Post by DancemasterGlenn on 2007-09-23
I hope someone can keep helping me with this... I'm learning some stuff but I don't know how to apply this information. I found an old thread that seems to have a similar sounding problem:

[http://ubuntuforums.org/showthread.php?t=238295](http://ubuntuforums.org/showthread.php?t=238295)

If this is the problem I'm having, then it would seem that OpenGL is crashing X for me. That's great, because it means I actually know (somewhat) what is going on. However, I still don't ecactly know why, and I certainly don't know what to do about it. I hope someone can shed some light on this situation.

---

### Post by DancemasterGlenn on 2007-09-24
Success!

I don't know why this happened, but I ran envy (which I'm using to configure my NVIDIA drivers) and downloaded an update that fixed everything. I'm hesistant now to re-update my hal1 stuff, so I think I'll just leave it as-is. Hal is weird.

Thanks for the help, dcstar!

---

