---
title: "Not authenticated updates"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by karmah on 2005-07-26
I get non-authenticated updates, last time I allowed these, things f***ed! Should I update? :S That "New updates availible" thing is in my tray and it will probably make me update anyways if no-one stop me!

Please, gimme some advice!
Thanks in advance.

---

### Post by Xian on 2005-07-26
Depends on what repo the non-authenticated packages reside. If they are Hoary backports then you should be relatively safe in upgrading your system using what Apt presents to you for consideration. I've certainly never encountered any problems with those packages on my box.

Do you recall what packages gave you the issues you describe?

---

### Post by karmah on 2005-07-26
GAIM, GIMP, gtk-2, powernowd (? :S), firefox.

How do I check what repo it is?

---

### Post by varunus on 2005-07-26
Ubuntu does not force you to update.  If you don't want to, then don't...but bugfixes are good to have.

Those packages sound OK to update...One way to see is to open up the Synaptic Package Manager, look at the packages it wants to update, right click them and choose properties, and look at "versions."  It'll tell you what repository each one is from.

Can you post your /etc/apt/sources.list?  If you haven't modified this file, or if you just followed the instructions in the UbuntuGuide, then you should be able to just update.

---

### Post by Xian on 2005-07-26
It has to be Backports if you are getting FF and Gaim updates.

---

### Post by karmah on 2005-07-27
Ah ok then, I'll just go ahed and update :). thx.

---

