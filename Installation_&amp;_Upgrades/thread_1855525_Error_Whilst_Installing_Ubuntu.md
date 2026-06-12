---
title: "Error Whilst Installing Ubuntu"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by Jamieyates14 on 2011-10-06
Hi, While I was trying to install Ubuntu on my Sony Laptop it comes up with ''Error Executing Command'' and just stops. A Picture is attached. Does anyone know how to fix this error?
Oh and it's Ubuntu 11.04(or the newest one)
I also tried using the Wubi thing, it took around 15 hours to install and it installed I think, but when I rebooted nothing happened, I thought it would come up with dual boot when I restarted, but it didn't. 
By the way I am a complete newbie at this so correct me if I'm wrong about something.

---

### Post by MAFoElffen on 2011-10-06
> **Jamieyates14 said:**
> Hi, While I was trying to install Ubuntu on my Sony Laptop it comes up with ''Error Executing Command'' and just stops. A Picture is attached. Does anyone know how to fix this error?
Oh and it's Ubuntu 11.04(or the newest one)
I also tried using the Wubi thing, it took around 15 hours to install and it installed I think, but when I rebooted nothing happened, I thought it would come up with dual boot when I restarted, but it didn't. 
By the way I am a complete newbie at this so correct me if I'm wrong about something.
I don't have a lot of experience with Wubi, (do have an understanding of) but I believe your picture was a Wubi install / Windows error saying that it had a problem during the windows boot manager add of the Ubuntu item....  Maybe someone else with more Wubi experience can explain how to get around that.  Or go to the [Wubi Mega-thread]("http://ubuntuforums.org/showthread.php?t=1639198").  I'm sure many have come up with that already and have been answered.

As for what you explained was your goal on creating a dual boot... That is traditionally thought of as being to install Ubuntu into a created new separate partition and uses Grub as the boot manager.  Whereas installing Ubuntu "Alongside Windows" or Wubi, installs into a disk image file within the Windows partition and uses the win boot manager as the boot manager.

---

### Post by bcbc on 2011-10-06
Your bcd store is corrupted according to that message. That's a windows issue so best to figure out whether the message is accurate and how to fix it via Windows support forums/the net.

[http://answers.microsoft.com/en-us/windows/forum/windows_7-system/corrupt-configuration-registry-database-unable-to/fd24e4f9-b327-464e-b023-245773557aa1](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/corrupt-configuration-registry-database-unable-to/fd24e4f9-b327-464e-b023-245773557aa1)
[http://support.microsoft.com/kb/822705](http://support.microsoft.com/kb/822705)

---

### Post by Jamieyates14 on 2011-10-06
Ok Thanks for the fast reply, so I need to repair windows?

---

### Post by Jamieyates14 on 2011-10-06
> **bcbc said:**
> Your bcd store is corrupted according to that message. That's a windows issue so best to figure out whether the message is accurate and how to fix it via Windows support forums/the net.

[http://answers.microsoft.com/en-us/windows/forum/windows_7-system/corrupt-configuration-registry-database-unable-to/fd24e4f9-b327-464e-b023-245773557aa1](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/corrupt-configuration-registry-database-unable-to/fd24e4f9-b327-464e-b023-245773557aa1)
[http://support.microsoft.com/kb/822705](http://support.microsoft.com/kb/822705)
So I need to repair my windows?

---

### Post by Jamieyates14 on 2011-10-06
> **MAFoElffen said:**
> I don't have a lot of experience with Wubi, (do have an understanding of) but I believe your picture was a Wubi install / Windows error saying that it had a problem during the windows boot manager add of the Ubuntu item....  Maybe someone else with more Wubi experience can explain how to get around that.  Or go to the [Wubi Mega-thread]("http://ubuntuforums.org/showthread.php?t=1639198").  I'm sure many have come up with that already and have been answered.

As for what you explained was your goal on creating a dual boot... That is traditionally thought of as being to install Ubuntu into a created new separate partition and uses Grub as the boot manager.  Whereas installing Ubuntu "Alongside Windows" or Wubi, installs into a disk image file within the Windows partition and uses the win boot manager as the boot manager.
I guess installing grub will give me the choice of operating system on start up?

---

### Post by dino99 on 2011-10-06
do a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

