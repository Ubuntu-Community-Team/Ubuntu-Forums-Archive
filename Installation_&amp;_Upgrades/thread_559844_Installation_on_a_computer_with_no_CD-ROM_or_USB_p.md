---
title: "Installation on a computer with no CD-ROM or USB ports"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by benton on 2007-09-25
Hi there,

I found an old laptop in the basement. Boots Windows 98 but does not have USB ports or CD-ROM drive. Is there a way I could install *buntu (or some other distro) on this baby? Maybe from floppy or network?

Regards,

-Benton

---

### Post by markk1994 on 2007-09-25
i dont think theres a chance sorry.

---

### Post by newtinnyc on 2007-09-25
The old way was to use rawrite to create a bootable floppy, or a bootable network floppy from the cd. But you'd have to have a network with the cd shared out via either NFS, FTP or maybe SMB, then boot from the network bootable floppy and do a network based install. Problem is, that laptop is not capable of running a recent version of Linux, no matter what anyone says (except perhaps in text only mode). You either need a much newer machine, or a much older version of Linux.

---

### Post by benton on 2007-09-25
Hmmm... the laptop is running Windows 98 and I could take it to the office and hook it up to our LAN. If I then share the CD-ROM drive of another PC on the network and the laptop can see this shared drive, do you think I'd have a chance by inserting the Linux CD on the shared drive?

---

### Post by tombott on 2007-09-25
> **benton said:**
> Hmmm... the laptop is running Windows 98 and I could take it to the office and hook it up to our LAN. If I then share the CD-ROM drive of another PC on the network and the laptop can see this shared drive, do you think I'd have a chance by inserting the Linux CD on the shared drive?

No Ubuntu (somebody correct me if I am wrong) needs to boot from CD to install.

If the laptop has a parallel port you could go really old school and use a Parallel CD-ROM drive, but this would probably require you to purchase one.

What's the make and the model of the laptop?

You could possibly look into buying a docking station for it, I have picked up cheap docking stations off ebay before now for some old laptops.

Tom.

---

### Post by oilchangeguy on 2007-09-25
> **benton said:**
> Hi there,

I found an old laptop in the basement. Boots Windows 98 but does not have USB ports or CD-ROM drive. Is there a way I could install *buntu (or some other distro) on this baby? Maybe from floppy or network?

Regards,

-Benton

please post the computers specs, cpu speed, amount of ram, and hard drive size. it may not even be able to run any version of ubuntu.

---

### Post by logos34 on 2007-09-25
if it turns out you have the min. specs (256MB ram, 700MHz cpu, 4GB drive), you could try these network install guides:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Or try Xubuntu, or any distro using a lightweight desktop environment

---

