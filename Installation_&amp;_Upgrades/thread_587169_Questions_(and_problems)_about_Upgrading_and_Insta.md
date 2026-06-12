---
title: "Questions (and problems) about Upgrading and Installation."
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by DoomCypher on 2007-10-22
Hello everyone,

I've decided to install Ubuntu on a machine at work to make an FTP server for backups. (took me quite a time to install this monster)

I've tried to install Gutsy AMD64, but it failed to past the CD boot screen. (reads the CD for a while and it just goes idle, with a blank screen) So I took out my old Dapper CD (x86) and it worked, but I had to disable the extra HDDs to do so, because grub didn't liked the RAID.

So, here are a few questions: Is there any memory limitation for Ubuntu x86? or it is vital that I change to Ubuntu to x64? (I know Windows XP x86 can't handle more than 4GB of memory) Can I upgrade Dapper x86 to Gutsy x64? How can I configure my nVidia RAID and what I need to make it appear in Ubuntu? Is there any good grub config tool (GUI would be nice :) ) that doesn't needs a PhD in computer science?

Thanks for your patience reading this, and thanks for your reply in advance. :)

---

### Post by mikewhatever on 2007-10-22
> **DoomCypher said:**
> 

So, here are a few questions: Is there any memory limitation for Ubuntu x86? or it is vital that I change to Ubuntu to x64? (I know Windows XP x86 can't handle more than 4GB of memory) 

That does not depend on the operating system, but on the CPU architecture. Any 32 bits CPUs will cant access more then 4 GB of RAM, and not every AMD is a 64 bits capable. You may want to check which one you have. Perhaps that was the problem with Gutsy 64.

> Can I upgrade Dapper x86 to Gutsy x64?

No.

> Is there any good grub config tool (GUI would be nice :) ) that doesn't needs a PhD in computer science?

Grub does not need a phd to configure. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by DoomCypher on 2007-10-23
Well, I used the alternate CD install, and I keep running on the same idle screen after GRUB. (no HDD activity, no graphics, just a blank black screen.)

I used the recovery mode and I entered correctly. 

No idea what could be going wrong. 

Oh, and the installer recognizes systems without Long mode and halts before installing. (displays a nice message saying that your system doesn't supports long mode.)

---

