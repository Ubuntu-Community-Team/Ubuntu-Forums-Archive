---
title: "Bios Age"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by jdcar81 on 2007-12-30
I was trying to install xUbuntu on a relatively old machine (used to run windows 98).  When I chose the install option from the screen that the cd pulls up, it gives me the message that the bios age is too old (1999) so it failed the cutoff (2000) and acpi=force is required to enable acpi.  The computer would not do anything else. Does this mean my computer is too old for xUbuntu?  Is there any way around this?

---

### Post by oldos2er on 2007-12-30
You can always try updating the BIOS.

---

### Post by jdcar81 on 2007-12-30
How do I update the Bios?  BTW I am doing a clean install.
Thanks

---

### Post by jdcar81 on 2007-12-30
I tried using the alternate install cd instead of the desktop install cd.  I don't get the bios age problem, but I am still having problems.  When I select install, it goes through a few screens of text and returns to the main install window.  What am I missing?

---

### Post by logos34 on 2007-12-30
maybe try hitting F6 and adding this boot option:

noacpi

(older pc's use APM power managnement)

may not help but give it a shot anyway.

To flash the bios with an update you would go to mobo manufacturer website and download it to a floppy

---

### Post by soleille on 2008-03-10
This is seriously weird - I have had the same problem and upgraded the BIOS (well- had someone upgrade it, this looked way over my head) on my T20

It IS upgraded now (a good 10 versions above the one I had) - however, *all* versions have the *same* BIOS date somewhere in 1999 - so it still fails cutoff age.

While this means Ubuntu doesn't usually start up at the first try, the third or so mostly does it - and weirdly enough, if I've booted windows, restart and then boot Ubuntu, it comes up on the first try without fail.



Will the suggestion of "noacpi" or, as seen in another thread, "boot action acpi=off apm=on" get rid of the startup problem? With no acpi I still won't be able to hibernate etc right? Can something else be messed up if I add this?

If this is a good idea, can I have a aimed-at-idiot walkthrough through setting this boot option please? (when, where and how exactly do i do it?)

Oh, and can I even be sure that APM instead of ACPI is what the computer needs? In windows suspend, hibernate etc. worked without fail, but I have no clue what they use for that and wouldn't know how to find out....

---

