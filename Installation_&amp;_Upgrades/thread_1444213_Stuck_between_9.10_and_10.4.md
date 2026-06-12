---
title: "Stuck between 9.10 and 10.4"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by H13N.H3N on 2010-04-01
well, i found a  solution by myself, which is quite good taking in count how many problems are being reported:
Problem:

```
E: ubuntustudio-plymouth-theme: subprocess installed post-installation script returned error exit status 2
E: ubuntustudio-look: dependency problems - leaving unconfigured
E: ubuntustudio-default-settings: dependency problems - leaving unconfigured
E: ubuntustudio-desktop: dependency problems - leaving unconfigured
```
Here's some Terminal action: 
```
h13n-h3n@R-System:~$ sudo apt-get install ubuntustudio-plymouth-theme
[sudo] password for h13n-h3n: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libx264-67 libfaad0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ubuntustudio-plymouth-theme
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.3kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Selecting previously deselected package ubuntustudio-plymouth-theme.
(Reading database ... 139417 files and directories currently installed.)
Unpacking ubuntustudio-plymouth-theme (from .../ubuntustudio-plymouth-theme_0.38.1_all.deb) ...
Setting up ubuntustudio-plymouth-theme (0.38.1) ...
update-alternatives: error: alternative path /lib/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth doesn't exist.
dpkg: error processing ubuntustudio-plymouth-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntustudio-plymouth-theme
E: Sub-process /usr/bin/dpkg returned an error code (1)
h13n-h3n@R-System:~$ 

```
Solution, just write in terminal 'sudo nautilus' which will open a nautilus explorer as root, go to /lib/plymouth/themes and copy an already existing theme, then rename the theme's folder (for example ubuntu-logo) to 'ubuntustudio-logo', go into the renamed folder and rename the file *.plymouth as 'ubuntustudio-logo.plymouth' this will do the trick. =)

---

### Post by H13N.H3N on 2010-04-01
bump, solution found

---

### Post by xtemplarx on 2010-04-01
Yup this got me past the error as well!  Thanks for posting the solution.

---

