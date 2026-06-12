---
title: "Aspire One - Lost Compiz."
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-07-07
I just want to check if anyone else using an Aspire One has had problems with Compiz in Karmic since Friday's updates. The last Intel video driver update was today and I still cant get it run right, so I just want to check if the problem is the updates, or more likely I have messed something up.

---

### Post by meeples on 2009-07-07
well yea but on my system im the only one with problems, all the other users still have compiz :S

i noticed todays updates included some sort of nvidia driver, maybe its confused and thinks i have a different graphics card.?

---

### Post by celticbhoy on 2009-07-07
That sound even weirder, I only have a 1 user system. Just out of info, I take you update the system from your user account only?

---

### Post by taavikko on 2009-07-07
> **meeples said:**
> well yea but on my system im the only one with problems, all the other users still have compiz :S

i noticed todays updates included some sort of nvidia driver, maybe its confused and thinks i have a different graphics card.?

Then something is b0rked on your user settings in  ~/.

jockey pulls the modaliases for nvidia and fglrx so that when installing new HW it offers drivers. This obviously is reduntant in notebooks. So no, it's not confused.

---

### Post by celticbhoy on 2009-07-07
Just tried deleting all reference to compiz from my home directory - still no joy. Just keeps saying desktop effects could not be enabled.

---

### Post by taavikko on 2009-07-07
> **celticbhoy said:**
> Just tried deleting all reference to compiz from my home directory - still no joy. Just keeps saying desktop effects could not be enabled.

You may need to erase/rename
.gconf and .gnome2
To see the difference

But before doing so, check that creating "new user" compiz works,
it's pretty futile to delete settings if drivers/software aren't working...

---

### Post by celticbhoy on 2009-07-08
I tried setting up a new user & checking Compiz, and it worked fine so some setting has been messed up.

---

### Post by tjeremiah on 2009-07-09
mines is enabled but the "show desktop" doesnt work, nor the "scale" feature. (that never did work anyway)

---

