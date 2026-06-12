---
title: "OpenOffice blocks installation"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by Ordep_ on 2007-03-17
I tried to install OO on Xubuntu 6.10 yesterday following some of the posts here but it did'nt work. Now i'm trying to install wpasupplicant but an error pops out

 E:The package openoffice.org-core04u needs to be reinstalled, but I can't find an archive for it.


 I notice that the same message appear in the Add/Remove option everytime I try to install/uninstall anything.

 Any idea of how to get rid of that????????

---

### Post by bapoumba on 2007-03-17
```
~ $ aptitude show openoffice.org-core04u
E: Unable to locate package openoffice.org-core04u

```
How did you install Openoffice ? From the rpms ?

---

### Post by Ordep_ on 2007-03-17
i did the alien thig to create the debs 

I ran you command here the results... 


ordep@ordep-laptop:~$ aptitude show openoffice.org-core04u
Package: openoffice.org-core04u
New:yes
State:Partially installed
Automatically installed: No
Version: 2.1.0-7
Priority: extra
Section: alien
Maintainer:
Uncompressed Size: 0
Description:

---

### Post by bapoumba on 2007-03-17
[http://ubuntuforums.org/showthread.php?t=318865]("http://ubuntuforums.org/showthread.php?t=318865")
Is this the procedure you have followed ?

---

### Post by Ordep_ on 2007-03-17
yep

---

### Post by bapoumba on 2007-03-17
Previous version of openoffice have to be removed before you go with this procedure. Did you do that ?
I'll try to chime in Hagar de L'Est, he is an OOo wiz ;)

---

### Post by Ordep_ on 2007-03-17
I did not.... because I have'nt installed any OO yet, it have a version on the packages but never added it, now it seems like two of the OO components(Draw and Presentation i think) are marked as installed but it doesn't let me uninstall em' because of the same thing with the package error.

There's a way to DELETE and REMOVE everything related to OO from the terminal so i can start all over again???



Muchas Gracias!

---

### Post by Hagar Delest on 2007-03-18
I think you've first to uninstall all the OOo packages via Synaptic for example. Sometimes, you've to remove packages before others (try the language ones first). Then reinstall OOo but reconverting the RPMS :
Here are the commands to install OOo, note the *--scripts* option needed.
```
cd rep_install_OOo/RPMS
```
Sometimes, there is a warning from *alien* that says it encountered errors with scripts. Better use  the *--scripts* option to avoid it :
```
sudo alien -d *.rpm --scripts
sudo dpkg -i *.deb
```
- Then update the Gnome menu and file association:
```
cd desktop-integration
sudo dpkg -i openoffice.org-debian-menus_2.0.4-2_all.deb
```
Hope this helps.

---

### Post by Ordep_ on 2007-03-19
Every time I try to go to synaptic this pops out :


E: The package openoffice.org-core04u needs to be reinstalled, but I can't find an archive for it

and the Synaptic show nothing, nothing from the reload, search, nothing totally blank


Other way to remove OO???? is bothering in every process and it's not even available.

---

### Post by Ordep_ on 2007-03-19
> **Hagar de l'Est said:**
> [SIZE="4"]**[COLOR="Orange"]I think you've first to uninstall all the OOo packages via Synaptic for example[/COLOR]**[/SIZE]. Sometimes, you've to remove packages before others (try the language ones first). Then reinstall OOo but reconverting the RPMS :


This is exactly what I want to do but synaptic getts blocked for the same process

any help Hagar??

Thanks

---

### Post by Hagar Delest on 2007-03-20
I'm not a package management expert so I would advise to search how to force DPKG or APT to uninstall a package. It must exist, something like a '-force' option in the command.

I just searched the web, try this : 'dpkg --remove --force-remove-reinstreq package_name'

---

### Post by Ordep_ on 2007-03-21
It Worked!!!!!

Thanks a lot!!!

---

