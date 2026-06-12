---
title: "Kernel Fails to Uncompress"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Turkey Pwner on 2007-10-25
Hello.  I installed Xubuntu 7.10 full release onto my older computer system today.  Xubuntu installed without errors, but I receive the following message when I try to boot the installed Xubuntu from the hard disk (the last two messages are most important):

> Starting up...
[0.000000] ACPI: No DMI BIOS year, acpi=force required to use ACPI. // I didn't bother to copy this verbatum, as I receive the same error while booting from the LiveCD... which doesn't hender my booting the LiveCD... hence I am here.  See below
[64.341397] invalid compressed format (err=2) // Probably the pointer to the actual booting hendrence
[64.346042] Kernel panic - not syncing: VFS: Unable to mount root fs on uknown-block (0,0)
***Comments proceeding "//".***

**WHAT I KNOW:**
I know that the error regarding ACPI is not pointing to any booting hendrence, as I receive the same error while booting from the LiveCD, which brings me to the full desktop, giving me full functionality.

I know that the booting hendrence is regarding the inability to uncompress the Linux kernel...

The problem cannot be solved via "updating software", as I was connected to the Internet during installation, which allowed Xubuntu to update the system automatically.

**WHAT I DON'T KNOW:**
I don't know why the Kernel can't be uncompressed... when it can be using the LiveCD, which has the same Linux Kernel version as the installed Xubuntu has; nor how to fix the hard-disk-booting problem.

**RELEVANT SYSTEM SPECIFICATIONS:**
Memory: 250.0 MB
Processor: AMD-K6(tm) 3D Processor
Linux Kernel on Hard Disk: 2.6.22-14-generic
File System: ext3

I would greatly appreciate anyone's help.  I did a lot of searching regarding this problem using many methods (e.g. Google, popular Linux forums), but I did not find a solution that solved the problem for me.  Many were such as: "Install again, except use ext3 instead of the used reiserfs", or something...

I know that the community here is very polite, so, if the replier must call me by any name, call me by my first name, Aaron. :)

---

### Post by Turkey Pwner on 2007-10-26
I hope the Staff doesn't mind if I bump this thread...

... the problem posted is keeping me from using an installed Xubuntu at all, and the problem is fairly common, and I have as of yet to find a solution on the Internet outside of "Reinstall on a ext3 file system; ReiserFS isn't supported."

... I have it installed on ext3 already, after all. :P

Pre-thanks for help...

---

### Post by Mekkacola on 2007-10-26
Hi, 

Strange I have a similiar problem, but it appears allready when I try to install Ubuntu 
(Feisty (7.04 it is?)). 

"[422.xx] VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
[422.xx] Please append a correct "root=" boot option; here are the available partitions: 
[422.xx] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

I have a brand new PC to wich I was able to install a Window$ Vista business edition, (not without problems) 

Now when I tried to install a 64-bit version of feisty to another harddrive it freezes and gives this error. 
If I try to start install ubuntu normaly it gives me a black blank screen and turns my screen into standby

CPU: Intel Core2 Quad 
GPU: Realtek GeForce 8600 GT
MB: MSI P6N SLI platinium
2 gigs of 800 Mz DDRII
Various Harddrives of which none gives any better results

-Santeri 
Espoo, FIN

---

### Post by Turkey Pwner on 2007-10-26
> **Mekkacola said:**
> Hi, 

Strange I have a similiar problem, but it appears allready when I try to install Ubuntu 
(Feisty (7.04 it is?)). 

"[422.xx] VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
[422.xx] Please append a correct "root=" boot option; here are the available partitions: 
[422.xx] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

I have a brand new PC to wich I was able to install a Window$ Vista business edition, (not without problems) 

Now when I tried to install a 64-bit version of feisty to another harddrive it freezes and gives this error. 
If I try to start install ubuntu normaly it gives me a black blank screen and turns my screen into standby

CPU: Intel Core2 Quad 
GPU: Realtek GeForce 8600 GT
MB: MSI P6N SLI platinium
2 gigs of 800 Mz DDRII
Various Harddrives of which none gives any better results

-Santeri 
Espoo, FIN
Your GRUB configuration seems to have an incorrect "root=" boot option. :S  Go into /boot/grub, and find the partition on which Ubuntu is install, and correct Ubuntu's kernel option with the correct root in /boot/grub/menu.lst.

---

### Post by Turkey Pwner on 2007-10-27
I'm sorry, but I must bump this thread again...

Like I did with the gentleman before me, I can also answer most questions related to boot problems... except this extremely complicated one that continues to perplex me.

---

