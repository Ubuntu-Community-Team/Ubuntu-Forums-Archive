---
title: "Anyone else lost audio."
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-02-25
Gone today....

---

### Post by lonniehenry on 2009-02-25
Some have said they got sound back after hal update but not me.  Tried adding myself to audio and no luck. Did get preferences to see the device 9 no longer null) but still no sound

---

### Post by eyelessfade on 2009-02-25
without pulse I get sound as usual

---

### Post by Mr. Picklesworth on 2009-02-25
> **eyelessfade said:**
> without pulse I get sound as usual

Not helpful.

---

### Post by eyelessfade on 2009-02-25
> **Mr. Picklesworth said:**
> Not helpful.

Depends if you want audio or pulse to work.

---

### Post by philinux on 2009-02-25
Updated and got audio back.

Next... :lolflag:

---

### Post by jp_coll2003 on 2009-02-25
totally lost my audio about 10 minutes ago. updated and no sign of getting it back :-(

---

### Post by Rhubarb on 2009-02-25
Updated around 18 hours ago, and lost audio.
Then about 5 hours ago I updated again, and audio is back.

I'm using the default Australian apt server (au.ubuntu.com I think).

Hardware: Asus eee pc S101 running up-to-date Jaunty.

I didn't pay that much attention to what updates I was getting at the time, though I do remember something about linux, and hal.
Sorry I can't be more specific.

---

### Post by rogerdean on 2009-02-25
Happened to me too. Go into Users & Groups, and check there's a group called 'audio'. If not, create one and add yourself to it. Reboot...
Cheers
Roger

---

### Post by lonniehenry on 2009-02-25
Finally got a bunch of updates to pulseaudio  and all is good with the world. Using pulseaudio 0.9.15

---

### Post by MadsRH on 2009-02-26
Perhaps some of you might find this interesting:

[http://drowninginbugs.blogspot.com/2009/02/pulseaudio.html ]("http://drowninginbugs.blogspot.com/2009/02/pulseaudio.html")

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027509.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027509.html")

---

### Post by Kow on 2009-02-26
I would recommend not posting "problem" threads when things go bad just after an update... chances are the build system just needs to catch up and get the rest of the updated packages out. This is usually the case with larger libs like gnome, gtk, audio, xserver updates, etc. I'd say after 1-2 days of the problem hanging around then there might be an issue besides the build system falling behind (unless it's openoffice... I've had to wait a week for those packages to entirely update.)

---

