---
title: "Disabled PPAs"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by Norm24 on 2016-08-07
I'm pretty sure I know what the answer will be but it never hurts to ask.

After upgrading from 14.04 to 16.04 all my PPAs were disabled.Is there a way to upgrade all my PPAs from Trusty to Xenial in one shot or do I have to manually remove each one and re-add them individually?

---

### Post by TheFu on 2016-08-07
Yep, you know the answer.

Best to re-enable them 1 at a time. Not all PPAs from these 3rd parties have been updated, so some probably won't work with the newer release.  Better to see that 1 at a time and decide on alternative solutions (or not using that software) as it happens.

Of course, you could re-enable all of them at once and try to figure out the issues, but since dependencies can become complicated, I'd do it 1 at a time.  I'd accomplish this with a few terminals and have them all in the /etc/apt/ directory to either edit/write the changes to 1 file or rename the apt.conf.d/ files so they are picked up again. I wouldn't use the GUI for this, but that is just me. ;)

---

### Post by Norm24 on 2016-08-18
Y-ppa manager!!!Made life much easier.

---

