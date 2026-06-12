---
title: "Unable to log in after installing 12.04"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by LibmasterLib on 2012-06-04
Hi, I just installed 12.04 on my laptop (HP Pavilion dv6000) and now whenever I log in I just wind up with a blank screen & a cursor.  If I hit the spacebar I can occasionally get my background image before it quickly wipes away to a new screen.

Does anyone know a fix for this?

---

### Post by dino99 on 2012-06-04
boot into recovery mode to check for errors, specially unity-greeter (which can be change by lightdm-greeter inside lightdm.conf)
purging then reinstalling lightdm can help too.

---

### Post by LibmasterLib on 2012-06-04
Thanks for the reply!

How do you boot into recovery mode on 12.04?
I've tried following [the instructions on the wiki]("https://wiki.ubuntu.com/RecoveryMode") with no luck.

And then once I'm in how do I check for errors?

---

### Post by inashdeen on 2012-06-04
looks like a graphic card problem to me

---

