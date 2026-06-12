---
title: "Ubuntu on ASUS P2B-S - Am I out of luck?"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-09-06
I am trying to install Ubuntu 6.0.6 LTS on a PII 400MHz 512MB PC having an ASUS P2B-S motherboard. It is still running Windows 2000 wonderfully. However, I would like to get rid of Windows on that machine and put Ubuntu.

But the Ubuntu CD refuses to even start at the most basic mode, claiming that there is an ACPI issue ("PCI routing").

I researched the web a little and sure enough, this ASUS P2B-S is on the [Linux ACPI black list]("http://www.columbia.edu/~ariel/acpi/acpi_howto.html#bioses_supported").   :(

Is this the end of the road?](*,) 

Am I doomed for posterity to use Windows on that machine?

Is there any trick I can do to run Ubuntu on that one? (I don't mind about not having ACPI).

Thanks!
Alex

---

### Post by xp_newbie on 2006-09-06
No. I am not out of luck. :) 

Through some research and persistence I managed to successfully boot Ubuntu 6.0.6 LTS CD and now it is in the process of installing into disk. :-D 

How I did that?

Simple. At the first screen, I pressed F6 and entered the following boot parameters:

> ide=nodma apm=off acpi=off noapic nolapic noacpiDon't ask me why and/or how it works. It just works.

Thank you SUSE and KNOPPIX! :)

---

