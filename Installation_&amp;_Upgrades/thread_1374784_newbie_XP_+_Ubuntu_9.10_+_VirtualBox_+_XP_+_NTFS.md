---
title: "newbie: XP + Ubuntu 9.10 + VirtualBox + XP + NTFS"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by grigglestone on 2010-01-07
Maybe VirtualBox forum would be better for this, but since it involves the Ubuntu install thought I'd try here first.

Goal is to have a machine that I can boot either XP or Ubuntu, but when I run Ubuntu I can start VirtualBox with a VM that uses the alternative XP boot. File system will be NTFS.

This is for a new machine I am getting. The machine will come setup with a single partition hosting a corporate XP image.

So where should I start .. should blow away the XP image and create 2 partitions and start from there? Or should the Ubuntu install be able to install over windows and provide a boot manager (for the dual-boot option)? .. and if that works does it in fact create separate partitions?

Then the second part is whether it is possible to have VirtualBox load from the original XP install (yeah wrong forum, but maybe someone else here has done the whole thing).

thanks, David

---

### Post by marcopolo1981 on 2010-01-07
Do you really need a dual boot scenario, or can you just install XP in VBox and use that directly?
In my experience of VBox, I can do just about anything I do on a standard install, except gaming. If gaming isn't important, then I don't think you need to dual boot. Again, even if you could make a virtual machine boot from the real partition, graphics will be slower anyway.
I don't think VBox can boot from a real hard drive partition.
Another thing to note is that the hard drive install has the drivers and configurations for the real pc, so when you try to boot from it in a virtual machine, it will have a whole new set of drivers and configurations to deal with. I am pretty certain that it will only crash anyway.

Sorry I can't help.

---

### Post by Jose Catre-Vandis on 2010-01-07
It is possible, but your genuine XP install will want to be re-validated (due to the different but virtual hardware)

Search the forums for how to set it up, but it is really not worth the hassle unless you have a mission critical reason or mission critical hardware that can't cope with a quick reboot or a trip to a VM.

---

### Post by nerdy_kid on 2010-01-07
it is possible to get Virtual Box to boot an XP install, however, the process in nonreversible.  XP will only then boot in VirtualBox.  [http://ubuntuforums.org/showthread.php?t=769883&highlight=virtual+box+dual+boot](http://ubuntuforums.org/showthread.php?t=769883&highlight=virtual+box+dual+boot)

---

### Post by marcopolo1981 on 2010-01-08
Can you not dual-boot XP and Ubuntu, and have a seperate XP installed in VBox on Ubuntu? Do they have to be exactly the same?

---

### Post by grigglestone on 2010-01-08
> **marcopolo1981 said:**
> Can you not dual-boot XP and Ubuntu, and have a seperate XP installed in VBox on Ubuntu? Do they have to be exactly the same?

I could have separate .. but it would have been better to have the same setup/settings.

The use case is that most of the time I only need MS office apps so will do that in VBox. Sometimes I need the office apps plus some server apps that require large amounts of core memory (more than I can provide them in a VM).

So just seeing if a common XP image might work.

However based on input to date, it seems there are some issues .. so I'd rather take the safe route which means as you suggest.

---

