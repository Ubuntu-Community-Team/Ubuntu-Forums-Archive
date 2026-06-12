---
title: "Old HDD in newer system"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by stretch_af on 2012-02-11
I scavenged the hard drive from my mom's computer that died(fairly certain motherboard issues).  It has Vista on it.  I would like to put this hard drive into my computer that currently only has Ubuntu 10.04 LTS.  Two hard drives, two operating systems would be my goal with Vista intact.  Question is how do I get an old hard drive and OS to play nicely with my newer system.  I don't have any disks from the old drive before it died.  Both drives are SATA.  I've read that some Windows OS's deactivate themselves when moving to a different motherboard.

Thanks 
Justin

---

### Post by bluexrider on 2012-02-11
Its NOT! The 'old' hard drive will have the hardware configuration from 'mom's' computer and will not play nicely on yours. Unless the configuration on yours is exactly like mom's.

I would recommend a re-installation of Vista if you want it to work properly on your computer.

---

### Post by stretch_af on 2012-02-11
Thats what I was afraid of, and being without any disks for it...

---

### Post by darkod on 2012-02-11
You can still give it a shot. If it only misses few drivers but can still boot, you can add the drivers once booted.

If you need to add the vista in grub boot menu, attach the vista disk, let the computer boot ubuntu and just run:
sudo update-grub

If it doesn't work and you decide to remove the disk (or reformat it and use it as data disk), run the same command and it will delete vista from the boot menu when it sees it's not there.

---

### Post by bluexrider on 2012-02-11
> **stretch_af said:**
> Thats what I was afraid of, and being without any disks for it...
Actually there are work arounds, WHICH I CANNOT STATE HERE, but if you have the COA from the Windows machine. There are re-installation disks available. I would suggest searching other forums to obtain said disks.

---

### Post by AlanR8 on 2012-02-11
Hehe

I just took a hard disk out of an old P4 running 10.04, and put it in to a much newer machine, core 2 duo. 

It just booted up as normal, all hardware detected and connected to the web!

And people say Doze is friendly....yeah right! :D

PS. I then did a full reinstall to 12.04 Alpha!

---

