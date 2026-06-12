---
title: "switched from Netbook Remix to regular desktop, nautilus isn't drawing icons"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cdwillis on 2009-03-26
I downloaded and installed the Netbook Remix version of 9.04 and I didn't like the interface so I disabled the Netbook Launcher and Maximus and just set up the desktop as usual. The problem is that when I login there are no icons on the desktop, just wallpaper. I checked in with the gconf editor and the icons are marked to be drawn so I brought up gnome-do, typed in nautils, and voila there the icons are. How do I get nautilus to start up when I log in each time?

---

### Post by Closed_Port on 2009-03-26
I don't have NBR installed at the moment, but if I remember correctly it has a gconf-setting that tells nautilus not to draw the desktop.

So open gconf-editor and then check apps->nautilus->preferences->show_desktop

---

### Post by ronacc on 2009-03-26
how did you disable netbook-launcher ? I used the item in the menus to disable mine and it worked fine .

---

### Post by cdwillis on 2009-03-26
> **ronacc said:**
> how did you disable netbook-launcher ? I used the item in the menus to disable mine and it worked fine .

That's how I did it as well. It was under the sessions options I think? 

> **Closed_Port said:**
> I don't have NBR installed at the moment, but if I remember correctly it has a gconf-setting that tells nautilus not to draw the desktop.

So open gconf-editor and then check apps->nautilus->preferences->show_desktop

I just double checked to make sure it's checked. I unchecked it and when I did that the desktop icons disappeared. When I checked it again the icons were still missing but if I run nautilus they show back up.

---

### Post by ronacc on 2009-03-26
That is NOT how I did it , I used the menus on the left side of the netbook screen .  preferences , scroll to the bottom , swtich destop mode ,a dialog box will popup , select classic desktop .

---

