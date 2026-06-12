---
title: "Can't shutdown after upgrade to 11.10!!!!!"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by matteosistisette on 2011-12-07
Hi,

After upgrading to ubuntu 11.10, shutdown doesn't work!!! 
I click on "shutdown", then I select wither "shutdown" or "restart" and in both cases absolutely nothing happens.

Logout doesn't work either.

Only hibernate works.

Does anybody know a fix?

Thanks
m.

<rant>
This is the most absurd, most ridiculous and worst bug ever.
Indeed the upgrade to 11.10 has been only regressions. A lot of basic things have stopped working. 
I guess this is because of the stupid commitment of releasing a new release every six months at all costs. Missing a release would do less damage than releasing a broken one where the most basic things stop working. 
</rant>

---

### Post by bluexrider on 2011-12-07
try this in terminal

sudo shutdown -h now

it may be an issue [https://bugs.launchpad.net/ubuntu/+bug/882817](https://bugs.launchpad.net/ubuntu/+bug/882817)

---

### Post by darkod on 2011-12-07
Or a little shorter terminal command is:
sudo poweroff

---

### Post by bluexrider on 2011-12-07
> **darkod said:**
> Or a little shorter terminal command is:
sudo poweroff

user pull-cord-out-of-wall

---

