---
title: "ubuntu won't install"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by wasmiddel on 2013-02-08
hello,

im trying to install ubuntu 12.10 via wubi on my hp envy 6-1012ed, core i5, ati radeon hd 7670m. every time it reboots in ubuntu and after i click install inside windows my system will reboot into windows and do nothing. i also tried installing in by partitioning my hard drive but that doesnt work either. any tips?

---

### Post by type4corp on 2013-02-08
To be Honest I have never used Wubi so that whole process is knew to me and strange But one thing i would look for is where your putting the linux partitions 
and what's your boot entry look like cause grub should be listing both linux first then Windows

---

### Post by bcbc on 2013-02-10
Is it because you already have 4 primary partitions? That's fairly common on HP computers. It's not entirely clear what you're doing so maybe add some more words.

---

### Post by wasmiddel on 2013-02-10
i deleted one of the 4 primary partitions. so i now have 3, that shouldn't be a problem right?

---

### Post by darkod on 2013-02-10
For installing inside windows you don't need to delete or create any partitions. It installs like a virtual machine on existing ntfs partitions.

What could happen is often in win7 you have to launch the wubi.exe with right-click, Run As Administrator so it has higher permissions. The UAC might block some things.

In any case, I would consider installing a proper ubuntu, not wubi inside windows.

---

### Post by cybrsaylr on 2013-02-10
> **wasmiddel said:**
> i deleted one of the 4 primary partitions. so i now have 3, that shouldn't be a problem right?

Correct it should install now.
I had the same problem awhile back, had 4 partitions and couldn't install Ubuntu. I eliminated an unneeded partition and Ubuntu installed with no problem. 

FWIW I never liked WUBI because if something goes haywire with Windows you will also lose Ubuntu since it then runs inside of Windows. Just create a Linux partition and do a dual boot. Ubuntu will run fine on as little as 10GBs if you are pressed for space and you will have two independent OSs.

---

### Post by bcbc on 2013-02-10
> **wasmiddel said:**
> i deleted one of the 4 primary partitions. so i now have 3, that shouldn't be a problem right?

That should be fine. You can either shrink the main partition (C: ) from Windows, or let the Ubuntu installer do it. (I'm guessing that the partition you deleted won't be big enough for Ubuntu). 

So if there's still a problem, post back on what happens.

PS I assume you're not installing Wubi as you mentioned you first tried to do a normal dual boot. If that's not correct, you should mention that (because not everyone is reading it that way).

---

