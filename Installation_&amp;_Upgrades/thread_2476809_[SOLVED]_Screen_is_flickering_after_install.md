---
title: "[SOLVED] Screen is flickering after install"
date: 2022-07-08
forum: Installation &amp; Upgrades
---

### Post by egshen on 2022-07-08
Hi all
I'm sort of new to Ubuntu even though I've installed it before (successfully) on several computers.
I've tried to install it on my new Lenovo laptop but the screen is not working (it's "blinking").
I got the following error messages (see attachments).
One after installing it and the other one when I booted the computer.
And when I tried the trial version from the same bootable USB key, it was working fine.
Any ideas what went wrong? Or what I've done wrong?

---

### Post by tea for one on 2022-07-08
Assuming that the installation was successful but now doesn't boot, can you jump into the UEFI firmware and see if you have:-

Secure boot
Fast boot
Platform trust technology
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Intel Optane

I have a Lenovo Ideapad where the live session and installation were fine.
Xubuntu did not boot until I disabled Platform Trust Technology.

Many obstacles these days to consider.  ;)

---

### Post by egshen on 2022-07-08
Thanks, I'll try that.
Sorry if I wasn't clear but it does boot after displaying error message but the screen blinks so there's no much that can be done.

---

### Post by tea for one on 2022-07-08
Possibly new hardware/graphics?

Boot into a live session, download this utility and provide the pastebin link with details of your PC.
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

### Post by egshen on 2022-07-08
> **tea for one said:**
> Possibly new hardware/graphics?

Boot into a live session, download this utility and provide the pastebin link with details of your PC.
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

There it is: [https://termbin.com/y15e](https://termbin.com/y15e)

[Update] The live version has the same issue now

---

### Post by tea for one on 2022-07-08
Thank you for supplying the system-info report.
There was nothing particularly unusual about the hardware, however, I popped your exact model in the well-known search engine with Ubuntu as the exact word:-
[https://forums.linuxmint.com/viewtopic.php?t=375600](https://forums.linuxmint.com/viewtopic.php?t=375600)
[https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro](https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro)
Both these answers mention [COLOR="#0000FF"]i915[/COLOR] together with [COLOR="#0000FF"]enable_psr=0[/COLOR]

I know that i915 is the Intel Graphics Driver but I am not familiar with psr=0.
Anyway, it may provide enough of a clue to allow you to research further.

Also, I think that it is advisable to disable Secure Boot because it may prevent the installation of necessary drivers.

---

### Post by egshen on 2022-07-09
> **tea for one said:**
> Thank you for supplying the system-info report.
There was nothing particularly unusual about the hardware, however, I popped your exact model in the well-known search engine with Ubuntu as the exact word:-
[https://forums.linuxmint.com/viewtopic.php?t=375600](https://forums.linuxmint.com/viewtopic.php?t=375600)
[https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro](https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro)
Both these answers mention [COLOR=#0000FF]i915[/COLOR] together with [COLOR=#0000FF]enable_psr=0[/COLOR]

I know that i915 is the Intel Graphics Driver but I am not familiar with psr=0.
Anyway, it may provide enough of a clue to allow you to research further.

Also, I think that it is advisable to disable Secure Boot because it may prevent the installation of necessary drivers.

Many thanks, I'll look into that

---

### Post by egshen on 2022-07-09
> **tea for one said:**
> Thank you for supplying the system-info report.
There was nothing particularly unusual about the hardware, however, I popped your exact model in the well-known search engine with Ubuntu as the exact word:-
[https://forums.linuxmint.com/viewtopic.php?t=375600](https://forums.linuxmint.com/viewtopic.php?t=375600)
[https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro](https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro)
Both these answers mention [COLOR=#0000FF]i915[/COLOR] together with [COLOR=#0000FF]enable_psr=0[/COLOR]

I know that i915 is the Intel Graphics Driver but I am not familiar with psr=0.
Anyway, it may provide enough of a clue to allow you to research further.

Also, I think that it is advisable to disable Secure Boot because it may prevent the installation of necessary drivers.

I've followed the instructions mentioned here: [https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro](https://askubuntu.com/questions/1376946/screen-flickering-on-mouse-move-ubuntu-20-21-lenovo-ideapad-5i-pro)
And it's worked! Many thanks!!

One question though. I'm still getting the same error message when I boot the computer. Is that a problem?

---

