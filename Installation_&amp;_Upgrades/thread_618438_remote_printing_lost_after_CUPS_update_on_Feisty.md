---
title: "remote printing lost after CUPS update on Feisty"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by DonLorenzo on 2007-11-20
After recent updates via update manager to CUPS on Feisty, a shared printer on one host didn't work anymore from another host.

This post
[http://ubuntuforums.org/showthread.php?t=590299&highlight=printing+ipp](http://ubuntuforums.org/showthread.php?t=590299&highlight=printing+ipp)
Though not an exact match to my environment gave me a clue.

In the CUPS update, it appears that the "share printers" global setting was overwritten by the update. Turning this setting back on fixed the problem.

**HowTo:**

On the host having the printer directly connected:
Using MainMenu -> System -> Administration -> Printing
... this opens the printers configuration dialog
click Global Settings
click Share Printers
... a check-mark should be on
close the dialog

It works for me.

---

