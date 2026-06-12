---
title: "An Interesting Situation Regarding Boot-up."
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by ImmortalGrey on 2007-02-28
I've had Ubuntu Edgy running for a handful of days now, and the other day when it booted, it gave me a black screen, showed the toolbar at the bottom, went black again, hesitated with the toolbar again, and stayed black.  I popped in the live CD and did some research, and the advice I found was to edit the boot file and place "noapic nolapic" after a certain section so I didn't have to edit the boot parameters everytime I booted up.

The editing of the original GRUB options booted Ubuntu just fine, but after I edited and saved the boot file, I restarted to test it, and got the screen I dispise "Unknown interrupt or fault at EIP *insert several numbers here*.  So I went to the GRUB screen again, and checked the boot parameters, replaced the previous "noapic nolapic" with "acpi=off" (which is what I had to do with the live CD, or else it wouldn't boot) and things were fine again.  I loaded the boot file once again, replaced the noapic codes with "acpi=off" and saved... and got the black screen problem again.

I cannot for the life of me get this system to boot properly without editing GRUB...

Suggestions?

---

### Post by ImmortalGrey on 2007-02-28
*bumpz0r* ...

---

