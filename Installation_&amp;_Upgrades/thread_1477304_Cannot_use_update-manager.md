---
title: "Cannot use update-manager"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by mreh.Eh on 2010-05-08
When I try to use update-manager I get this message:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.'

This came after my computer shut down in the middle updating to 10.04.

---

### Post by DougieFresh4U on 2010-05-08
Have you fired up the 'terminal' and tried any 'sudo' magic?:p
```
sudo aptitude -f install
sudo dpkg --configure -a
```
Sorry to here of your drama.

---

### Post by mreh.Eh on 2010-05-08
I get:

max@Netbook:~$ sudo aptitude -f install
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.
Reading package lists... 0%    
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.

---

### Post by mreh.Eh on 2010-05-08
Anyone?

---

