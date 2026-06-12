---
title: "Get NetworkManager started earlier?"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fluteflute on 2010-04-09
My system is now booting up far faster than ever before (with Bootchart reading 28.9 seconds). I get firefox to autostart, but by the time it has loaded, NetworkManager is still trying to connect to my wireless network. It probably takes it 20 seconds after the rest of my system is booted.

Is there any way to get NetworkManager started earlier? (Maybe just some service and not the GUI at first?)

I appreciate "the fastest network connect" is an aim of the Maverick Meerkat so maybe I should just be patient...

---

### Post by mikewhatever on 2010-04-09
Try setting up a static IP. Having done that, I often find the network already connected when the desktop shows up.

---

### Post by randomizer101 on 2010-04-09
Edit the connection you're using and check the "Available to all users" box in the bottom left of the edit window. This will get it connecting before login and it should be up or almost up by the time you reach your desktop (unless you boot too fast :)). It's always bothered me too, but this is how I get around it. I'm the only user of the system though, so allowing all users access doesn't really change anything for me except to make it faster.

---

### Post by fluteflute on 2010-04-10
Thank you, those both seem great suggestions. I have just "applied" randomizer101's method, but I may well investigate the static IP if that isn't fast enough for my tastes...

---

