---
title: "extracting vuze update"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by pak bear on 2010-04-06
hi to all ubuntu experts here...i have extracted the vuze update eg:-Vuze_Installer.tar.bz2...but it gave me this result...and my azureus can't be running till now...please help anyone...total newbie here:lolflag:

tar jxvf /home/faridz/Downloads/Vuze_Installer.tar.bz2
vuze/
vuze/vuze.schemas
tar: vuze/vuze.schemas: Cannot open: File exists
vuze/ChangeLog.txt
tar: vuze/ChangeLog.txt: Cannot open: File exists
vuze/GPL.txt
tar: vuze/GPL.txt: Cannot open: File exists
vuze/updateAzureus
tar: vuze/updateAzureus: Cannot open: File exists
vuze/README.txt
tar: vuze/README.txt: Cannot open: File exists
vuze/azureus
tar: vuze/azureus: Cannot open: File exists
vuze/vuze.torrent.png
tar: vuze/vuze.torrent.png: Cannot open: File exists
vuze/vuze.desktop
tar: vuze/vuze.desktop: Cannot open: File exists
vuze/plugins/
vuze/plugins/azrating/
vuze/plugins/azrating/azrating_1.3.1.jar
tar: vuze/plugins/azrating/azrating_1.3.1.jar: Cannot open: File exists
vuze/plugins/azupdater/
tar: vuze/plugins/azrating: Cannot utime: Operation not permitted
vuze/plugins/azupdater/Updater.jar
tar: vuze/plugins/azupdater/Updater.jar: Cannot open: File exists
vuze/plugins/azupdater/azupdaterpatcher_1.8.13.jar
tar: vuze/plugins/azupdater/azupdaterpatcher_1.8.13.jar: Cannot open: File exists
vuze/plugins/azupdater/plugin.properties
tar: vuze/plugins/azupdater/plugin.properties: Cannot open: File exists
vuze/plugins/azplugins/
tar: vuze/plugins/azupdater: Cannot utime: Operation not permitted
vuze/plugins/azplugins/azplugins_2.1.6.jar
tar: vuze/plugins/azplugins/azplugins_2.1.6.jar: Cannot open: File exists
vuze/plugins/azupnpav/
tar: vuze/plugins/azplugins: Cannot utime: Operation not permitted
vuze/plugins/azupnpav/azupnpav_0.2.23.jar
tar: vuze/plugins/azupnpav/azupnpav_0.2.23.jar: Cannot open: File exists
vuze/plugins/azupnpav/azureus.sig
tar: vuze/plugins/azupnpav/azureus.sig: Cannot open: File exists
vuze/plugins/azupnpav/plugin.properties
tar: vuze/plugins/azupnpav/plugin.properties: Cannot open: File exists
vuze/vuze.png
tar: vuze/plugins/azupnpav: Cannot utime: Operation not permitted
tar: vuze/plugins: Cannot utime: Operation not permitted
tar: vuze/vuze.png: Cannot open: File exists
vuze/installer.log
tar: vuze/installer.log: Cannot open: File exists
vuze/Azureus2.jar
tar: vuze/Azureus2.jar: Cannot open: File exists
vuze/swt.jar
tar: vuze/swt.jar: Cannot open: File exists
vuze/TOS.txt
tar: vuze/TOS.txt: Cannot open: File exists
vuze/vuze
tar: vuze/vuze: Cannot create symlink to `azureus': File exists
tar: vuze: Cannot utime: Operation not permitted
tar: Exiting with failure status due to previous errors
faridz@ubuntu:~$

---

### Post by Halcyon31415 on 2010-04-08
Im in the same boat, Im pretty lame when it comes to figuring this stuff out, i would like to update to the latest version of Vuze as well. Im not sure what is required. I know it will be some work but it would be wonderful to get a step by step instruction list. 

Thank you in advance.

---

### Post by Halcyon31415 on 2010-04-10
Pak Bear, 
    This is what i did and got it to run. First off i cleaned out any and all things related to Vuze on my computer. Too many partial updates and old files. The best way i think to do this is go into the symantic package manager in your systems area. Choose to remove vuze. Then maybe do a file search or something and try to get the other loaner files hanging out on there own. I then found this instruction guide online. [Vuze Installer]("http://www.detector-pro.com/2009/12/how-to-install-vuze-43-and-newer-on.html") I followed the steps and it actually worked. So if you have any questions please let me know I hopefully can help you. :P

---

