---
title: "apt-get segmentation faults"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by slickwilly on 2007-08-06
Have a nasty problem.  Did a slew of upgrades the other day, don't remember off the top of my head what was upgraded.  But just went to use update manager to check for updates and it died, so ok I tried Synaptic, it died also, ok now this is getting scary, fine I'll go to Konsole and do a sudo apt-get dist-upgrade, well nope it gives me a segmentation fault, YIKES.

I truly dont want to have to reinstall, I've still got a Dapper install DVD and bringing it up to Feisty will take bloody aeons, as will downloading a Feisty install dvd which is why I keep putting off doing it :(

Any ideas?

Slick

---

### Post by JudasReanimated on 2007-08-06
First is this Slick Willy from TOaster Oven, and secondly.

Make a Root Account Password

Restart your computer and pick recovery mode. 

After it does it's thing, enter the root pass when it asks for it, and run apt-get update, and dist-upgrade, and that should fix it. If not come back and we will try something else. You could also try -f install as well. THough I believe dist-upgrade would handle it all.

---

