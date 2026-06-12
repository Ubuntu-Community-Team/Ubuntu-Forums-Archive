---
title: "Preventing Mediatomb Upgrades (sidegrades)"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by mebunto on 2011-03-31
Hello,
I have taken much time and effort to get Mediatomb working on my new machine running Maverick Server, with GUI.  Those of you who run Mediatomb know that it's pretty convoluted to get everything "just right".
I have located the three Mediatomb packages in Synaptec and marked them as **"lock version"** in the hope that they will not be up(side)graded to a slightly different version of Mediatomb, which does not have Javascript enabled however, update manager still insists on trying to make the change to the other version ... is there anything that I can do?

Thanks

---

### Post by mebunto on 2011-03-31
Fixed it - it was xulrunner that was causing the problem, now that has been castrated!

---

