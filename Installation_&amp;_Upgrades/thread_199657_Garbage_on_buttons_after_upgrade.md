---
title: "Garbage on buttons after upgrade"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by madchicken on 2006-06-19
Hi to all.
I've successfully upgraded my Ubuntu Breezy using a Dapper CD on
a Sony Vaio PCG-K195HP.
All seems to work great with the latest patches (battery, acpi,
hibernate), except for the suspend to RAM (but I have to investigate
more deeply, 'cause it didn't work for me in breezy, so I changed some
configuration file during my tests...I have first to search for broken
config).
Another strange problem I have is that sometimes I get corrupted
images on buttons. I attach an image to this mail to explain my
problem.
I tryed to change my xorg.conf disabling and enabling some flag of the
Radeon driver (I have a Radeon IGP 345M) but nothing seems to solve
this problem.
Do anyone has an idea about this?

Thank you very much.

--
Pierpaolo

---

### Post by Gustav on 2006-06-19
It has to do with the ATI-driver and the ubuntu theme. 

If you switch theme you should get rid of it. (I don't know any better solutions)

---

### Post by madchicken on 2006-06-19
Uh...thank you very much Gustav. It worked for me too.
I thounght it was a problem due to the upgrade, not a bug.
Now I'm going to file a bug for this.

Thanks,
bye

---

