---
title: "how can I fix an IRQ conflict?"
date: 2006-05-01
forum: Installation &amp; Upgrades
---

### Post by kludge on 2006-05-01
What can I do to resolve an IRQ conflict?  Is there a kernel parameter I can use to explicitly assign an IRQ to a particular device or something?  

I'm pretty sure the gdm freeze problem I posted about on saturday is being caused by an IRQ conflict between the wireless card and the ATI video drivers on my VAIO laptop.  I've tried using the binary ATI drivers as well, but they just cause a kernel panic rather than a lockup - not much progress!  I think that if I can end the IRQ conflict, I can get the wireless and graphics working together.

---

### Post by tseliot on 2006-05-01
Try to pass "irqpoll" as a boot parameter.

If you don't know how to do that, try this guide:
[http://ubuntuforums.org/showthread.php?t=75281]("http://ubuntuforums.org/showthread.php?t=75281")

and read the part about:
> OTHERWISE

b) If you have installed Ubuntu...

I hope it helps

---

### Post by kludge on 2006-05-01
Ah, that looks like the kind of thing I've been seeking.  I'll try it tonight.  Thanks!

---

