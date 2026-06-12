---
title: "Post-Install: login, no Gnome, no nothing!"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by pointym5 on 2005-07-01
I've managed to get an install completely through on an older IBM laptop: no complaints at all through the entire process (a first for me).  It got all the way to presenting me with the "gdm" login screen, looking just like all my other Ubuntu systems; it even gave me the drumroll.

I logged in and waited. And waited.

After some time it became clear that none of the Gnome stuff, or anything else for that matter, was going to show up.  I can toggle to the alternate consoles and log in, and everything seems fine; it's just that X and Gnome are completely non-functional. What would be likely to cause that?

I didn't do anything about package selection at all during the installation; it's just a stock vanilla machine.

---

### Post by michael_salcher on 2005-07-01
[QUOTE=pointym5]I've managed to get an install completely through on an older IBM laptop: no complaints at all through the entire process (a first for me).  It got all the way to presenting me with the "gdm" login screen, looking just like all my other Ubuntu systems; it even gave me the drumroll.

I logged in and waited. And waited.

After some time it became clear that none of the Gnome stuff, or anything else for that matter, was going to show up.  I can toggle to the alternate consoles and log in, and everything seems fine; it's just that X and Gnome are completely non-functional. What would be likely to cause that?

I didn't do anything about package selection at all during the installation; it's just a stock vanilla machine.[/QUOTE]
 the xserver is working if you see the gnome login.

---

### Post by pointym5 on 2005-07-01
[QUOTE=michael_salcher]the xserver is working if you see the gnome login.[/QUOTE]

Yes, I know that.  But essentially nothing else about the UI is working.

---

### Post by Fnyx on 2005-07-04
Having the same problem on a standard PC. Same problem with Hoary Live.

---

### Post by dejitarob on 2005-07-04
Try switching to one of the virtual consoles by pressing "CTRL+ALT+1" and seeing if its still finishing up some installation stuff.

---

### Post by Fnyx on 2005-07-05
The last thing I see before x starts and GDM pops upp is:
*Loading ACPI modules...

If I go to a virtual console I see this after ACPI... :
*Starting advanced configuration and power interface daemon...
*Starting system message bus:
*Starting hardware abstraction layer:
*Starting internet superserver...
*Starting postfix mail transport agent
This processor "AMD Athlon(tm) Processor"  is known _not_ to support power-saving
*Starting powernowd...
*CPU frequency scaling not supported
*Starting anac(h)ronistic cron: anacron
*Starting deferred execution scheduler...
*Starting periodic command scheduler...
*Checking battery state...

[OK] on all of them.

The last one seems a bit odd to me.
Any ideas?

---

### Post by Fnyx on 2005-07-06
Anyone?

---

### Post by epukinsk on 2005-07-09
I am having the exact same problem on an IBM Thinkpad 600x.

I haven't figured anything out, but I'll post here if I do.  

Does anyone know what might be causing this, it seems like a number of people are experiencing the same problem.  Maybe we should file a bug.

Erik

---

### Post by epukinsk on 2005-07-09
I do have a couple of tips though:

1) You *can* start up with the Failsafe Terminal session, and you'll have an xterm window.  I have been doing that, and then doing:

```
metacity &
```

That will let you manage windows.  At this point I couldn't start gnome apps (like the panel) because of the drumroll thing.  To fix that, you need to do:

```
sudo killall aplay
sudo gdmsetup
```

And then uncheck "Make a sound when login window is ready" in the "Accessibility" tab.  Now you won't get the drumroll any more and you can start gnome apps.  I then do:

```
nautilus &
gnome-panel &
```

And that gives me a basic environment.  However, the themes and fonts are messed up, and it's a pain in the butt, but it's a temporary solution to make your machine usable.

But I would sure appreciate some help fixing the gnome login thing.  I just don't know how to troubleshoot the login process--how to tell what's happening when Ubuntu is just sitting there twiddling its thumbs.

Erik

---

### Post by epukinsk on 2005-07-10
Yay, I figured it out.  Well, I found another forum post that explained the problem:

  [http://ubuntuforums.org/showthread.php?t=46740](http://ubuntuforums.org/showthread.php?t=46740)

The solution (for me) was just to apt-get install polypaudio and reboot.  It takes a few seconds for the splash to come  up, but it came!  And now I am using Hoary in all it's glory, Gnome 2.10... Beagle... sweet.

Erik

---

