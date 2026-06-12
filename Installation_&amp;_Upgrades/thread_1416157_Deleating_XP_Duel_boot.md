---
title: "Deleating XP Duel boot"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by glowell on 2010-02-25
Hi,
 
I installed Ubuntu inside the windows through Wubi and I selected the 30gb partition. Can I delete the Windows partition from my netbook through Ubuntu so I can go to a full hard drive and no longer have the windows xp on my netbook and just use the ubuntu as the primary os?

---

### Post by nuclearj on 2010-02-25
my uneducated guess would be no.  but then again I do not really know.  Good Luck!

---

### Post by JackRock on 2010-02-25
No, as the Ubuntu is "hosted" by Windows. Since it's not on a true separate partition, a Wubi installation can't exist on its own, and thus is not a "Dual Boot".  It's closer to a virtual machine install, which demands an existing "outside" OS to operate.

It'd be wise to back up all important files/emails/etc on a separate drive, then re-format and re-install Ubuntu clean.

---

### Post by meierfra. on 2010-02-25
> Can I delete the Windows partition from my netbook through Ubuntu so I can go to a full hard drive and no longer have the windows xp on my netbook and just use the ubuntu as the primary os?
Yes, you can. I have done so myself.

If Wubi is installed on its own partition, it is completely independent from Windows and you can delete the Windows partition. But you should install Grub 2 to the MBR before deleting Windows, otherwise you will not able to boot in Wubi after deleting Windows.

In order to give you detailed instruction, follow this [link ]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

---

