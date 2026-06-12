---
title: "soundblaster"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by d-valand on 2011-02-12
hi :)

     I enjoy using ubuntu, and everything to do with it. but however after my on board sound failed, i had to purchase a sound card. i bought the soundblaster x-fi xtreme audio. It didn't work on ubuntu, so i had to go back on windows. anyway has anyone got any idea on how to make it work?. i couldn't find any drivers. thanks in advance

---

### Post by cogier on 2011-02-12
Try this: -

Go to **System>Preferences>Sound** click on the **Hardware** tab and make sure the correct sound card is selected.

While your there check the other settings and that nothing is muted.

---

### Post by d-valand on 2011-04-10
> **cogier said:**
> Try this: -

Go to **System>Preferences>Sound** click on the **Hardware** tab and make sure the correct sound card is selected.

While your there check the other settings and that nothing is muted.

I did that it says i got the correct drivers and that, but i get no sound coming out at all?, the card works fine under windows.

any other suggestions?

---

### Post by MrSpike16 on 2011-04-10
Install GNOME ALSA Mixer.  The front speaker volume is probably very low or muted.
This gives you a GUI and menu entry in Sound & Video

Sound Preferences only gives you the Master volume control.

Another alternative is to install ALSA Utilities.  It runs in Terminal (type in alsamixer)

---

