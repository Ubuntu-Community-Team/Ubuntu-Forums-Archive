---
title: "Where did my filesystem go?"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by MuttonchopsXXY on 2010-01-04
Problem with suddenly invisible (or missing?) filesystem.  I have been a software developer for over 30 years, with occasional unix exposure, but not much admin experience.  I installed Karmic on my laptop, and have been pursuing a two-headed configuration that has proved elusive.  I tried to set up twinview, but I haven't gotten it to work.  In the process I ran with an xorg.conf which was in an Ubuntu forum.  When it failed (with lots of useful diagnostic info), I tried to boot to a command line to restore the known good xorg, but found myself in a loop between the following screens:

1) "How would you like to reconfigure your display?"  "Use Default".
2) "Failure restoring configuration to default.  Your config has not been changed".
3) "How would you like to reconfigure your display?  Create new configuration for this hardware".
4) "A new configuration has been generated and your old configuration backed up.  Please restart.  Failure restoring configuration to default.  Your config has not been changed.
5) "How would you like to reconfigure your display? Use your backed up configuration.
6)  "How would you like to reconfigure your display?

And around and around...

At one point earlier, I got to a "recovery" command line in the root dir, but it seemed to think there were no files (or dirs) at all below that dir.  I hope that is not the case.

What is happening and how do I move forward??

Thanks for whatever help anyone can supply.

---

### Post by steveneddy on 2010-01-04
Did you back up or change the name of the old xorg.conf file to a different name, like put a little "**~**" at the end?

EDIT:

Here is a link from my sig (Ubuntu Guide: Karmic - 

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Reconfigure_xserver-xorg](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Reconfigure_xserver-xorg)

Hope this helps....

---

### Post by MuttonchopsXXY on 2010-01-04
I was going to say there were at least one or two copies of the original xorg.conf in /etc/X11, but I would have been wrong.  There are 7 copies total, most with long trailing date strings.  I don't know exactly what happened there, but it looks like I am good to go on.  I think I will leave all of the config files as is and maybe even squirrel one or two copies away for safekeeping, as well.

I will study your xorg.conf and build mine from it, as it seems that you were dealing with the same hardware as I am.  I will certainly have another question or two as I press on,  but for now, prospects are a lot brighter.

Thanks for your time & effort.

P.S. One protocol question: Should I continue this thread if I encounter more problems or questions, or should I start a new one?

---

