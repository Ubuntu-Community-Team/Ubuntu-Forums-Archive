---
title: "Cannot log in after last update in Natty"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by Colonel-Panel on 2011-08-23
If someone has posted such a solution, feel welcome to delete this thread.

If you find that you cannot log in as any user, even root, view your /var/log/auth.log file and you'll most likely see PAM moaning about illegal module types, go check the common-* files in /etc/pam.d

I had garbage inserted after the lines specifying the .ko file after the last update I did, just delete all that garbage and save the file(s) after editing.

PS: Obviously to do/check all this, boot in recovery mode, drop to root user in console mode, enter your root password.


Took me 4 hours of suffering to finally find the problem, lol

Hope I save someone that time.

---

