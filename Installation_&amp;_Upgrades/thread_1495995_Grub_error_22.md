---
title: "Grub error 22"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by jparthen on 2010-05-28
Hello, 
I would firstly like to say that I'm pretty new to these forums.
I have a VAIO laptop with dual boot capability (XP+Ubuntu). I decided to reformat the hard disk after some misuse using the built-in restoration utility (dedicated hard disk partition). Therefore everything in my hard disk has been erased including the UBUNTU OS.
I tried to recover the system using either a live CD or an XP installation CD. The result was disappointing. Boot from the live CD was unsuccessful always giving 
GRUB loading, please wait....
error 22
and thus bypassing the CD!!!

Boot from XP CD was again unsuccessful due to undetected hard disk (an appropriate  message described the problem).

Can you please advise what to do????
Thanks very much in advance.

---

### Post by darkod on 2010-05-28
Are you sure you were booting from the live cd? That doesn't load grub at all.

I think the message was because the computer tried to boot from the hdd and the partitions are gone as you said.

Go into BIOS and make sure cd-rom is before hdd in boot devices.

---

