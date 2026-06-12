---
title: "I Need All 4 Primary Partitions"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by jb2005 on 2009-11-21
Hello coders,

I'm a rock bottom beginner to any kind of Linux but I read a lot about Ubuntu and I successfully installed Ubuntu 9.10 on a Windows 7 machine during my 3nd try, but I had to wipe the entire disk twice, re-installing Windows-7 on the first Primary again on the 3rd try.  The Live-CD is so cool. .. but we are only allowed 4 Primary Partitions on a single Hard-Drive and this is what I had to do:

[FONT="Courier New"][SIZE="3"][B][COLOR="Blue"][SIZE="2"]Primary Partition 1 = Windows 7
Primary Partition 2 = Extended partition for Windows
Primary Partition 3 = Ubuntu 9.10
Primary Partition 4 = Ubuntu Swap [/SIZE]
[/COLOR][/B][/SIZE][/FONT]
I am very disappointed because when you make a Extended partition (for Windows), it actually eats up one of your primary partitions (the 2nd one in my case).

Now I learn when I installed Ubuntu 9.10 on my 3rd Primary Partition it ask me to make a SWAP and the only way I could see to do it was to use the last Primary Partition.

I need the last Primary Partition (the 4th primary partition) for an OpenBSD install.  I have three questions.

My first question is:
1) How do I install Ubuntu 9.10 and manually build-in root and the other directories, including the swap, inside the 3rd Primary Partition only?

Ubuntu 9.10 Grub-2 worked perfect for booting Windows 7 and Ubuntu 9.10 so to add to this question, (provided the 4th Primary Partition can be free-up) my final question is:

2) How do I add OpenBSD to GRUB-2 or how do I install a BSD to the last partition with Ubuntu 9.10 being in control of it all? ... (Grub-boot wise I guest).

I think explained fairly well of what I am trying to do.  Hope someone can help or point me to a thread of details that do exactly what I am after.  I'll save the 3rd question for next.

Thanks

MY Dream Machine:
[FONT="Courier New"][FONT="Courier New"][SIZE="4"][SIZE="3"][B][COLOR="RoyalBlue"][SIZE="1"]Primary Partition 1 = Windows 7
Primary Partition 2 = Extended for Windows only
Primary Partition 3 = Ubuntu 9.10 including Swap
Primary Partition 4 = OpenBSD or any other BSD or OS[/SIZE][/COLOR][/B]
[/SIZE][/SIZE][/FONT][/FONT]

---

### Post by Mark Phelps on 2009-11-21
Actually, neither the Ubuntu partition nor the swap partition have to be primary.  They can both be logical partitions contained within an extended partition.

---

