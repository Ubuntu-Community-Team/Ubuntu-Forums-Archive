---
title: "Ubuntu 10.10 Installation Failed"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by chessteacher on 2010-11-24
Installation nightmare.
 
Here is the problem. My computer's powered down in the middle of an ubuntu 10.10 upgrade.
 
Yesterday 
 
**I began installing ubuntu 10.10 as an upgrade** 
 
and everything was going fine. I unplugged my computer to move it only after 
 
**Downloading Packages completed**
 
The computer prompted ready to
 
**Install**
 
and I selected OK and left the room. When I returned, the computer was powered off. Then I noticed that I failed to plug it in. 
 
Can this be reinstalled without any loss of user files? Thank You

---

### Post by Quackers on 2010-11-24
It is possible that data has been lost. Have you tried booting it up? What happens - nothing? 
All I can really suggest is that you try re-installing again and if you had a separate home partition try using that again in the partitioning stage.

But this time plug it in! That's the benefit of using a laptop - no power outages! Well, normally :-)

---

### Post by sikander3786 on 2010-11-24
As **Quackers** asked above, what happens when you power on your laptop? Can you see the Grub menu? (press and hold down the Shift key from Bios screen)

If you could get into the recovery mode and drop to shell, you might be able to fix those problems without re-installation.

---

### Post by chessteacher on 2010-11-24
[COLOR=#000000][FONT=Verdana]>>As **Quackers** asked above, what happens when you power on your laptop? Can you see the Grub menu? (press and hold down the Shift key from Bios screen)

I can see the Grub menu.  When I select the New Kernel in the menu, the system starts to load but fails.  The screen messages reads "The configuration defaul for gnome power manager has not been installed correctely, consult your administrator"

I can login to a separate partition which has an older Ubuntu OS version.  There, I see my original system but I want to boot and use that system.  Is there a way to have the original system (ubuntu 10.10) complete the installation? Or can I rollback to Ubuntu 10.04 and then restart it to give a clean Ubuntu 10.10? 

Thank You
[/FONT][/COLOR]

---

### Post by wilee-nilee on 2010-11-24
If you can boot to a command line run these two commands, not a live cd but a command line in the HD.

sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by chessteacher on 2010-11-26
Thank you all for your help.  I fixed it!
I was able to edit grub to show the link for "single user" boot.  Then I selected that option.  Next, I got a prompt to make a menu selection which included a way to reinstall the upgrade. It was as if the Ubuntu's creators new I would have this problem.  It runs as good as ever.

---

