---
title: "MDADM - How to preserve breezy - Dapper"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by slumption on 2006-06-10
I had Breezy running fine, used the upgrade via synpatic and it crashed out halfway stating to many errors during the upgrade. I have no network card showing up, samba has been uninstalled and things like

dpkg --configure -a
apt-get -f update

and other things haven't fixed the system.
My setup is, one drive with the OS on it
Then two other drives that are mirrored using MDADM.
If I reinstall the OS to the first drive and preserve the other two drives how do I get the raid up and running again?

I am assuming I can install MDADM, copy my MDADM.conf over as I have backed it up, and just alter my FSTAB.

At the moment I am running tapes to back all the date up but if I can just re-use my raid it would be easier.

---

### Post by slumption on 2006-06-10
I forgot to mention I was actually upgrading from Breezy to dapper

---

### Post by bozo on 2006-09-05
> **slumption said:**
> I forgot to mention I was actually upgrading from Breezy to dapper

Did you actually get around to upgrading your system?

I'm asking myself the very same question : got a fully mirrored system with mdadm (md0 as /, md1 as swap and md2 as a general-purpose partition), and I'm afraid an upgrade might blow it all to hell ...

I shouldn't be affected by the udev reordering bug, since I'm only using the two onboard IDE ports, but I've had woes before when setting up grub and rebuilding my initrd for a boot straight off the md0 partition.

Does anyone know exactly what the upgrade process does regarding :
- the grub configuration file
- the way initrd is rebuilt
- the mdadm configuration?

---

