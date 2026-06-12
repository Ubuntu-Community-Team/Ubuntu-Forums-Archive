---
title: "Kubuntu KDE4 &amp; GTK issues &amp; KDE 4.0.4"
date: 2008-05-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by disturbedite on 2008-05-12
i did a clean install of kubuntu intrepid w/ kde4 x86.
i test daily builds of firefox3, it will not close properly.  (closes the interface, but stays open in the background, confirmed via system monitor).
i like synaptic, for one reason, cuz its faster, so i use it.  now i've been forced to use adept cuz synaptic won't close properly either.  its a slightly different problem than with fx3.  i have the option ticked to "close when updates are successfully applied" but it never does, even when the updates are successfully applied.  i have to kill the app to get it to close.

has anyone else experienced these type of problems with gtk apps in kub-kde4?



oh, i also changed my sources.list to hardy-backports to get kde 4.0.4.  (for some reason, kde 4.0.4 isn't in intrepid, & intrepid is newer)!  i updated all the kde4 packages to 4.0.4, but all my kde4 packages/interfaces still say 4.0.3.  did someone forget to update the version strings?  (i have confirmed that the 4.0.4 packages *are* actually installed via my package managers & i didn't encounter any problems updating the packages).

should i have not switched to the hardy-backports repo?

---

### Post by chaddles on 2008-07-25
I've got the same issue with synaptic on KDE4 when starting it from the K Menu, but I found running "gksudo synaptic" works fine.

---

### Post by Bachstelze on 2008-07-26
No issue here with up to date Intrepid (KDE 4.0.98). I'm not using Synaptic, but all my GTK apps (Firefox, Pidgin, Gimp) seem to operate normally.

---

