---
title: "Not able to add a network printer"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DarkReaper79 on 2009-03-29
when I was using Intrepid, I followed the Lexmark how-to and I was finally able to get it working. Not that Im using Jaunty, the option to add a samba printer, is not listed in the options. I followed the how-to, and have cups, and samba installed. Is anyone else having this problem, or have found a solution?


Solved!

---

### Post by Reiger on 2009-03-29
Am not sure if you already did this, but fiddling with the CUPS control panel might help: [http://localhost:631/](http://localhost:631/)

For a very common denominator: LPD printing (requires LPD & LPR features be enabled in Windows) is easy to set up.

---

### Post by DarkReaper79 on 2009-03-29
> **Reiger said:**
> Am not sure if you already did this, but fiddling with the CUPS control panel might help: [http://localhost:631/](http://localhost:631/)

For a very common denominator: LPD printing (requires LPD & LPR features be enabled in Windows) is easy to set up.

I think I may of messed up on the title, my apologies. The printer is connected to a xp box. Before there was a option on the add printer secton to add printer vis samba, but now its not listed. Sorry about the mess up:(

---

### Post by DarkReaper79 on 2009-03-29
Its all fixed!, I completely remove samba and cups. Ended up losing Nautlius, but reinstalled it all. The option for printing on samba was finally there. Must of been a bad install or something:P

---

