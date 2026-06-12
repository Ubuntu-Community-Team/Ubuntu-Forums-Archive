---
title: "lubuntu install drops wired network connection and hangs"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by hhbell370 on 2014-09-08
I am trying to install lubuntu from a cd on an acer 5610z.  Boots from cd normally and gets to the page where it asks if you want to update as you install, install third party perks.  It shows I have the memory, disk space, and a network connection with the green check marks.  The light is on the RJ45 socket.  I click continue and it sits for maybe 30-50 seconds and a balloon pops up saying network connection lost. The RJ45 light turns off.  It then just sits there forever with a little spinning wheel icon. There is nothing wrong with the network.  Suggestions please.

Thanks

Buddy Bell

---

### Post by varunendra on 2014-09-11
Did you tick the "Install Updates" and "Install third party perks" checkboxes (or whatever new way it has to offer them)? If so, DON't!

I am suspecting a typical b44 (for ethernet) vs wl (for wireless) driver conflict that causes such behaviour. Just do a plain install without the offered updates or third party perks - they can be installed later as and if required.

If the installation gets finished properly this way, please post open a terminal (Ctrl-Alt-T) and post back the output of the following command so we can advise whether you need any further steps/precaution.

---

