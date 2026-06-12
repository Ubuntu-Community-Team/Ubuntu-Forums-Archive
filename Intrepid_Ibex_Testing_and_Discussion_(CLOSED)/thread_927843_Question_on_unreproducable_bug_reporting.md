---
title: "Question on unreproducable bug reporting"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Tatty on 2008-09-23
Since instaling Ibex I have had a few occasions where an application has crashed in the background, whilst I have been doing nothing obvious to cause it.  The only reason I have known they have crashed is because the "an application has crashed, do you want to report it to developers?" dialog has appeared.

As these bugs are unreproducable as I am not aware of what may have caused them and so could not give much details on it, i have always hesitated to report them.  I was wondering what the correct procedure is for this.

I have had compiz,nm-applet and even crash-apport(sp?) itself crash in this way in the last few days.

My trash applet just crashed whilst I was not actively doing anything on my machine, and I am sitting here wondering wether to click the "report" button, or wether it will not help.

---

### Post by Nullack on 2008-09-23
Apport dumps get sent to LP. If the devs want to get further info, theyll ask for it in the bug report such as installing debugging symbols and waiting for the next apport dump to give them the info.

---

### Post by Tatty on 2008-09-23
> **Nullack said:**
> Apport dumps get sent to LP. If the devs want to get further info, theyll ask for it in the bug report such as installing debugging symbols and waiting for the next apport dump to give them the info.

Ah so you are saying to just send the report anyway?

Thanks, I will do this next time I get a crash caught by apport. :)

---

