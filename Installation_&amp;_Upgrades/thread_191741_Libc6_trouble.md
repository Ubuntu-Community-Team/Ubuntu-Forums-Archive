---
title: "Libc6 trouble"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by Selbstmord on 2006-06-07
I'm running Ubuntu 6.06 with Gnome, upgraded from Breezy Badger on an old laptop.

I have no idea how this happened, but can someone tell me what's going on?

Libc6 and it's sidelibs (3 in total) are identified as broken, but I can't remove them or install any new ones over them.

This is the output I get;

The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-7 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Please help, as I'm thinking my computer won't boot into Ubuntu when I turn it off...

---

### Post by r4ik on 2006-06-07
There is a section about Libc6 here,

[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Hope it has some pointers for you.

Good luck !

---

### Post by Selbstmord on 2006-06-08
Still have the same problem, I can't install ANYTHING at ALL. So things like that don't exactly help me...

But thanks anyway

/F

---

### Post by effoff on 2006-06-08
if you upgrade libdb2 and perl as well you'll probably be OK...
This is a chicken and egg problem: if you force remove before upgrade, dpkg won't work. It's kinda like a surgeon operating on himself. Anesthesia (Shutdown) is necessary to upgrade (operate), but the surgeon can't operate asleep. DPKG cannot easily remove itself out of the way to replace one of its essentials while it is working. Normally upgrade scripts take all this into consideration....

I had a similar problem and went ahead and shutdown anyway.... And the install was "magically" fixed upon reboot. I went into synaptic and checked "broken", clicked on "fix" and the db was updated and the "apply" button was grayed-out indicating nothing to apply. The list showed that the upgrade had taken place.

---

### Post by nomail on 2006-06-11
here what I did: I just googled up for version of libc6 which libc6-dev depends on. And then reinstalled it.

So go to the [http://packages.ubuntulinux.org/dapper/base/index.hu.html](http://packages.ubuntulinux.org/dapper/base/index.hu.html)
Download correct libc6 version(libc6_2.3.6-0ubuntu20_i386.deb) and then just
sudo dpkg -i libc6_2.3.6-0ubuntu20_i386.deb

that's it....well at least it helped me:rolleyes: 

Best regards,
nomail

Sorry for my rubbish english

---

