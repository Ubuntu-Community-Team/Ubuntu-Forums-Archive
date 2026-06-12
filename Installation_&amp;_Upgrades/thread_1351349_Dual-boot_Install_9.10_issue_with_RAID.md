---
title: "Dual-boot Install 9.10 issue with RAID"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by jlloyd_ndpdd on 2009-12-10
Hi guys,

The backstory: I used the windows installer to install Ubuntu 9.10 but my Vista Business is 64-bit. When i loaded Ubuntu i realized it was also 64-bit but i wanted 32-bit so i deleted it and started over.
I downloaded the live cd and used it to test if it would see the RAID. It found my RAID so i went ahead and tried to install, but i saw that it did not give me the option to install side-by-side with Windows. So... i went back into windows and created a partition. I then used the live cd to install Ubuntu and didn't know what options to pick so when it gave me the option to choose (the root I guess), I chose "/" over "/boot." Well it didn't boot. I am new to Linux so i was just messing around with it. Long story short I deleted the partition.

Now, i am trying to use the windows installer bc i figure the 64-bit is fine anyway but when i run "Wubi.exe" it says there is an installation present and it needs to be uninstalled first. so now, i can't have Ubuntu at all until i figure out how to:

A: Install via cd to dual-boot with windows
OR
B: Resolve the issue with Wubi so it will reinstall Ubuntu 9.10 64-bit.

Sorry for the length;)
Thanks for the help in advance!

---

### Post by darkod on 2009-12-10
The issue with wubi should be resolved by using add/remove programs. Wubi installs ubuntu inside windows and the removal should be from add/remove like any windows app. I don't know what you did first time and if you just deleted the ubuntu folder the uninstallation might not work. But try it.
Another point, depending how much you want to learn about ubuntu, wubi is not really proper side-by-side dual boot. I personally never use it, but it might be easier for lots of people. As long as you know that it's not "true" ubuntu (it will reside on your ntfs partitions for example).
For raid you need to use the alternate install cd, not desktop cd. But be warned, the installer is text based, not GUI. You still end up with desktop GUI system but the install process is text based. Are you up for a challenge? :)
Find the alternate cd here:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by jlloyd_ndpdd on 2009-12-11
> **darkod said:**
> As long as you know that it's not "true" ubuntu (it will reside on your ntfs partitions for example).


wow i didn't realize that. thanks! i do hope to get into Ubuntu with the file system and all, but one step at a time, right? :)

---

### Post by darkod on 2009-12-11
> **jlloyd_ndpdd said:**
> wow i didn't realize that. thanks! i do hope to get into Ubuntu with the file system and all, but one step at a time, right? :)

As I said, as long as you're aware of the differences, use what ever is working for you. :)
The "bad" side of wubi is that I've seen people here that actually think they have the full dual boot install, with separate partitions, etc. I don't mind if people use it (who am I to do it anyway?), but I just feel it needs to be more clearly said what is the difference and what that means.

---

### Post by jlloyd_ndpdd on 2009-12-11
its true that i had no idea that the file system would be different. what is the difference? do you think that being in NTFS makes it accessible by viruses, etc? :confused:

---

### Post by darkod on 2009-12-11
> **jlloyd_ndpdd said:**
> its true that i had no idea that the file system would be different. what is the difference? do you think that being in NTFS makes it accessible by viruses, etc? :confused:
Well, I'm not that much of an expert, but if linux wanted to work on ntfs they would have made it like that from the start right? I believe ext3 and now the next ext4 had advantages over ntfs. You can read more about the filesystems if you want to.
Also, the fact that wubi is inside windows goes against the "dual boot" principle. If you windows install goes, your wubi is gone too. Which is not the case in side-by-side install.
To be honest, I didn't read too much about the differences myself too. I haven't used linux a lot but I always used it side-by-side, on its own partition with its own filesystem.

PS. In fact if it wasn't for few windows applications that I really need to work with, I would have dropped windows all together.

---

### Post by jlloyd_ndpdd on 2009-12-11
> **darkod said:**
> 
PS. In fact if it wasn't for few windows applications that I really need to work with, I would have dropped windows all together.
  That seems to be the resounding consensus LOL
Thanks for all your help!:popcorn:

---

