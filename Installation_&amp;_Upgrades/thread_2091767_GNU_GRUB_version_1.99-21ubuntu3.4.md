---
title: "GNU GRUB version 1.99-21ubuntu3.4"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by imonkey01 on 2012-12-06
HI
Im new to ubuntu and i downloaded it and installed it through windows and im running it alongside windows 7. it was good until i tried to change from windows 7 to ubuntu by restarting my computer and then i received the following message

GNU GRUB version 1.99-21ubuntu3.4

Minimal BASH-like line editing is supported for the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions grub>

ive been trying to search for a solution but nothing ive read sounds familiar. mostly i hear about a liveCD or liveUSB but since i downloaded and installed ubuntu off the internet i dont have either. can anybody help?

thanks in advance

---

### Post by Darris on 2012-12-06
Same thing just happened to me 
Was it working for you before?

---

### Post by darkod on 2012-12-06
It would be much better if you can burn the ubuntu live cd from the iso. That way you can boot it into live mode (running from the cd) and take a look what is going on, run some commands. For example, it would help if you open terminal and post the output of:
sudo parted -l (small L)

It looks to me like you have installed wubi inside windows (which is not running along side win7) and grub2 got installed on the MBR of the disk by mistake.

Or, if you are sure you installed a dual boot along side win7, then sometimes grub2 can't reach its config files to load them, and it gives the rescue prompt. This usually happens on older boards if they can't use boot files beyond 137GB on the disk, and disks these days are much bigger than 137GB. If the grub config files end up towards the end of the disk, and your BIOS has the 137GB limitation, then grub2 can't reach the config files.

---

