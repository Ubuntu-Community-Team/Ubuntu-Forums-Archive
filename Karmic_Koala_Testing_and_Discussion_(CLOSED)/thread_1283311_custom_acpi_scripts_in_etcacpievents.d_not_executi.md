---
title: "custom acpi scripts in /etc/acpi/events.d not executing in Karmic"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sanktnelson on 2009-10-05
Hi all,

I have custom acpi scripts which should be triggered when switching between latop and tablet mode on my thinkpad x61. I already had some wirdness with them in Jaunty where I had to restart ACPID once after booting for those scripts to be executed properly. Now after the upgrade to Karmic they don't execute at all.

I read somewhere that the scripts in /etc/acpi/events.d don't get executed if something else is already listening to these events. How do I find out what else is listening, and how do I stop it?

Any help is greatly appreciated.

---

