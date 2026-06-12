---
title: "Sound card question"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by n8qxb on 2005-06-22
I was thinking about installing Ubuntu on my second drive. Does anyone know if Ubuntu supports the Turtle Beach Santa Cruz PCI sound card. Thank you in advance!

Tom

---

### Post by intangible on 2005-06-22
It does AFAIK, but here's a note I found about it:

[i]
NOTE: as of ALSA 1.0.8, you MUST enable the "External Amplifier" in the mixer, or you will end up with no sound. This was apparently only implemented in this version, though the mixer channel has been there since before 1.0. Since it defaults to "Off", upgrading from an older vesion to 1.0.8 (or to the 2.6.11 kernel) will leave you with no sound unless you "unmute" (turn "On") this switch.[/i]

---

