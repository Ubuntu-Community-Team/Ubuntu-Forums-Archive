---
title: "Remove Gnome Startup Program From Shell"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by suRoot on 2006-10-26
I'm having a brain fart & a search hasn't lead me anywhere.

Which file lists the gnome startup programs - the ones you can define under sessions from the system menu?  I've upgraded to edgy today & apparently one of the startup programs (think it is probably emerald based on the logs) is farking gnome... after logging in I see the panel for a moment & then it goes away... left with just a brown desktop & nothing more.

Created a new user account, logged in & everything is cool.  I just need to know which file I can edit from the shell to remove that startup program.

Thanks.

---

### Post by suRoot on 2006-10-26
According to the notes I just found, it used to be at ~/.gnome2/session-manual ... but I don't see such a file on my system?

---

### Post by suRoot on 2006-10-26
well... looks like it's now in ~/.config/autostart

---

