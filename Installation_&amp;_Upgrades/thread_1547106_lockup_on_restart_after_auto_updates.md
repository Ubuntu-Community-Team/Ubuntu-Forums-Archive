---
title: "lockup on restart after auto updates"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by wonderin_y on 2010-08-06
I'm very new to unbuntu/linux.
Nearly every time that automatic updates finishes installing the software and requires a restart of the OS, the PC locks up at the 'Ubuntu' screen with some dots beneath it.
I have been just been forcing it down by powering off/on the PC - which I figure is probably not a safe thing to do but don't know what else to do or how to troubleshoot this problem.
Can someone help point me to some things I can do to resolve this problem?
I've looked at some of the log files but can't make any sense of most of them nor do I know which log file might show the problem.
TIA

---

### Post by lemming465 on 2010-08-07
In my experience lockups on restarts tend to be due to BIOS bugs.  See if there is a BIOS update for your motherboard.

---

### Post by presence1960 on 2010-08-07
The only time I know that requires a restart after updates is when updating your graphics card driver or the kernel. All other updates do not require a restart. Can you please elaborate.

---

### Post by wonderin_y on 2010-08-09
I don't remember the specifics of what types of updates were being applied when I've been prompted to reboot but they could have been kernel updates that required the reboot.
Not every update requires me to reboot but when it does, it locks up when attempting to do so which has happened maybe 3-4 times in just the 2-3 weeks I've been running ubuntu.

---

### Post by lemming465 on 2010-08-09
How far does it get on the shutdown / restart before it locks up?  If it locks up partway through the shutdown process it's probably due to video driver bugs with your video chip.  If it locks up after the ubuntu kernel finishes shutting down and can't reboot without being powercycled, then it's probaby BIOS bugs.

---

### Post by mwildam on 2010-08-10
I have experienced some box where a restart had problems too (even if effect was slightly different from yours). What, if you say "Restart Later" instead and then do a shutdown instead? Does it boot then when you turn it on again?

---

### Post by wonderin_y on 2010-08-13
I recently had an update that required a reboot again and this time I selected to reboot later. I then tried to do a restart and it again locked up.
It gets to about the 3rd dot under the "Ubuntu" screen during the reboot process so I don't know at what point it got to.
I'm going to try updating the bios and check on the video driver.

---

