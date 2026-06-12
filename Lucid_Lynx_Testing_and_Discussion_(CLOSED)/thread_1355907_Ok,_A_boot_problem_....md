---
title: "Ok, A boot problem ..."
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2009-12-15
After applying updates today, I cant boot in. This is a regular intel gma, hp laptop. 

On Regular boot, screen just blanks after ubuntu loader.

Recovery mode, shows following output and it just hangs in there. Attaching the hanged screen. There's a cursor blinking just below the last message.

---

### Post by zeroandone on 2009-12-15
Did you do a Partial Upgrade when the installer prompts you?

---

### Post by vikrant82 on 2009-12-15
Nope, I had done an update-manager -d. I lived happily ever after for 3 days and then it got screwed today. No partial updates done. However during last login session I did downgrade a package, 'libopenal1' to karmic version as it was messing my mplayer. I guess chrooting and looking at logs is one option ?

---

### Post by dino99 on 2009-12-15
you are not alone  :P

mine is hanging with a black screen & i can't do anything.
no cursor, no console, even in recovery mode.

---

### Post by vikrant82 on 2009-12-15
So it starts. Bring it on, Hurt me plenty :D

Then its a heads up. Guys don't reboot :P

---

### Post by zeroandone on 2009-12-15
Don't remove or change any packages unless you are 100% sure what you are doing. AND do NOT do any partial upgrade. I did two stupid Partial Upgrades, and messed up the whole system twice.

---

### Post by panaut0lordv on 2009-12-15
I was actually installing today upgrades... Then I yelled OH DUCK! xD I already have 800x600, but to miss GUI at all is too big effort for me xD

---

### Post by koso on 2009-12-15
Try "nomodeset" in kernel boot line. For me it worked.

---

### Post by vikrant82 on 2009-12-15
Great! nomodeset works. :)

---

### Post by vikrant82 on 2009-12-15
Its fixed with some updates.

---

