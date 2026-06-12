---
title: "Upgrading Win7 on dual boot while keeping ubuntu..."
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Slash621 on 2010-03-29
So today I have a single drive with Ubuntu on the first partition and MBR (Grub) and Windows 7 Release Canidate on the second partition.  I own a copy of Windows 7 Home and I want to install it fresh on the windows partition without harming my GRUB install if possible.  Please let me know if this is possible.  I just dont want to screw the linux side because thats where I keep all my schoolwork etc.  Im making a drive image just in case.  -Slash

---

### Post by Mark Phelps on 2010-03-29
> **Slash621 said:**
> ... I own a copy of Windows 7 Home and I want to install it fresh on the windows partition without harming my GRUB install if possible...

Sorry, not possible. Any MS Windows install will automatically rewrite the MBR of the drive on which it is installed.  MS does not provide you a choice in the matter.

You will have to reinstall GRUB after you do the Win7 install.

---

