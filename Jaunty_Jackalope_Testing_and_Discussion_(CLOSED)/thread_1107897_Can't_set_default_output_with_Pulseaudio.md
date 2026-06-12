---
title: "Can't set default output with Pulseaudio"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2009-03-27
I am not able to set the default sound output with any of the available pulseaudio GUIs (pulseaudio-mixer-applet, pavucontrol, gnome-volume-control-pulse). In any of these applications, I should be able to plug in my USB headset, set the device to default, and them have all subsequent audio streams play on that device (or in gnome-volume-control-pulse, everything should be switched over immediately). Is anyone else having this problem?

---

### Post by markbuntu on 2009-03-27
Well, that is not how it works. The way it works is that your applications will use the same device they used last time they were opened. There is some discussion going on at the pa mailing list about how to deal with this but opinions vary.

Personally, when I plug in my usb headset I don't want Amarok to just switch over to it automatically. I want Amarok in my speakers, always unless I specifically tell it otherwise. Ekiga or Skype could move automatically to my headset but not for call notification, I want that in my speakers. Do you begin to see how not easy this is.

Anyway, the pa devs are working on a system where you can define your applications by usage and assign them sinks/sources priority lists depending on their usage category. So, what you want is coming soon to pulseaudio. KDE/Phonon is also working in this direction.

---

### Post by rockin_goliath on 2009-03-28
but the behavior that I describe worked fine during the Alpha releases with the new gnome-volume-control-pulse. Strange.

---

