---
title: "boot XP when installed on external HDD"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2008-09-05
Hi All,

Quick question that I can't see an answer to.

A friend of mine wanted to try Ubuntu without touching his laptop hard disk. He has an external hard disk (120Gb) which I suggested installing Linux onto. So, we did the following:
[LIST=1]
[*]Set the bios up to boot the USB HDD
[*]Devices: /dev/sda = internal HDD, /dev/sdb = external HDD
[*]I set Ubuntu up on /dev/sdb1 (/) and swap /dev/sdb2. I installed grub to /dev/sdb (the mbr of the external disk).
[*]Now, when we launch the system, IF the external HD is connected we get Grub, otherwise ntldr takes over and boots windows oblivious (the desired effect).
[/LIST]

The problem arises because my friend leaves his external HDD connected by default, so always gets grub. XP has turned up as an option, naturally, but we are struggling to boot it. The appropriate section of menu.lst is:
```
root (hd0,0)
savedefault
chainloader +1

```
Now, HD0 *appears* to be the correct boot device i.e. correct root, but on doing this I get "bad executable format" as a grub error. The only other option would be to chainload (hd1,0) which, surely, would chainload grub itself?

Does anyone see a way out of this issue? We have a working solution (leave the external disk unplugged for windows) so this isn't critical, but I'd like to understand what's going on!

Thanks

Quark_77

---

