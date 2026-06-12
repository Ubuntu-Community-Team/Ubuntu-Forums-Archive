---
title: "Boot up hangs unless a key is held down"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by ljoslin on 2008-10-31
I just upgraded to 8.10, the install worked, had some minor issues (my wireless card, to be expected, and /etc/sudoers permissions were changed?!, place->home opened totem - fixed)  this one...it's not really a problem, but really freaking weird!!

When booting up grub loads, I choose my kernel, goes to the splash screen (I have quiet off) and then stops booting?!

The first time this happened I went to goto another terminal by hitting ctrl-alt-f1 just to see if that showed anything, as I hit ctrl-alt it started booting again, so I let go...it promptly stopped again, hit the keys again and it started booting again?!

I have rebooted many many times and have the same thing happen, it doesn't seem to matter what key I press as long as I have a key pressed.

Any ideas?!  My other computer that is similar amd 64, nvidia, 2 gigs ram, sata drives boots just fine w/o a key being pressed. Any ideas?!

-=Ljoslin=-

---

### Post by ljoslin on 2008-11-07
I fixed this by adding acpi=noirq  to the menu.1st grub file...not a great fix, but at least the machine boots now.  Maybe this will bump up the post and someone will have a better fix.

-=ljoslin=-

---

