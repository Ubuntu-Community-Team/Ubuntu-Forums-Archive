---
title: "What happened to CUPS LPD / LPR Host option?"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jaded Misanthrope on 2008-10-12
I recently upgraded to Ubuntu Intrepid Ibex, and I need to set up a wireless printer (Canon MP600R). I have done this before on 8.04 without much of a problem.

However, when I came to configure CUPS (accessing it through Firefox: localhost:631), I found that there was no longer an option to create an LPD / LPR Host or Printer, which is necessary for me to set up my printer.

Is there a way to create an LPD / LPR Host or Printer in the version of CUPS used in 8.10, or failing that a way to revert the version of CUPS used by 8.10 to that used by 8.04?

---

### Post by ja4 on 2008-10-27
anyone?
Bueller?
Bueller?

---

### Post by yelo3 on 2008-10-28
You have to manually enter the address ldp://....

---

### Post by Jaded Misanthrope on 2008-10-28
> **yelo3 said:**
> You have to manually enter the address ldp://....

I assumed that the option had an impact on how CUPS treated the printer, with the prefix just being a convenience for the user, but I got the printer working. Thanks anyway.

---

### Post by ja4 on 2008-10-28
I got it working by doing apt-get install lprng and entering 

lpd://server.domain/queuename  
(not ldp://...)

under 'Device URI' in 'New Printer'->'Other devices'

---

