---
title: "Wireless Printing"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jaded Misanthrope on 2008-10-20
Wireless printing to my Canon MP600R worked perfectly on Ubuntu 8.04 using CUPS. However, since I upgraded to 8.10, the option 'LPD / LPR host or printer' (or similar) is no longer present in CUPS (accessed by localhost:631 in Firefox). How could I go about getting this option back or printing wirelessly to my Canon MP600R on Ubuntu 8.10 through a different method?

---

### Post by Jaded Misanthrope on 2008-10-21
Does anybody know?

---

### Post by koki on 2008-10-23
I have a similar configuration, and was able to print choosing Other for the printer connection, and using lpd://192.168.0.200/lp1 as the printer URL. Hope this helps.

---

