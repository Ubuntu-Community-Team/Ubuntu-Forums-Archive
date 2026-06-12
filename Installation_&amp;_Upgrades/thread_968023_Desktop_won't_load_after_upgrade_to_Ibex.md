---
title: "Desktop won't load after upgrade to Ibex"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by YorNamHere on 2008-11-02
I just got done with the upgrade from Hardy to Ibex and now my desktop won't load.  I did the upgrade through the update manager, it ran smoothly, restarted and went to the login screen.  I enter my user name and password, it goes to the brown screen before the desktop is loaded and then stops.  I tried using the failsafe GNOME session, but it does the same thing.

If anyone can help it would be GREATLY appreciated!
Thanks!

---

### Post by kylebridge on 2008-11-03
I'm having the same problem!  I can't find anything that's worked, I just tried KDE and that didn't work either.

---

### Post by jerrylamos on 2008-11-03
8.10 Intrepid Ibex may freeze after login on many computers with Intel graphics cards.  The cause is the compiz code that does fancy "eye candy" effects.  The fix is to remove compiz.  Actually the "official fix" which is just out didn't make it into the release code.  The "official fix" is to "blacklist" some intel codes and then to not run the compiz code.

To see if this is your problem:

boot in rescue mode
at the menu, choose
root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit 
resume normal boot

Works for me and lots of other people if you scan the posts for black or brown or orange screen.

Jerry

---

### Post by YorNamHere on 2008-11-03
Just tried it and it works perfectly!  Thank you so much for the help.

Quick question:  Has the compiz problem been fixed?  Can I download the newest version and will it work properly? (The eye-candy helps when I'm pimping Ubuntu on the Triple-E :biggrin:)

Thank you again, and I will definitely try the search criteria you suggested next time!

YNH

---

### Post by abn91c on 2008-11-03
I have a dimension 2400 with Intel 845 card, had the same problems with Kubuntu, go to the recovery log in, make sure you can access the Internet, do dhclient eth0 if you have to. Also you need to be root. What worked for me was installing metacity
sudo apt-get install metacity, accept whatever it tell you. after its done do metacity --replace(this installs a basic gnome desktop)
If you are able to log in then turn off the desktop effects, Im using Kubuntu its under  system settings, desktop
this is what worked for me, by the way it installed a minimal gnome desktop and i changed the settings from there and I was able to log in to kubuntu then.

---

### Post by akrapacs on 2008-11-05
Worked perfect for me on a Dimension 2400. Thanks!

---

