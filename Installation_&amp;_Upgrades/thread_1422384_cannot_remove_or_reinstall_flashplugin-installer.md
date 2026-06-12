---
title: "cannot remove or reinstall flashplugin-installer"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by koyigo on 2010-03-05
Hi! I installed flashplugin-installer in my ubuntu netbook remix, i found out that it couldnt play net videos. I have tried to purge it inorder to install adobe flash player but it is not going away. this is the message i get:-
[B][I]koyigo@ubuntu:~$ sudo apt-get -f purge flashplugin-installer
[sudo] password for koyigo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  qt4-qtconfig
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-installer*
0 upgraded, 0 newly installed, 1 to remove and 117 not upgraded.
1 not fully installed or removed.
After this operation, 180kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 159881 files and directories currently installed.)
Removing flashplugin-installer ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-installer (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I][/B]
wat can i do to get to stream live videos from the net? please help.

---

### Post by pastalavista on 2010-03-05
First run 'sudo apt-get update' and then 'sudo aptitude safe-upgrade'. Then remove 'flashplugin-installer'. You might need to remove 'iceape-flashplugin' too but you won't need it if you install 'adobe-flashplayer'. I believe you need 'ubuntu-restricted-extras' installed to install adobe-flashplayer because of their license agreement.

---

### Post by koyigo on 2010-03-06
sat infront of ma computer today doin that but it is still not going away. thank you though

---

