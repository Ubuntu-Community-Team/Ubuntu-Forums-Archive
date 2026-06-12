---
title: "Shell script for installing updates"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by manfromthezoo on 2010-06-16
Hello all.

I'm looking to put together a script, called by a cron job on a daily (or weekly) basis, to automatically have apt-get pull down and install all updates, followed by a re-boot.

Anybody care to venture anything?

Cuddles for the winner.

---

### Post by gradinaruvasile on 2010-06-16
Reboot? What, are you running Windows or something?
Reboot is only required on kernel update or the like.
Not to talk about the implications - picture yourself doing something when the computer suddenly reboots. Not nice... even vorse than Windows.

I have a very simple bash script i use for updates:

#!/bin/bash
sudo aptitude update ; sudo aptitude upgrade

I use this logged in as user.
If you modify it to something like this:

#!/bin/bash
aptitude update ; aptitude upgrade -y && reboot

it probably will do the job. But the problem is that you wont know what really happens if it runs and can mess up your system in some cases when packages are automatically removed.

---

### Post by manfromthezoo on 2010-06-16
Thanks, those look useful.

Yes, I was referring to wanting to re-boot in the case of kernel updates. The machine itself is effectively just a notice board device, and so no-one will be using it in the middle of the night :)

I'll take a look at using these.

---

