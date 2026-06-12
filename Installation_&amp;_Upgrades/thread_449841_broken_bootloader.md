---
title: "broken bootloader?"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Pai on 2007-05-20
**Edit2: This problem has been solved. The solution is posted below, in case anybody is interested**

Today I recently reformated my drive in favor of a dual boot system (featuring Feisty and XP).

Feisty is up and running just fine, however, I can't boot to XP. When I try, I receive a message saying: 

[I]Winnt_root\System32\Hal.dll missing or corrupt:

Please re-install a copy of the above file.[/I]

I found this problem in MSFT's support database, which says that the cause may be one of the following:
> This behavior can occur if any or some of the following conditions are true: 
&#8226;	The Default value in the [Boot Loader] section of the Boot.ini file is missing or invalid.
&#8226;	**Windows XP is not installed in the location specified in the Boot.ini file.**
&#8226;	The Ntoskrnl.exe file is missing or damaged.
&#8226;	**The partition path in the Boot.ini file is not set correctly.**
&#8226;	General hardware failure.

I feel like this problem wouldn't be too hard to solve using the Bootcfg utility on my XP cd, but I'm worried that I will in turn screw up GRUB.

edit: after doing a little more research, it seems that the cause of the problem is the boot.ini file simply does not point to the correct partition for windows. How could I edit the boot.ini file to point to the correct partition?

**What should I do to fix my XP install without ruining my GRUB setup?**

The following algorithm was used to solve this problem:
[I]1.	Use the Windows XP CD-ROM to start your computer.
2.	When you receive the message to press R to repair Windows by using the Recovery Console, press the R key.
3.	Select the Windows installation that you want, and then type the administrator password when prompted.
4.	Type bootcfg /rebuild, and then press ENTER.
5.	When the Windows installation is located, the following instructions are displayed:
Add installation to boot list? (Yes/No/All)
[Type Y in response to this message.]

Enter Load Identifier:
[This is the name of the operating system. Type Windows XP Professional or Windows XP Home Edition.]

Enter OS Load options:
[Leave this field blank, and then press ENTER]. 
After you perform the preceding steps, restart the computer, and then select the first item on the boot menu. This should allow Windows XP to start normally.

After Windows XP has successfully loaded, the Boot.ini can be modified to remove the incorrect entry.[/I]


Thanks in advance.

---

