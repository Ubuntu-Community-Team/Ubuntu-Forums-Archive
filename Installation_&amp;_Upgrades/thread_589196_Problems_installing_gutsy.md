---
title: "Problems installing gutsy"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by inversekinetix on 2007-10-24
Hi I'm trying to get gutsy installed on my system with many problems.  Could anyone please help in simple language.

I know nothing about linux, but know a little about pc's.

In my bios.

HD1 500GB IDE  100/400 partitions   xp/data ide (0,0) (win  C:/D: )
HD2 80GB   IDE data (0,1) unformatted
HD3 500GB SATA   data  (sata 1) (win E: )
HD4 500GB SATA   data (sata 2) (win F: )

DVD  (sata 3)  (win G: )


boot sequence is  USB >> Optical >>>first HD

I have tried several times to install gutsy on unformatted HD2

when the partitioner starts  it always puts the drives in random order in the list and assigns them sda sdb sdc sdd.  I am i right in thinking that  S in sdc means SATA?  i thought it should show  Hd for ide drives, I am probably completely wrong, but I'm just learning.

Anyway,  I choose the 80GB HD for the installation, give it 75GB as ext-3  for /  and 2GB as swap,  I go through all the install, it says its scanning for other OSs and is installing grub,  I whip out the disk reboot and it goes straight to windows.  I've tried reinstalling a few times, at the end of the install setup dialog there is an `advanced` button that allows you to choose which HD to install the bootloader to,  that is set to HD0 as standard,  I have tried changing that and it I still end up with no grub, just straight to windows.

I'd be grateful for any help, I want to get using ubuntu, but need to get it installed first.

Thanks

Inverse

---

### Post by confused57 on 2007-10-24
Since Feisty, all hard drives are recognized as SATA(sdx), regardless of whether they're IDE or SATA.

It's possible that grub is recognizing your 80 Gb IDE as (hd0) & is installing grub's IPL to this drive's mbr...you could try setting your bios to boot first to your 80 Gb drive to determine this.

Another possiblity you might want to consider is using WinGrub to boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

---

### Post by inversekinetix on 2007-10-24
Thanks 57, I'll try it when i get home.

---

### Post by inversekinetix on 2007-10-24
big thanks, I went with wingrub,  got me to the broken grub, manged to get into my ubuntu install and fix the menu.lst.  Learnt loads in the process.

Thanks!

if you could tell me how to install XMESS with a frontend GUI i woulk love you forever :)

---

