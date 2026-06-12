---
title: "i just downloaded ubuntu!!!???"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by 50cent1228 on 2007-05-06
like i said i just downloaded it and i tried to burn a bootable iso level 1 cd with cdburnerxp. after burning it i put the cd into my pc which all ready has windows xp on it but when ubuntu would start to boot or load it would just resart the pc...

did i burn the cd wrong????

if i did what do i need to do to fix it???

---

### Post by H.E. Pennypacker on 2007-05-06
You need to burn the file you downloaded as a CD image.  Do not burn the file directly.  

Follow these instructions:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by ticopelp on 2007-05-06
Assuming the ISO is burned correctly (see above post), I imagine you would may to change the boot sequence on your PC or go to the boot menu. You usually get to the boot menu by hitting a key during the boot sequence, most often F8, F12, sometimes DEL. It depends on the machine. Most computers will briefly display the options during boot.

---

### Post by 50cent1228 on 2007-05-06
no i had already set the boot sequence and everything was ready...i guess i just burned it wrong

---

### Post by 50cent1228 on 2007-05-06
ok i re burned it and it booted ...but when i checked for integrity it came up with this message:

Uncompressing Linux...Ok booting the kernel
MP-Bios bug: 8254 time not connected to IO-APIC
Kernel panic- not syncing: IO APIC timer doesn't work
boot with apoc-debug and send report
then try booting with the no apic option 

what should i do???

---

### Post by H.E. Pennypacker on 2007-05-06
> **50cent1228 said:**
> ok i re burned it and it booted ...but when i checked for integrity it came up with this message:

Uncompressing Linux...Ok booting the kernel
MP-Bios bug: 8254 time not connected to IO-APIC
Kernel panic- not syncing: IO APIC timer doesn't work
boot with apoc-debug and send report
then try booting with the no apic option 

what should i do???

That sounds to me like a bad burn.  Bad burns can cause strange error messages, and I have had my fair share.  I even had to stop using CD-RWs, and switched to CD-Rs to get a proper burn.  For others, CD-RWs may work just fine, but for me, at least the brand that I have, they didn't work.

Follow the guide in my earlier post to make sure you are doing everything correctly, and make sure you are using reliable CD-Rs.

---

### Post by 50cent1228 on 2007-05-06
nope i figured it out... i clicked  F6  and booted with noapic and it loaded...thnx but now i had another question.

now my second question is ...
i already have windows installed on my c drive now i want to have ubuntu on this machine as well now...in the partitioning software what do i do??? should i select manual option or not...sry im a noob...could u guide me through what i need to do to get a 30 gb space of ubuntu on my c drive without formating the whole drive..

basically i want the drive to have a partitioned space of 30 gb for ubuntu without reformatting or deleting my windows

---

### Post by ticopelp on 2007-05-06
If you want to install Ubuntu on the empty space, check the option that tells Ubuntu to use up the empty space, although I seriously, *seriously* recommend backing up everything on your Windows partition first, if you haven't done so already.

---

### Post by H.E. Pennypacker on 2007-05-06
Backing up is one thing, but knowing the right steps is yet another thing.  If you follow the correct procedure, you'll likely save time as well as not having to deal with many problems.  

That's why I am pointing you to the following guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Read it several times if you must, but whatever you do, make sure you understand that guide.  If you have questions about it, let us know, but read the guide carefully to make sure you know what you're doing.

The installation part is a breeze, but because of its potential risks, you need to be careful.

---

