---
title: "Can not load installation"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by MGadAllah on 2008-06-29
Hi
I've downloaded the latest release of the desktop 8.04 but as soon as I run installation from the CD I've found that may monitor keep flickering and all i can see is pieg color background with nothing viewable at all (as if you are recieving a non clear streaming).
My video or vga card is ati radeon 9200 128 mb... is it enough to install or something wrong with it.
Thanks

---

### Post by utab on 2008-06-29
> **MGadAllah said:**
> Hi
I've downloaded the latest release of the desktop 8.04 but as soon as I run installation from the CD I've found that may monitor keep flickering and all i can see is pieg color background with nothing viewable at all (as if you are recieving a non clear streaming).
My video or vga card is ati radeon 9200 128 mb... is it enough to install or something wrong with it.
Thanks

Maybe giving the live cd first is a good option to see that your system works fine with the OS.

HTH,

Umut

---

### Post by MGadAllah on 2008-06-29
> **utab said:**
> Maybe giving the live cd first is a good option to see that your system works fine with the OS.

HTH,

Umut

actually the same thing happened with the live CD :(

---

### Post by MGadAllah on 2008-06-29
I've get a picture with my mobile for the screen.
I hope that you can see it clear.

---

### Post by upchucky on 2008-06-29
if that is the screen after the install then the vert and horiz frequencies are set wrong in xorg.conf

need to manually set them at command prompt probably lower than the auto set them at.

search here for vidio screen settings.

---

### Post by MGadAllah on 2008-06-29
I did not start any installation at all. I've got this screen when I was launching the live cd and get it again when I was trying to install. So this screen is the 1st thing I've got before I even touch my mouse or key board at all.

---

### Post by upchucky on 2008-06-29
you may have to see if your bios is locked at some default setting that can be changed, since it is doing that at the live cd and install start then it is a hardware setting that is needing a change.

I have a desktop that has an asus mainboard, i had to change a setting long ago to let  the ubuntu live cd set up the monitor.

you may also want to see if there are settings or jumpers on the ati card to adjust.

google the mainboard and the card.

---

### Post by MGadAllah on 2008-06-30
What exactly shall I look after? I am really do not know what exactly shall I search for? And does the ati card has any jumpers? I am really neobie to all that stuff but I've found that most people around switched to ubuntu.
Thanks

---

### Post by VMC on 2008-06-30
> **MGadAllah said:**
> What exactly shall I look after? I am really do not know what exactly shall I search for? And does the ati card has any jumpers? I am really neobie to all that stuff but I've found that most people around switched to ubuntu.
Thanks

You might have to use the kernel cheat codes to be able to boot using the livecd. Or download the Alternate CD method. The cheat codes I'm referring to were first used by Knoppix. For example vga=normal, or vga=771. Just to be able to get a stable display for it to boot up and then you can install ATI drivers.

Her is one link that maybe of help:
[http://ubuntuforums.org/showthread.php?t=567409](http://ubuntuforums.org/showthread.php?t=567409)

---

### Post by MGadAllah on 2008-07-02
My card is ATI Radeon 9200, is it the reason being an old one?
I've tried the CD on other computer and it worked as fine.
Plz advise 
Thanks

---

