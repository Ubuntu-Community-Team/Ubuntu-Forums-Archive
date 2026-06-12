---
title: "Dual Boot Issue"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by alfamuzjak on 2011-11-01
Hi guys, i have dual boot with windows 7 and Ubuntu 11.04.
I have some bugs on windows + 1 have 1Gb of ram...so i want to remove and change from windows 7 to xp (sp2 or sp3...doesnt matter).
Can you tell me how to accomplish that (remove only windows 7, install xp but to have dual boot with my ubuntu)?

Thank you.

---

### Post by ashickur.noor on 2011-11-01
It's is easy, just install windows xp on that drive where windows 7 is install. Then Restore grub. There will be one problem, windows will not let you install xp when windows 7 is installed. You can just delete the drive of windows 7 from Ubuntu and update grub.
To restore grub of Ubuntu 11.04 see [here]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")

---

### Post by Hedgehog1 on 2011-11-01
The partition arrangement between  Windows 7 and XP is different, Windows 7 uses a little 100 meg boot partition, while XP does not.

Going backwards to XP from Windows 7 can be tricky.

Might I suggest:

1) Saving your data from the Windows and Ubuntu partitions
2) Do a clean install of XP using one partition
3) Then re-install Ubuntu side-by-side with XP.

This will have the least issues and problems for you.

***The Hedge***

:KS

---

### Post by alfamuzjak on 2011-11-01
Thanks for suggestions...Tell me 1 thing...if i insert win xp, start installation and format both my partitions, install xp on c:..i wont have problems with grub,boot loader etc?
And then when installation is complete i can install fresh ubuntu and have dual boot?

---

### Post by ashickur.noor on 2011-11-01
> **alfamuzjak said:**
> Thanks for suggestions...Tell me 1 thing...if i insert win xp, start installation and format both my partitions, install xp on c:..i wont have problems with grub,boot loader etc?
And then when installation is complete i can install fresh ubuntu and have dual boot?
You don't need to install Ubuntu again. After installing Windows just restore the grub using live cd. Then you can use both of them via dual boot.

---

### Post by alfamuzjak on 2011-11-01
Are you sure that after formating both partitions, ubuntu will be still available?

---

### Post by ashickur.noor on 2011-11-01
> **alfamuzjak said:**
> Are you sure that after formating both partitions, ubuntu will be still available?
Why you want to delete the Ubuntu partition? If you delete the Ubuntu partition then Ubuntu definitely will be gone.

---

### Post by Mark Phelps on 2011-11-01
By "both" partitions, he means both the 100MB partition and Win7 OS partition -- not the Ubuntu partition.

Just boot into Ubuntu, use the Disk Utility to remove those two partitions.

Then, boot from the XP CD and select the unformatted space.  XP will then format that space and install itself.

Then, you'll need to reboot from the Ubuntu CD and reinstall GRUB.

---

