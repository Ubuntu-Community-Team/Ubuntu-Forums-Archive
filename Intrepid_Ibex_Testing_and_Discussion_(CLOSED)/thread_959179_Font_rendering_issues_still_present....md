---
title: "Font rendering issues still present..."
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sslaxx on 2008-10-26
Ubuntu 8.10 still has issues with rendering of fonts as of 26/10/08's updates. It's entirely inconsistent about how it does it, meaning lines can be larger or smaller, numbers get rendered oddly (sometimes correctly, sometimes serif) and monospaced fonts don't line up properly. I've watched the line spacing and number rendering change as I've typed this up.

Has anyone else experienced these issues? Is there any workaround?

---

### Post by psyke83 on 2008-10-26
> **Sslaxx said:**
> Ubuntu 8.10 still has issues with rendering of fonts as of 26/10/08's updates. It's entirely inconsistent about how it does it, meaning lines can be larger or smaller, numbers get rendered oddly (sometimes correctly, sometimes serif) and monospaced fonts don't line up properly. I've watched the line spacing and number rendering change as I've typed this up.

Has anyone else experienced these issues? Is there any workaround?

It seems this problem is isolated to your system (and therefore may be a configuration/upgrade issue). Did you upgrade from Hardy? Did you ever perform a partial upgrade that may have removed packages?

---

### Post by Sslaxx on 2008-10-26
Yeah, it was an upgrade from Hardy.

---

### Post by caro on 2008-10-26
I experienced a similar problem with 7.10 but it was random and limited to the web browser.  I'm not sure what caused it and it eventually went away (with an update to either 7.10 or Firefox), but there were bugs submitted on launchpad for this that may give you some idea of where the problem lies.  

I could close my browser and relaunch and it would correct the symptom if not the source of the problem.

---

### Post by Sslaxx on 2008-10-26
It isn't just Firefox. The panel's exhibiting the same issue, and as is gEdit. I've seen bits of text being "chopped" because of the font rendering problems. This has been reported before, but I can't find the original thread, otherwise I'd have bumped it.

---

### Post by forumache on 2008-10-27
Try creating a new user. Log in as that user. Do you still see the problem? If not, you are lucky, the system is OK, just your user configuration is messed up (solutions exist). If it is still messy for the new user, then you focus your troubleshooting on the system files (it can be done).

So, which one is it?

---

### Post by Sslaxx on 2008-10-27
It was system-wide. I decided not to bother and re-installed using the Intrepid RC CD. So far, it appears not to have re-occured...

---

