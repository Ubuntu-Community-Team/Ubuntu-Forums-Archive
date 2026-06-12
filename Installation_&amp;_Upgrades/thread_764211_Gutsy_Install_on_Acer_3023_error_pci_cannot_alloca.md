---
title: "Gutsy Install on Acer 3023 error: pci cannot allocate resource region 7"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by ricketick on 2008-04-23
Hi there,

After booting using the Gutsy alternate cd and adding noapic in command line at the install screen, I get four of these messages:
pci cannot allocate resource region 7 in bridge (followed by some zeros and numbers). Then the screen halts at black.

I've looked around and most people who installed acer aspire 3023 succeeded with their installation after adding noapic, however I do not.

Any suggestions?

Best

---

### Post by Pumalite on 2008-04-23
This might help:
[http://doube.org/ubuntu3023.html](http://doube.org/ubuntu3023.html)

---

### Post by ricketick on 2008-04-23
I don't think it will, I have already looked at that page and I can't find any information about my problem. But thank you anyway :)

"This goes very well. Just make sure that you select safe graphics mode at the startup screen.."

When I try this my install screen freezes just like it does for him in normal graphics mode.

I just tried to check the cd for defects, and I get the same (or similiar error). Could there be a problem with my dvd?

---

### Post by Pumalite on 2008-04-23
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less, check CD integrity after burn and before install. Do not use CD-RW

---

### Post by ricketick on 2008-04-23
I just tried my server cd, which I've used a couple of times on my server, and it didn't work either. Well, I might as well burn a new cd anyway, got nothing to lose, well except for a blank cd :P

---

### Post by Pumalite on 2008-04-23
Clean the lens in your burner, try your CD's in a different computer.

---

### Post by tommcd on 2008-04-23
You could also try:
"acpi=force pci=noacpi" as a boot option, or just acpi=force. IF all else fails, you can try "acpi=off", to at least get it installed. Some things, like the battery monitor, may not work with acpi=off though. I have had similar problems with IRQ errors trying to get Zenwalk 5 on my Acer 3680 laptop, and acpi=off is the only thing that worked.
After it installed I did not need acpi=off to boot, but the boot process hangs for about a minute or so while booting up. I'm still working on that one.

---

### Post by ricketick on 2008-04-23
:oops: I think I found the problem.. After realising that my server is i386 and that disc shouldn't work on acer since it's amd? I checked my desktop cd and it was also i386! I'm downloading amd at the moment, and I'll let you know if it works!

Hm, or wait is that only amd 64? yea, sempron isn't 64..

---

### Post by ricketick on 2008-04-23
> **tommcd said:**
> You could also try:
"acpi=force pci=noacpi" as a boot option, or just acpi=force. IF all else fails, you can try "acpi=off", to at least get it installed. Some things, like the battery monitor, may not work with acpi=off though. I have had similar problems with IRQ errors trying to get Zenwalk 5 on my Acer 3680 laptop, and acpi=off is the only thing that worked.
After it installed I did not need acpi=off to boot, but the boot process hangs for about a minute or so while booting up. I'm still working on that one.

Just tried it and I got the same four errors as before, plus a new error: failed to allocate shard interrupt 0

---

### Post by ricketick on 2008-04-23
I just found an ond fesity fawn server edition lying around and it gave me some errors as well but it seems to be working, it didn't give me the black screen of death at least :)

---

