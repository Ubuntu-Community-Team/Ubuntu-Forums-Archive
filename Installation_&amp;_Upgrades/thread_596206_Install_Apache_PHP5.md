---
title: "Install Apache PHP5"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by nubie777 on 2007-10-29
I am attempting to install apache2 &  php5.  I'm following: The Perfect Setup - Ubuntu Feisty Fawn (Ubuntu 7.04) [http://www.howtoforge.com/perfect_setup_ubuntu704_p6](http://www.howtoforge.com/perfect_setup_ubuntu704_p6) starting on page 6.

Apache2 installed successfully.

However, for the php install, I have run into a package dependency problem. libssl-dev and libtools have unmet dependencies as follows:

libtool:  Depends: **libc6-dev**

libssl-dev: Depends: zlib1g-dev
   zlib1g-dev: Depends: libc6-dev
      libc6-dev:  Depends: [B]libc6 (=2.5-0ubuntu14) but 2.6.1-5 is to be installed
[/B]
The problem I think is that I need lib6c-2.1.5, but I have lib6c-2.1.6-5 installed.  I can't uninstall ib6c-2.1.6-5 because it will remove well over 200 items that are installed.

I've included a screen shot of synaptic package manager's message.

Any idea how I can resolve this situation?

Thanks,

Cheers!

---

### Post by stuffer007 on 2007-10-30
I just tried that and it worked, I am using Gutsy Gibbon, all i needed was the install CD for Gutsy.

---

### Post by timcredible on 2007-10-30
i ran into this with 7.04 - i had to upgrade to 7.10, no other way around gcc library dependency issues like that.

---

