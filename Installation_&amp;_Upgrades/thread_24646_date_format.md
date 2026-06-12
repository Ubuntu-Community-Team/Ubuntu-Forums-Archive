---
title: "date format"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by brickbat on 2005-04-07
hi, i have managed to install software i never could have imagined with ubuntu but for the life of me i cannot find where the date format is set. please help me. its driving me crazy.

ciao,
bb

---

### Post by IceAxe18 on 2005-04-08
Move your mouse pointer to your clock and right click, & then you can select Preferences or Adjust Date & Time. Is this what you wanted?

---

### Post by brickbat on 2005-04-08
Hi IceAxe,  No, unless there is something hidden there that I don't know about, it isn't what I want.

Currently the short date format in the system is mm/dd/yy.  This is an american format.  I want it to be dd/mm/yy.  Also, the long format is ddd mmm d.  I want it to be ddd dd mmm.  All I can find in preferences is changing the time to 24/12 hour clock.

ciao,
bb

---

### Post by nocturn on 2005-04-08
The date format is controlled by your locale.

Try 
dpkg-reconfigure locales

and pick one that is appropriate for your region.  Please keep in mind that this might set the language too.

---

### Post by brickbat on 2005-04-08
i tried it and it worked...thanks again nocturn.
ciao bb

---

