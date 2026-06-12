---
title: "stupid upgrades"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by Bart Ellebaut on 2007-04-18
I just succesfully installed ubuntu, made everything work. Been working on it for about 6 hours.
Now my ubuntu wanted to update. removed some thing, restarted my pc, and now it freezes. I can typ in my usersname and password, but than the whole system freezes. 
Anyone had this problem??
Didn't expect this from linux!!

I have to start all over again, formatting HD en installing everything.

---

### Post by Jeremy23 on 2007-04-19
Is this coming from selecting the wrong kernel when your system boots up? I know I had that problem (keyboard/mouse freezing).

When your system first boots up, before the Ubuntu logo comes up, you will see "GRUB". Hit ESC to stop it booting automatically. Then, try booting with the top-most kernel available.

Might be worth a try.

---

### Post by rillip on 2007-04-19
Try booting into a recovery kernel, or a default x386 kernel instead, I agree with Jeremey, it sounds like this could be just such an issue.  You say it freezes completely after the username and password.  I assume you're typing this into gdm/kdm?  Try chosing to go to console from the menu, and see if after you login you get any errors you can give us.

---

