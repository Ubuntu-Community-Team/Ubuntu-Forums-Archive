---
title: "Can't Get Auto Upgrades"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by saxonjf on 2006-12-07
Please forgive if this has already been covered, but I did a search and could find the info I needed, and this is my first attempt at making a post here.

Anyway, I cannot get Edgy to automatically inform me of new updates.  I can certainly go to the update manager and check for them, but when I had 6.06, whenever there was an update, a symbol would pop up on the top panel.  I cannot figure out how to get that to work now.

As a noob with all things Linux I really want to make sure everything is running smoothly.  And when I check the update maanger and have to run it twice to get all the updates I want to ](*,)  .  Well you get the point.

Well, I love Ubuntu, and am telling everyone to get it and to forget the mindless chatter of Vista...

---

### Post by 23meg on 2006-12-07
Are you sure you have a notification area on the panel? That's where the update manager icon appears; if you don't have one, it won't.

---

### Post by saxonjf on 2006-12-07
I think I figured it out.  Thanks 23... I also got the weather forcaster on my panel, too.  Appreciate it.

---

### Post by helvete on 2006-12-09
> **saxonjf said:**
> Please forgive if this has already been covered, but I did a search and could find the info I needed, and this is my first attempt at making a post here.

Anyway, I cannot get Edgy to automatically inform me of new updates.  I can certainly go to the update manager and check for them, but when I had 6.06, whenever there was an update, a symbol would pop up on the top panel.  I cannot figure out how to get that to work now.

As a noob with all things Linux I really want to make sure everything is running smoothly.  And when I check the update maanger and have to run it twice to get all the updates I want to ](*,)  .  Well you get the point.

Well, I love Ubuntu, and am telling everyone to get it and to forget the mindless chatter of Vista...

i have the exact same problem as you and i have the notification area too, does anyone why whats causing this or have a workaround or solution?

---

### Post by Azakus on 2006-12-10
It appears that the update manager doesn't automatically check for new updates. I always just run ```
sudo aptitude update && sudo aptitude upgrade
```

---

