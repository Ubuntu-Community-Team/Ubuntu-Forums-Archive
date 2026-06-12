---
title: "Upgrade from 16 to 18"
date: 2019-09-03
forum: Installation &amp; Upgrades
---

### Post by mcp1766 on 2019-09-03
Hello,
I'm running Ubuntu 16.04 server with Ubuntu Desktop, Apache, Php, Mysql, Samba ans owncloud.
I want to upgrade to Ubuntu 18.04 (Do I need the Desktop/server edition ? and if it is Desktop edition does it contains Apache, Phph, Mysql ? Or do I need to upgrade them manually ?
Apache and Mysql are configured to have the documents & data dir on a external usb drive.  I have several Samba shares.
Just want to know if the upgrade will not alter these apps configurations means my shares will remain the same and active and my config for Apache & Mysql will remain the same.
Just also defined fixed IP (what about after upgrading ?)
Want also to know if Php will be upgraded to 7.2
I have also a self-signed SSL for Apache. Do I need to recreate another one ?

Thanks.

---

### Post by grahammechanical on 2019-09-03
I do not think that it will make any difference. The upgrade scripts will upgrade all the packages installed as part of the OS and any additional packages that you have installed if updated versions are in the 18.04 repositories.

You may find that the User Interface of Unity 7 will change to Gnome 3 shell. You may get an option at the login screen to load into Unity or Ubuntu (Gnome 3 shell). As 16.4 is still in life you do not have the issue of doing an End of Life upgrade. 

[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

The command recommended in that link will work with server or desktop systems. I think that you should consider your system to be basically a server edition and not a desktop edition with some server applications added.

Regards.

---

### Post by mcp1766 on 2019-09-04
Thank you !

---

### Post by Skaperen on 2019-09-04
the desktop edition does not contain most server packages.  that's the same with 16 and 18 as it was with 12 and 14.  but you can add them on.  one way to do it install a fresh server edition somewhere (a VM?) and gather the list of packages it has ([COLOR=#008000][FONT=courier new]dpkg -l|egrep ^ii[/FONT][/COLOR]) and install those on the desktop installation (a fresh install).

although i always recommend a fresh install (and a separate non-reformatted [COLOR=#0000ff][FONT=courier new]/home[/FONT][/COLOR] partition), if you are doing a version upgrade, it should upgrade every package you have.  i am unsure if it handle package renaming and package splits well.

if you do any coding in Python, 18.04 gets you on Python 3.6. which is a nice improvement over 3.5.

---

### Post by mcp1766 on 2019-09-05
Hello Skaperen,
Thank for your answer.  At the first time I installed the server edition of Ubunt 16 then from the Terminal I installed ubuntu-desktop.  Now I wonder If I can upgrade to 18.04 and which version to take (server or desktop).  I thing the command "do-release-upgrade' is for the server edition, not sure ..  So maybe I can check on a VM which packages ares installed on  a server edition then install them on my 16's version then do 'do-release-upgrade' ... ?

---

