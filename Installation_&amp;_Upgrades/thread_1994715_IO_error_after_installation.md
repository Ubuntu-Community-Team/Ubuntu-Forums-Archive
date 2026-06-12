---
title: "I/O error after installation"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by girffe on 2012-06-03
Yesterday I bought a used Thinkpad T61 (processor T7100, 2GB RAM), which worked with windows XP installed. I also bought a OCZ Agility 3 120GB SSD to replace the original hard drive with. I went to install ubuntu, the laptop runs fine from the disk itself, and the installation seems to go smoothly. However, when the laptop restarts itself to boot off of the disk, it gives me the error:

[ 1944.149664] end_request: I/O error, dev sr0, sector 52xxxx

It spams this message several (30?) times, with increasing values for xxxx. When I try to boot off the hard drive, it just gives me a black screen. Of course, this sounds like a hard drive error, but weirdly, when I run disk utility on the hard drive, it comes back perfectly fine. Even more weirdly, sometimes when I try to boot from a disk (when there's no disk in the laptop), it will wait a couple of minutes, then boot off of the hard drive with no issues. The best guess I can make is that only some of the hard drive sectors are faulty, and the missing files cause it to behave unreliably? Are there any tests I can run that would confirm that the hard drive is faulty so I can just take it back to the store and claim warranty?

tl;dr: After installation, Ubuntu says the hard drive has bad sectors, hard drive only boots sometimes, Disk Utility says it's fine.

---

### Post by girffe on 2012-06-03
I just ran badblocks on blocks 52000-53000 and there were no errors found

---

### Post by girffe on 2012-06-04
Found the problem. For anyone who has this issue, 10.04 doesn't support SSDs, make sure the version you're trying supports SSDs if you're trying to install on one. Also, beware of OCZ Agility (probably OCZ in general). It didn't work with 12.04 either, so I decided to go on the exact opposite side of the reliability scale and buy an Intel SSD, works like a charm now

---

