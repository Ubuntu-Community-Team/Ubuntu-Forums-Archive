---
title: "Upgrade 10.04 problem(s)"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by jack@athlonII on 2010-09-09
I upgraded 9.10 to 10.04 via the web.  The program announced it would take several hours, and when I came back to check, computer was off (kids?).

Anyway, machine boots and 10.04 starts, but then blinks a few times and goes to a prompt.  What should I tell it?

I have a 10.04 disc too, but it won't run from that either (Cannot mount dev/loop0 on filesystem.squashfs failed).  Same message when I tried to start a nearby Windows machine with it.  Disc "verified" when I made it.  What's with that?

Any advice much appreciated!

---

### Post by grief -l on 2010-09-09
you could try telling it to apt-get update

or when booting from the CD use the repair system option

---

### Post by tommcd on 2010-09-09
> **jack@athlonII said:**
> I upgraded 9.10 to 10.04 via the web.  The program announced it would take several hours, and when I came back to check, computer was off (kids?).
Anyway, machine boots and 10.04 starts, but then blinks a few times and goes to a prompt.  What should I tell it?
If the upgrade was interupted, try this from recovery mode if you can:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
Sudo apt-get upgrade

```
If that don't work then I am out of ideas I'm afraid.
> **jack@athlonII said:**
> 
I have a 10.04 disc too, but it won't run from that either (Cannot mount dev/loop0 on filesystem.squashfs failed).  Same message when I tried to start a nearby Windows machine with it.  Disc "verified" when I made it.  What's with that?

Some people have reported this. Some reported success with the DVD version of Ubuntu. Others reported success with downloading a the iso from a different mirror and burning a new CD:
[http://www.ubuntumonk.com/2010/09/02/boot-from-cd-cannot-mount-devloop0/](http://www.ubuntumonk.com/2010/09/02/boot-from-cd-cannot-mount-devloop0/)
[http://ubuntuforums.org/showthread.php?t=1556602](http://ubuntuforums.org/showthread.php?t=1556602)
I would download from a different mirror and burn a new CD at the slowest possible speed. Then boot the CD and run the option "*check disc for defects*".

---

