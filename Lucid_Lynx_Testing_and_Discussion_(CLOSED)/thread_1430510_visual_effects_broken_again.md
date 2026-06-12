---
title: "visual effects broken again"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-03-15
After an update a couple of days ago visual effects are no longer enabled on startup and compiz is not started . furthermore visual effects cannot be activated from system>preferences >appearance , no boxes are checked when it comes up ( not even none ) and checking extra does nothing . compiz starts normally from fusion icon but does not retain settings on reboot . on startup windows are missing title bars until compiz is activated . I am using the repo nvidia driver activated by "hardware drivers" .

---

### Post by lidex on 2010-03-15
Have you checked the settings in gconf-editor and have "compizconfig-backend-gconf" installed?

---

### Post by nanog on 2010-03-15
I had this happen earlier in development and after much hair pulling it turned out there was a dependency missing somewhere along the way. I purged and reinstalled compiz/jockey/nvidia (and associated dependencies) and the problem was fixed.

I'm no longer running nvidia because nouveau and gallium3d are working well on my systems.

---

### Post by ronacc on 2010-03-15
compizconfig-backend-gconf is installed and settings in gconfig look ok . all was working until the update of a couple of days sgo , I waited awhile to see if later updates fixed it again . Thanks for the suggestions .if it doesn't clear up by beta I'll bug it .

---

### Post by cariboo on 2010-03-15
I had a graphics card fan die Friday, so I pulled it and used the onboard graphics adapter, I thought the graphics problem was due to the change of cards, but even after a fresh reinstall of the daily build yesterday, the problem persists.

---

### Post by ronacc on 2010-03-15
I update twice daily , AM and PM and also tried yesterdays daily ( zsync'd early this AM ) no change .

---

