---
title: "Installing with USB?"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by Mombie on 2008-10-21
Hello everyone
i'm planing on getting an acer netbook but it comes with xp and I'd prefere to put Ubuntu on it.

The thing is that it doesn't have a cd drive, I was wondering if it could be installed via a usb drive, or would I have to use an external drive?

Thanks :)

---

### Post by Herman on 2008-10-21
:) Hello Mombie,
See [Installation without a CD]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD") - in the Ubuntu Community Docs, and maybe even [Server and network installations]("https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations").

Usually, Acer computers come with a 'Recovery Partition', a 'C:\ drive' for Windows and a 'D:\ drive as well. (Three partitions already).
In some Acer computers, there is data stored in the 'D:\ drive for the Acer eRecovry software, and deleting the 'D:\' drive to install Ubuntu will cause some annoying pop-ups in Windows caused by deleting the 'eRecovery stuff.
Therefore it's probably best to leave the 'D:/' partition there and just resize it (shrink it), the eRecovery stuff takes up very little room, and make more partitions to install Ubuntu in.
The Ubuntu installer will probably make you an 'extended' partition automatically anyway, so your Ubuntu partition will probably turn out to be partition number 5, and your swap area will likely be partition number 6.

Regards, Herman :)

---

### Post by Mombie on 2008-10-21
Thanks so much :)

there have been alot of netbooks i've been looking at but they all come with watered down OS's which I dont care for much, so this info has been very helpful :)

---

