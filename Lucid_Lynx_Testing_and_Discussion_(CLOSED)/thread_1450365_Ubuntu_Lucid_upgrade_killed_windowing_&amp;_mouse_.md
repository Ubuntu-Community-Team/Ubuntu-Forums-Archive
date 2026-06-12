---
title: "Ubuntu Lucid upgrade killed windowing &amp; mouse pointer!"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sporkman on 2010-04-09
Posting this in case anybody else runs into this problem:

So I did a update/upgrade/dist-upgrade tonight & rebooted...

When the login screen comes up, there's no mouse - weird. I log in, and the mouse appears but it's the big ugly "X" shape of yore. The rest of the desktop appears as normal.

When I open something like a terminal or firefox, it opens up at the top left corner, with no window border or general window functionality.

When I tried to start gdm in the terminal, it would fail with "Failed to acquire org.gnome.DisplayManager".

Here's how I fixed it:

```

sudo bash
apt-get purge gdm ; apt-get install gdm

```

...then reboot.

Everything's now back to normal. :)

---

### Post by Sporkman on 2010-04-10
It started happening again. :( Happened after a reboot.

The cursor looks normal, but the window action doesn't work as per above. The above purge & install doesn't fix it.

---

