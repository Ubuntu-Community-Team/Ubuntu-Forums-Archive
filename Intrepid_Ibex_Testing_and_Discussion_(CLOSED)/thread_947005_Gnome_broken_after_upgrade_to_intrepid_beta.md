---
title: "Gnome broken after upgrade to intrepid beta"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plantboy1 on 2008-10-13
I upgraded both my systems to the Intrepid beta (I know it's a beta and there's still bugs) but it totally killed gnome one one of them.  On login, if logging into gnome, the system goes to either the brown or a black screen and just hangs and seems to lock up.  This only happens with gnome though, logging into a different interface such as fluxbox works just fine.

I've tried deleting all my gnome config files, but that didn't change anything.  

Any ideas?

---

### Post by overdrank on 2008-10-13
Moved to  Intrepid Ibex Testing and Discussion :)

---

### Post by tkiesel on 2008-10-13
I had this issue today.  Cleared up when I clicked "Session" in the login screen and chose "Gnome"

When asked whether to make this the new default. I answered yes.  All solved now.

---

### Post by jerrylamos on 2008-10-14
> **tkiesel said:**
> I had this issue today.  Cleared up when I clicked "Session" in the login screen and chose "Gnome"

When asked whether to make this the new default. I answered yes.  All solved now.

If that doesn't work, try 
booting in recovery mode
select command prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core

which fixed Beta on my IBM Thinkpad R31.  Launchpad bug 277344.

Jerry

---

### Post by plantboy1 on 2008-10-14
Yes, thanks, that worked!  Hopefully they'll iron out the problems with compiz so i can reinstall it, i miss my wobbly windows :(

Now if I could just get CUPS to work that would be REALLY nice..

---

### Post by elcman on 2008-10-20
I'm totally doing this. [I've been having a similar issue...]("http://ubuntuforums.org/showthread.php?t=942906&highlight=logging+gnome+black+screen")

I figured it had something to do with Screen Expansion or something because my computer has been acting weird with that for a while. GDM shows up fine, which made me realize that the graphical interface was working...

Here is where I posted about this on my Dell C400 computer. I'm going to jump into my failsafe terminal and remove compiz and see what happens.

It had worked dandy before the Intrepid upgrade from Hardy.

I'll confirm it now.

Sweet! That did it... thanks for the advice. I should have known to axe Compiz, but since it worked it the past, it didn't seem to make sense.

Welcome to testing!

---

### Post by InFeh on 2008-10-30
I would like to add that this happens to me too, but only on my second monitor, which runs on a different X server. My Monitor0 runs on 1280x800, and Monitor1 runs on 1440x900. The result is that the remaining 160x100 pixels "not present" on Monitor0 are drawn black; windows can not exist in them, but the mouse can.

---

