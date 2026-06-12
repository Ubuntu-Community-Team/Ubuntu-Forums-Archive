---
title: "Install Ubuntu 6.10 on nForce4 SATA drive"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Bram77 on 2007-02-03
I've been struggeling with this eversince I have nForce4 motherboards. I'm realy enthousiastic about (K)ubuntu, and have had it installed on my PC on a IDE drive, but I don't have IDE drives anymore.

I would realy....realy like to install (K)ubuntu on one of my SATA drives. I use the Nvidia nForce4 SATA controller, in SATA, mode on my ASUS K8N4E-Delux mainboard for both my drives. One is for Windows, the other one I'd like to use for Linux.
When I try to install Ubuntu, I can't create any partition to install to, because the installer can't see my drives. Most likely my chipset is not supported and I'd like to know how to make Ubuntu see my chipset/SATA controller zo I can start installing this wonderfull distibution.

I have had the same problems with all other distributions I've tried. SUSE, Debian and Mandriva.

Thank you in advance.

---

### Post by Garyu on 2007-02-03
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Maybe this wiki entry can help you?
I got nForce4 as well and installed on a SATA drive without problems. But I'm guessing you are running a software RAID with several disks made into one?

---

### Post by Bram77 on 2007-02-03
Thank you for the quick reply.

no, I have RAID disabled. I'm not using the Silicon controller but the integrated nForce SATA/RAID controller, in SATA mode. I have two seperate drives, both on the SATA controller.
I've had ubuntu 6.06 installed on a IDE disc, but the drive crashed beyond repair. In that situation I wasn't able to see the drives connected to the SATA controller either.

---

