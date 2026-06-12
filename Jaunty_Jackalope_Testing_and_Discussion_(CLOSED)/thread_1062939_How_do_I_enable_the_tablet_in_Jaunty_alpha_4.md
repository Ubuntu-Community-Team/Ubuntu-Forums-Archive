---
title: "How do I enable the tablet in Jaunty alpha 4?"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tariqf on 2009-02-07
Hi how do I enable the tablet on my TOshiba M400 on jaunty alpha 4? 

It works in 8.10 with the xorg.conf changes as per the wiki however the Xorg version in Jaunty does not accept the serverlayout part so I'm stumped.

Thanks in advice for any advice or comments.

---

### Post by tariqf on 2009-02-12
Has anyone got any success with a tablet laptop and Jaunty at all? Have been trying for a week now and still cannot get the graphire intuos tablet in my toshiba laptop working.

---

### Post by Favux on 2009-02-12
Hi tariqf,

Your making me nervous.  I thought they had agreed to give more support to tablets in Jaunty.  There is suppose to be a gui to configure xorg.conf.  Maybe it isn't finished.  I do not know its name.

I imagine your running into the changes of the new Xserver 1.6

This discussion:

[http://www.nabble.com/Tablet-hotplug-and-dbus...-td21040661.html]("http://www.nabble.com/Tablet-hotplug-and-dbus...-td21040661.html")

talks about a gnome tablet app or gnome graphics tablet app, which appears to be a configuration gui.  But I'm not sure it is the same one as we're suppose to be getting in Jaunty.

Also this bug report:

[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/318172]("https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/318172")

You could try and see if the man pages have been changed:

man wacom
man xorg.conf

and

man Xserver
man Xorg

Good luck!

---

