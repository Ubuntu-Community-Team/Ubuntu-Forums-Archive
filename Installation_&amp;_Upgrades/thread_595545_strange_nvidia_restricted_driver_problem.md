---
title: "strange nvidia restricted driver problem"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by lukeminus on 2007-10-28
Okay so I originally upgraded to Gutsy from Fiesty, which was okay, and to get my nvidia card to work I enabled the restricted driver from the restricted drivers manager. It worked fine and I had some sweet 3d effects and all that jazz.

However, I had so much crap on my system I thought that I would reformat and do a fresh install of Gutsy, which I did and it worked fine. BUT, now when I enable the restricted nvidia driver and restart my system, it boots in 'low graphic mode' and looks like puss.

What is the difference here? I can't work it out. Any help will be greatly appreciated.

Luke.

---

### Post by khughitt on 2007-10-28
Hey Luke,

It may be that the wrong driver is being used for whatever reason. Try going to **system**-> **admin** -> **screens and graphics** and make sure the correct driver is selected. Also, does nvidia have it's own error log? Check the /var/log folder and see if you see any logs for nvidia.. If you do, try searching for "error" or "warning" and may be you will find some useful clue.

Goodluck!

---

### Post by lukeminus on 2007-10-28
Thanks Keith, I will have a look at this after work.

---

