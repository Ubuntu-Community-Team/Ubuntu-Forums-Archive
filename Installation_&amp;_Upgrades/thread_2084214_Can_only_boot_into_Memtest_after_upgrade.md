---
title: "Can only boot into Memtest after upgrade"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by paul0075 on 2012-11-14
Hi Guys,

I am running Lubuntu 12.10 and performed an upgrade this morning, and since it's rebooted, the only thing that loads is Memtest. I have no choice of what loads and can't exit from Memtest.

I am new at all of this, and haven't dealt with this before. Is there a keyboard shortcut I can use to bring up the bootloader? I have spent 40 minutes trying to find some info on what to do but am lost.

Thanks in advance

Paul

---

### Post by oldfred on 2012-11-14
May be best to see where everything is at. From Ubuntu liveCD you can add Boot_Repair or download a full repair ISO.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by paul0075 on 2012-11-14
Thanks Oldfred, doing the Boot Repair now. I finally found that I needed to hold the Shift key to show Grub, and it now only has entries for MemTest and nothing else.

Once the Boot Repair is done I will post the results.

---

### Post by paul0075 on 2012-11-14
Problem has been solved. It would seem however I didn't copy the URL correctly for the report.

I can tell you that all I did was the automated repair. It has changed my Grub settings a bit, but works now. Where as before it never showed a menu, now it shows by default. Which I prefer anyway.

---

### Post by oldfred on 2012-11-14
Glad it worked. :)

Sometimes it is a bit more complicated and we need to review the report to see details, but if it works that is even better. And it often works.

---

