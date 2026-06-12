---
title: "volume notification not working."
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-03-02
i have a problem with the new notification app. 

after todays update i am missing the new volume notification it has reverted back to the old style.

is there any way to get it back. 

the other notification work ie next track in rhythmbox.

i have tried kilall notify-osd -15 but still the same.

---

### Post by medeshago on 2009-03-02
Do this:

```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status/

killall -15 notify-osd
```

---

### Post by Technoviking on 2009-03-02
> **medeshago said:**
> Do this:

```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status/

killall -15 notify-osd
```

No change here after doing that.

T-V

---

### Post by terry_gardener on 2009-03-02
this didn't work 

i am still getting the old volume control icon when pressing the volume up and down on the keyboard. 

here is the volume notification i am getting.

---

### Post by JohnJackson on 2009-03-02
Does this mean they've switched back to the old style? It appears to be an improved version of the old one anyway.

---

### Post by scaine on 2009-03-02
Yeah, I'm getting that old notification too - maybe related to the fact that volume notification using the new system had an issue over the weekend where the notification box was totally black.

And I agree - it's the old style, sure, but it seems to be better at tracking the volume changes I make.  The old one jumped around a lot if I remember correctly.

---

### Post by smbm on 2009-03-02
Brightness has reverted for me too.

---

### Post by Vaun on 2009-03-02
[https://bugs.launchpad.net/notify-osd/+bug/336810]("https://bugs.launchpad.net/notify-osd/+bug/336810")

---

### Post by terry_gardener on 2009-03-03
got the sound notifications back and it has changed.

---

### Post by go7Ul1ai on 2009-03-03
Yes, same with brightness. I'm glad they came back ^_^

---

### Post by pappfer on 2009-03-03
Yep, I'm glad that they came back, too!
But I preferred the one it was before: it wasn't just showing a single horizontal line but it showed an increasing vertical bar.
And also so far when i changed volume and brightness at the same time then it showed both indicators, one below the other. Now it only shows only one indicator.
I hope they'll change it back! But both versions are cooler then the ones on previous versions of Ubuntu! ;)

---

### Post by pappfer on 2009-03-18
> **pappfer said:**
> And also so far when i changed volume and brightness at the same time then it showed both indicators, one below the other. Now it only shows only one indicator.
It's been fixed now. ;)

---

### Post by scaine on 2009-03-18
Volume is back and looking good.  No notification at all when using brightness keys here (the brightness does change though).

---

