---
title: "Sound does not work in Karmic 9.10?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yuxinzhu93 on 2009-10-25
Any ideas? it worked before in 9.04, I have the RC

---

### Post by cariboo on 2009-10-25
More information would be helpful. What sound card/chipset are you using?

Right click on the speaker icon in the top panel and select Sound preferences. Make sure your hardware is detected.

I've been using Karmic since the toolchain uplaod and sound has always worked, I even swapped the motherboard, cpu, ram and video card, and sound still works. :)

---

### Post by rockstarrem on 2009-10-25
You can fiddle around with the settings in System > Preferences > Sound. Click test next to each driver you select to find the right one.

---

### Post by norm7446 on 2009-10-26
My RC1 installed with the sound Muted.

---

### Post by humphreybc on 2009-10-27
I think Karmic has switched the default from alsa to pulseaudio, so perhaps pulse is having some trouble picking up your hardware.

---

### Post by gstrock on 2009-10-29
ECS NFORCEE4M-A mamma board ;)

> lspci
Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
-----------------------------------------------
No Sound for me in Flash or movie player.
Rhythm box does have sound.  Go figure.

when I open the Sound Preferences dialog box
and click on the hardware tab, no devices are
listed.  There is no Profile pull down list
either.  That is completely missing.  There is
no box labeled "Profile", just this line instead:
"Settings for the selected device:".  

I know what this should look like because I installed 9.10 at work.

---

