---
title: "[SOLVED] Upgrade hangs on en_us.UTF8..."
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by LeGollemux on 2008-08-12
I am upgrading my server from 7.1 to 8.04 LTS. On finnalising the upgrade with 6 minutes to go the installation froze on "setting up locales. (2.7.9-4)" while setting up "en-us.UTF8...".

after a few hours of waiting, I did the alt-F thing and typed sudo apt-get upgrade. it came back and said dpkg had been interrupted and I was to run it again with --configure -a set.

I did.. it got stuck again in the same place.

any suggestions?

---

### Post by snowpine on 2008-08-12
> **LeGollemux said:**
> I am upgrading my server from 7.1 to 8.04 LTS. On finnalising the upgrade with 6 minutes to go the installation froze on "setting up locales. (2.7.9-4)" while setting up "en-us.UTF8...".

after a few hours of waiting, I did the alt-F thing and typed sudo apt-get upgrade. it came back and said dpkg had been interrupted and I was to run it again with --configure -a set.

I did.. it got stuck again in the same place.

any suggestions?

Hi there, check out this thread: [http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679)

It is a common problem, but there is a work-around. Good luck!

---

### Post by null byte on 2008-08-12
This guy had the same problem.

[http://ubuntuforums.org/showpost.php?p=5573509&postcount=28](http://ubuntuforums.org/showpost.php?p=5573509&postcount=28)

More info: [https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

---

### Post by LeGollemux on 2008-08-13
that was amazing. I got assistance in under a minute!!
Problem solved! Thank you.

I loaded the previous kernel. Logged in under "safe mode" and ran "dpkg --configure -a".

done.

---

