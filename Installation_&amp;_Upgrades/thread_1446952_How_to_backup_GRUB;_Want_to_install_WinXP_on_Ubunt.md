---
title: "How to backup GRUB; Want to install WinXP on Ubuntu 9.10 system (no 'menu.lst')"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by 50GreenDodge on 2010-04-04
Hi:
I am trying to install WinXP on my Ubuntu 9.10 notebook. I'm very happy with Ubuntu but I need WinXP because I cannot make my MiFi2200 internet card work in Ubuntu. (Have tried for weeks)

I have an instruction sheet that tells me it's a good idea to back up GRUB before getting into any other activities.  Instruction:
'Applications->Accessories->Terminal  Type: sudo gedit /boot/grub/menu.lst

Then I am to make a copy of 'menu.lst'

Problem: There is NO 'menu.lst' in my filesystem. Zero.Zip.Nada.

Any idea on what I should do to backup GRUB?  

Thank you all for the help you all have given me during my first few months as a Ubuntu baby.  

50GreenDodge - Phoenix, AZ.
[email]lavelle3@cox.net[/email]

---

### Post by oldfred on 2010-04-04
grub2 uses grub.cfg but that is created dynamically every time you run sudo upate-grub. If they were talking about backing but grub perhaps they were discussing the MBR. But it is so easy to reinstall grub to the MBR that no backup is really required. Of course any important data your have should be backed up before any system changes.

If you have a new install of 9.10 you have grub2. Updates from 9.04 to 9.10 will still have grub legacy (0.97).
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

