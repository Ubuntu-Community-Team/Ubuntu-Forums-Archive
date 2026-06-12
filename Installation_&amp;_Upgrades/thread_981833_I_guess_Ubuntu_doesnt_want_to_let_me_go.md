---
title: "I guess Ubuntu doesnt want to let me go"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by steve789 on 2008-11-14
I want to install WinXP i search in the forums and all i found was virtual boxes and all of those emulators but the thing is that I need a real Windows not alternatives I really have some apps that i need for work that are not avalible on Ubuntu and no is not Ms Word.... Sooo I created a partition using the Ubuntu live cd then left it "unlocated" i tried booting from my WinXp cd and I get and error saying something like "no hard drive detected please make sure your hard drive is power on blah blah blah" so I formated the partition with Fat32 still samething then fat16 and I kept getting the same error so I finally decided to back up all my data and delete all partitions from ubuntu and leave it unlocated I try the winxp cd same error then formated with fat32 then 16 and nothing it seem like the hard drive was dead so I had no option but to re-Install Ubuntu and now Im writing this and like 5mins ago Ubuntu finish updating it self wow I guess im stuck with ubuntu unless someone is willing to help I dont i want to buy a dell inspiron hdd they are not cheap.

for some reason when I was installing ubuntu it said that 120gbs wasnt enough but since I didnt care about Vista at the time I just decided to use the full hard drive(160gbs)

---

### Post by cb951303 on 2008-11-14
> **steve789 said:**
> I want to install WinXP i search in the forums and all i found was virtual boxes and all of those emulators but the thing is that I need a real Windows not alternatives I really have some apps that i need for work that are not avalible on Ubuntu and no is not Ms Word.... Sooo I created a partition using the Ubuntu live cd then left it "unlocated" i tried booting from my WinXp cd and I get and error saying something like "no hard drive detected please make sure your hard drive is power on blah blah blah" so I formated the partition with Fat32 still samething then fat16 and I kept getting the same error so I finally decided to back up all my data and delete all partitions from ubuntu and leave it unlocated I try the winxp cd same error then formated with fat32 then 16 and nothing it seem like the hard drive was dead so I had no option but to re-Install Ubuntu and now Im writing this and like 5mins ago Ubuntu finish updating it self wow I guess im stuck with ubuntu unless someone is willing to help I dont i want to buy a dell inspiron hdd they are not cheap.

for some reason when I was installing ubuntu it said that 120gbs wasnt enough but since I didnt care about Vista at the time I just decided to use the full hard drive(160gbs)

surely there is something wrong with you hdd. and you don't have to buy a hdd from dell. they don't make hdds anyway. just go to newegg.com and find a good cheap hdd ...

---

### Post by steve789 on 2008-11-14
Im using the same hdd on ubuntu I just dont see how I can get it to work on WinXp

---

### Post by cb951303 on 2008-11-14
> **steve789 said:**
> Im using the same hdd on ubuntu I just dont see how I can get it to work on WinXp

oh I see, sorry I misundersttod. It might be a incompatibility thing. I had a fujitsu laptop which only worked with Vista but didn't work with xp because of a similar hdd problem. But I'm pretty sure there were workarounds for this. One thing I remember is that there are lots of pirated xp isos out there that are bundled with the correct SATA drivers to address your issue.

---

### Post by steve789 on 2008-11-14
oh yeah drivers almost forgot hahaha....now i have to look for Drivers for a hard drive wow thats funny that almost never happens, well thanks for all your help Ill try installing vista as soon as i  get a copy

---

### Post by Xanerrix on 2008-11-14
Yeah I had a similar issue earlier. It has to do with the HDD controller in your Mobo. You can change the setting to IDE instead of SATA in your bios if you have access.
Ubuntu might not work in IDE mode though it didn't for me.
WinXp never included the drivers for SATA, I think, in an attempt to sell more vista copies.

Options are:
If you have a floppy drive, you can load SATA driver during installation.
Install Vista...
Or try to find a copy of XP with the driver already loaded.

In any case, don't look for HDD drivers it is your MOBO controller that is the issue.


P.S. Installing Windows after Linux is trickier than the opposite because of the Windows boot loader...

---

