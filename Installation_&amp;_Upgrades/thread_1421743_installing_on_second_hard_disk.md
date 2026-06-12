---
title: "installing on second hard disk"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by notwatson on 2010-03-04
At the moment I have one HDD (on a single plug IDE cable) and two DVD drives on the other IDE channel (both on one cable [slave/master]). 

The HDD is set to master and contains PCLINUXOS.

I have got another hard disk and a twin plug IDE cable.

So, I want to replace the single IDE cable with the double - install the new hard disk and install Ubuntu on the new hard disk. This, I plan to be a temporary measure, as I want to check that my Thunderbird 2 and Firefox profiles work with Thunderbird 3 and Firefox in Ubuntu. Once I have established this to be the case and had a play for a few days, I'll simply install Ubuntu to the present master (which is larger anyway).

So - here's my question...

If I leave the present master disk as master, set the new hard disk to slave and boot up from the Ubuntu live CD, can I install Ubuntu onto this new hard disk without touching the other hard disk - or will I need to change the master/slave settings around ? (at the moment, the master has two partitions, system and swap). If there is something else I should do, please let me know...

Could somebody advise me on the best way forward please ?

I know this seems like a lot of hand-holding, but I just really want to make sure....

Thanks in advance for any help.

Jon

---

### Post by mikewhatever on 2010-03-04
You shouldn't have any problems. Once thing to be aware of is that by default, Ubuntu installs GRUB to the MBR of the first hdd. There is a button, 'Advanced' to change that just before the copying of files begins.
Anyway, good luck with that.

---

