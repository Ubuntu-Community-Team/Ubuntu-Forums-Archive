---
title: "How do I get SMP for 7.10 Desktop?"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by Cr0n_J0b on 2007-11-24
So I'm installing 7.10 desktop on a new system and I would like to take advantage of the dual cores.  I just got an AMD BE-2300 which I believe is an X2 processor with 2 cores.  I installed 7.10 Desktop from the 32-bit version, but does that automagically put the SMP in there or do I need to do something extra?  

thanks

---

### Post by Phurious on 2007-11-24
You can check and see if both processors were detected.  An easy way is to launch System Monitor (System > Administration > System Monitor) and check the "Resources" tab.  The CPU History graph should display 2 separate line, one for each CPU.

---

### Post by Pumalite on 2007-11-24
The installer automatically installs SMP if that is what you have.

---

### Post by Cr0n_J0b on 2007-11-24
Cool, thanks that's what I was guessing, but  wanted to make sure.  I noticed references to 2 CPUs in the logs, but I wasn't sure.

---

### Post by Pumalite on 2007-11-24
You are welcome. Good luck.

---

### Post by arutkin on 2007-11-25
Any suggestions on what to do if Ubuntu 7.10 does not recognize multiple processors automatically?

---

