---
title: "All Windows Maximized!"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iheartubuntu on 2009-04-05
I dont think this is specific to Jaunty, but here I am because I have this problem on my Jaunty laptop. Any window I open up, opens in full maximized mode and the minimize/maximize/close icons are not available (or see-able). I need to press ALT+F10 to bring each window back to normal. If I close out a window and reopen, same problem occurs. Rebooting didnt help. Would anyone know how to fix this? This problem just started recently after upgrading to Jaunty. Ive checked compiz to see if there were any settings I could change, but nothing. Must not be a compiz prob since I still have the prob with compiz turned off too. I noticed this soon after I accidentally pressed some combination of keys, but dont recall what was pressed. So I am thinking there must be some key combination to fix this? Anyone? Much help would be appreciated, its really annoying! TIA.

---

### Post by iheartubuntu on 2009-04-05
Problem solved...

> **tim.read said:**
> i found the solution to my problem via the .xsession-errors file as it showed errors related to an application named "maximus".

For some reason this application is now one of the default startup applications. I disabled it under "system / preferences / startup applications" and now my desktop applications work the way they used to :-)

---

### Post by mdurham on 2009-04-05
I wonder how you got this 'maximus' thing? It's not on my machine.
Cheers, Mike

---

### Post by iheartubuntu on 2009-04-07
Good question... I have no idea. Installed Jaunty on two of my computers... Laptop at home which got this maximize thing, and a desktop at work which never got it. Im doing the updates daily. These were both upgraded from 8.10.

---

