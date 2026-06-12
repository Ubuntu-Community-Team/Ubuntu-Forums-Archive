---
title: "ACPI ERROR ... toshiba laptop"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by mackubex on 2011-01-24
hello to all da ubuntu gurus ,,, 

guys im new to linux ... 
nd i decided to get onto the ubuntu bandwagon ... ng 

after 2 weeks of troubleshooting i found out that ACPI on my toshiba laptop is causing a error during boot up .. 

from install screen using F6 ... (advice fm a guru on linuxforums.org) 
i cancelled ACPI .. 

managed to install UBUNTU ... 
now i am in a dilema .. i cant switch off ubuntu .. / comp 

coz wen i try to rebbot into ubuntu ... i get the ACPI ERROR ... 


plz plz plz .. tell me how do i cancell ACPI for good .. from within UBUNTU .,

---

### Post by sikander3786 on 2011-01-24
You can permanently turn of acpi in /etc/default/grub.

Edit your /etc/default/grub.

```
gksudo gedit /etc/default/grub
```

Find this line.

```
GRUB_CMDLINE_LINUX=""
```

And type *acpi=off* in between the quotes so it looks like.

```
GRUB_CMDLINE_LINUX="acpi=off"
```

Save and close that file.

Now, update your grub.cfg by,

```
sudo update-grub
```

The changes will take effect after a reboot.

Let us know about your progress ;-)

---

