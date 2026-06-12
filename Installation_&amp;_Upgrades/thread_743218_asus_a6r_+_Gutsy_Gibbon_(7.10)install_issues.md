---
title: "asus a6r + Gutsy Gibbon (7.10)install issues"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by int80 on 2008-04-02
I've been trying to install this now for about 3 days on my Asus a6r, and it's killing me. I've managed to install it, but I can only boot in recovery mode. If I add acpi=off at startup, it gets to a section that says hpet0 timer etc etc, and hangs. So I tried to put hpet=disabled or hpet=off into the startup line, but it still just shows some text then the screen goes black.

I've searched these forums for ages, but there seems to be bits and pieces, but nothing concrete (that I can find)..

Has anyone got any ideas?

---

### Post by int80 on 2008-04-02
that's weird, it seems to work now. I left the room and it had booted up. I used hpet=disabled acpi=off on the startup line and it's ok... :)

---

### Post by blazercist on 2008-04-02
hmm it boots in recovery mode and operates properly?

perhaps its something similar to what happened to me on my old MSI-1039,  it took me forever but in the end i discovered that it was a conflict between network-manager and my wireless driver.

do lspci in console and post the output

---

