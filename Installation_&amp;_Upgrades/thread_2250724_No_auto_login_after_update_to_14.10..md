---
title: "No auto login after update to 14.10."
date: 2014-10-30
forum: Installation &amp; Upgrades
---

### Post by KFoder on 2014-10-30
Hi

Since I updated my kubuntu 14.04 to 14.10, the auto login feature has stopped working.

I have always had auto login enabled on this computer, and it is still enabled in lightdm settings, and in the user manager, but still I'm asked to enter my password at startup!

I have tried to disable autologin, reboot and enable it again, reboot again, but to no avail.

Any ideas? 
Has any one else had this problem?

Kim

---

### Post by KFoder on 2014-10-30
Problem solved

It looks like I was running kernel 3.13, the upgrade had installed 3.16 but for some reason that's not the one that booted!

Unfortunatly this was discovered when I removed the 3.13 kernal, and had a dead computer at restart :(

Reinstalling 3.16 solved (both) problems!

Kim

---

