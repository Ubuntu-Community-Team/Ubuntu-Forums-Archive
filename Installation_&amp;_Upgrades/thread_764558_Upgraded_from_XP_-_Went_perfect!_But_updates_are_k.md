---
title: "Upgraded from XP - Went perfect! But updates are killing me!"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by snipedu1st on 2008-04-24
I had ZERO snags upgrading from XP on my IBM Thinkpad T41p.  Everything works.  Now that it's up and running, I got a balloon message that says I have 204 updates available.  I downloaded all of them and started the install.  Suddenly the laptop rebooted. Stating something about the laptop exceeded 88 degrees celsius, and automatically shut down.

After reboot, I tried to do it again and I get this error message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report."

I have NO idea what this means and/or how to fix it.

---

### Post by Monicker on 2008-04-24
> **snipedu1st said:**
> I had ZERO snags upgrading from XP on my IBM Thinkpad T41p.  Everything works.  Now that it's up and running, I got a balloon message that says I have 204 updates available.  I downloaded all of them and started the install.  Suddenly the laptop rebooted. Stating something about the laptop exceeded 88 degrees celsius, and automatically shut down.

After reboot, I tried to do it again and I get this error message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report."

I have NO idea what this means and/or how to fix it.

dpkg does all the grunt work for package management.  Its probably saying you need to make sure its data is consistent, since it was ended abruptly.

Just run the command using sudo: sudo dpkg --configure -a

---

### Post by NightwishFan on 2008-04-24
That will do it. :KS

---

### Post by Bubba64 on 2008-04-24
the two previous posts are correct but I have a feeling that you might need a little instruction. Go to application-accessories and click on terminal copy and paste this sudo dpkg --configure -a then it will ask for your password when you type it it will not show in the terminal then hit enter and your download will probably continue.

---

