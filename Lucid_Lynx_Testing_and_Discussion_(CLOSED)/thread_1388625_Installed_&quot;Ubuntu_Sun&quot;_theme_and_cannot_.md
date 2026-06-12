---
title: "Installed &quot;Ubuntu Sun&quot; theme and cannot find its gtkrc file"
date: 2010-01-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by k64 on 2010-01-23
I recently just installed the [Ubuntu Sun]("https://wiki.ubuntu.com/Artwork/Incoming/Lucid/UbuntuSun") theme. I wanted to edit its gtkrc file to enable RGBA in it (already enabled RGBA globally) and for some reason I can't find its gtkrc file.

Okay, none of the gtkrc files (there's three of them, because Ubuntu Sun is really three themes [Ubuntu Dawn, Ubuntu Day, and Ubuntu Dusk]).

---

### Post by sisco311 on 2010-01-23
How did you install the theme?

Your user's themes are in the ~/.themes directory. System themes are in the /usr/share/themes directory.

---

### Post by k64 on 2010-01-23
Okay, thank you for that tip. The instructions for enabling RGBA that I found on the Edubuntu Wiki said to look in /usr/share/themes, but thank you! I got the RGBA enabled.

---

### Post by Sashin on 2010-01-24
Did it change the appearance much?

---

### Post by k64 on 2010-01-24
> **Sashin said:**
> Did it change the appearance much?

Actually, no. I have no idea why the original hack actually created transparency, whereas this hack didn't!

I am using GNOME Shell now. It has more RGBA than librgba.c in GTK. That's because GNOME Shell uses Clutter.

---

### Post by Digikid on 2010-01-24
That looks REALLY nice!  Where can I get the Ubuntu Dusk Theme for Karmic?

Never mind.....figured it out.  Thanks!

---

