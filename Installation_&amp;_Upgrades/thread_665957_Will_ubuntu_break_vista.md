---
title: "Will ubuntu break vista?"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by syno8 on 2008-01-12
Hi i just got an acer aspire 5520-5919 laptop. i want to install ubuntu on it and duel boot with vista. the only thing that is stopping me is can anything go so wrong that i can never get vista back with out purchasing a new copy. i have the recovery cd but thats it. i dont mind if i had to lose everything i had saved on the laptop to get vista back. i just have read that some times its not even possible with the recovery cds you get with the computer.

any one know?

thanks in advance

---

### Post by Pumalite on 2008-01-12
Wrong. Backup everything because is the thing to do before the installation of a new OS. Use Vista partitioner to allocate space for Ubuntu, then install Ubuntu and let Grub install to MBR (by default) and you'll have dual boot.

---

### Post by erfahren on 2008-01-12
actually setting up the partitions on Acers isn't hard - there should already be a "Data" (Windows "D:") partition set up from the factory - you can resize it from within Vista

it is a good idea to leave some of it (20GBs or so at the least) because the Acer eRecovery backs up to it and there is a "monitor.exe" service from eRecovery that checks for the the backup (Data) partition at Vista's boot. - so that either needs to be disabled or just leave 20GB of that partition for Windows

Once that partition is resized and you created space for Ubuntu just use the "Manual partitioning" option when installing from the LiveCD to create the partitions needed for Ubuntu out of that space [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by MobiusNZ on 2008-01-12
I've got Ubuntu dual-booted with Vista on my Laptop. You can do all your partition resizing from within the Ubuntu setup.

---

### Post by erfahren on 2008-01-12
> **MobiusNZ said:**
> I've got Ubuntu dual-booted with Vista on my Laptop. You can do all your partition resizing from within the Ubuntu setup.
did you use manual or "guided" - it was my understanding that the LiveCD didn't support resizing of Vista partitions 

from: [http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)
> 
Dual-Boot Windows Vista and Linux 
After the installation of Windows Vista, you will want to install Linux. DO NOT resize the Vista partition during the installation of the Linux distribution! Due to the change in NTFS versions, no Linux partitioning program, nor standard Windows partitioning programs, can properly alter the partition that Vista is installed to.


---

### Post by MobiusNZ on 2008-01-13
I guess that howto must be out of date. It does mention "public beta release of windows vista"...

Then again, it has been a while since I set up the laptop - I may have prepped the hdd in windows... but I certainly didn't have to muck with the grub config as the howto directs you to - it picked up my Vista partition as a boot option and my recovery partition too.

At the end of the day, now that microsoft *finally* include tools for working with it's native partition format, you're always safest working with them. (Just like you use a linux program to resize ext3 partitions rather than a windows program)

---

### Post by Nero_Flint on 2008-01-13
>  Will ubuntu break vista?

Hopefully.

---

### Post by azraelck on 2008-01-13
I doubt it's possible for Ubuntu to break Vista any more than it's already broken.

Seriously, my brother installed 7.10 without a hitch, and the only issues with vista are the same ones he's already been having long before he installed Ubuntu. 

He did not use the Vista tools to do anything. Everything was done when he installed Ubuntu.

---

### Post by nowhere@cox.net on 2008-01-23
FYI I jumped right in and installed Gutsy on my Vista encumbered Thinkpad T61. I let Ubuntu live CD (safe graphics mode) install handle the partitioning using the guided resize, selected how much I wanted the Vista to be left with and let er rip.

Result? Booted to Ubuntu just fine. Rebooted to Vista, got the disk check which rebooted Vista again, got a installing new driver for hard drive which rebooted Vista again and Voila! Dual Boot Thinkpad on Gutsy and Vista. Grub even set up a menu item for the recovery partition. 

NOW I do get a message from fdisk -l about partitions not ending on a cylinder boundary but I will start a new thread on that...

Cheers!

---

