---
title: "Mouse cursor invisible after screen saver mode"
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by prickett2 on 2014-05-18
I'm running Lubuntu and after my PC comes out of screen saver mode the mouse cursor is gone.  Is this a known issue?  Is there a fix?  I upgraded to the latest version of Lubuntu and still have the same problem.

---

### Post by robbo.stanley on 2014-05-19
Are you sure it's not the mouse? I used an external bluetooth mouse and it always used to unpair if my PC went into screensaver mode. If you are using a bluetooth/wireless mouse that could be a possible reason.

---

### Post by prickett2 on 2014-05-19
I've tried two different ones with no difference in results.  Both are wired, BTW.

---

### Post by Luke M on 2014-05-19
Is the mouse working (apart from not being able to see the cursor)? In that case it's a graphics driver problem. Possibly solvable by disabling hardware cursor.

---

### Post by robbo.stanley on 2014-05-19
Hmm, i'm not really sure then. Does it fix it if you unplug the mouse then plug it back in? Have you got the brand and make of mouse, so that you can search if there are any known issues with them and Lubuntu. Sorry I can't help you anymore than this.

---

### Post by prickett2 on 2014-05-19
> **Luke M said:**
> Is the mouse working (apart from not being able to see the cursor)? In that case it's a graphics driver problem. Possibly solvable by disabling hardware cursor.

Yes, it is.  I'll try that (if I can figure out where it is set).

Thanks!

---

### Post by prickett2 on 2014-05-19
> **robbo.stanley said:**
> Hmm, i'm not really sure then. Does it fix it if you unplug the mouse then plug it back in? Have you got the brand and make of mouse, so that you can search if there are any known issues with them and Lubuntu. Sorry I can't help you anymore than this.

Thanks for the suggestions.  I'll try both when I get home.  I appreciate the help.

---

### Post by prickett2 on 2014-05-20
> **prickett2 said:**
> Yes, it is.  I'll try that (if I can figure out where it is set).

Thanks!

I tried turning off hardware cursor but don't have the file I *think* it is configured in (per another post complaining about the same issue):  [COLOR=#000000]/etc/X11/xorg.conf
[/COLOR]
My video card, btw, is a Nvideo GeForce 6150 LE.  Not sure if Lubuntu knows this or is using a default driver.  How do find that out?

---

### Post by prickett2 on 2014-05-25
I installed the Nvidia drivers and it took care of the problem

---

