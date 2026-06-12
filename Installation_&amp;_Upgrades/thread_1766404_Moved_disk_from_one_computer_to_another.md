---
title: "Moved disk from one computer to another"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by Fake51 on 2011-05-24
Hi everyone

I could use some crowd-wisdom on this one. I've just switched working computers (both stationary) and I've taken the boot disk out of the old one and stuck it in the new one.

So far, so good - everything (net connection, graphics, general system) seems to work just fine. However, being somewhat paranoid, I wonder what else I can check to make sure I haven't overlooked anything. What things should I check to make sure my old setup is compatible with the new computer?

---

### Post by satanselbow on 2011-05-24
A good old fashioned 

```

sudo apt-get update
sudo apt-get dist-upgrade

```

should take care of any missing bits I would have thought ;)

Likewise if there are any "un-required" bits left lying around a

```

sudo apt-get autoclean

``` 

will shift 'em ;)

Couldn't do that with a windows install :popcorn:

---

### Post by Fake51 on 2011-05-25
Thanks, doesn't look like much more is needed - did this and the system was up to speed (had a slight bit of lagging before but that took care of it). Now just need someone with time and skills to fix the Intel drivers for i915/sandy bridge (whichever is the problem) :)

---

