---
title: "I try to install VMware - Gtk-WARNING - Failed to load module &quot;canberra-gtk-module&quot;:"
date: 2015-06-28
forum: Installation &amp; Upgrades
---

### Post by conny2 on 2015-06-28
Hello,

I need to install VMware on Ubunto 15.02, but I get always the same error. I found many solutions in this forum and other forums, but not one of them helped. 
It is really wired. I just installed Ubuntu 15.02 and then I installed all the updates Ubuntu offers just after the installation of Ubuntu. Right after this I tried to install VMware and get the error. I even reinstalled Ubuntu but I had the same Error. 

I despair slowly :shock: and I would be very happy about help. Many thanks in advance. :-(

Error:
 (vmware-installer.py:1957): Gtk-WARNING **: Im Modulpfad »murrine« konnte keine Themen-Engine gefunden werden,
 Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
OR in English
Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory


I tried to install VMware using this very detailed guide: [https://www.liberiangeek.net/2014/12/install-vmware-workstation-11-ubuntu-14-10/](https://www.liberiangeek.net/2014/12/install-vmware-workstation-11-ubuntu-14-10/)

I found solutions in several threats, but non of them helped:
[http://ubuntuforums.org/showthread.php?t=2061142](http://ubuntuforums.org/showthread.php?t=2061142)
[http://superuser.com/questions/337639/how-to-fix-unable-to-locate-theme-engine-in-module-path-murrine](http://superuser.com/questions/337639/how-to-fix-unable-to-locate-theme-engine-in-module-path-murrine)
[https://bbs.archlinux.org/viewtopic.php?id=46025](https://bbs.archlinux.org/viewtopic.php?id=46025)


I already tried:
 sudo apt-get install gtk2-engines-murrine -> here it installed a lot of things, but error was still there 
sudo apt-get install gtk2-engines-murrine:i386 
sudo apt-get install --reinstall gtk2-engines-murrine:i386 -> here it deinstalled and then installed a lot of things, but error was still there 
sudo apt-get install libgtkmm-2.4-1c2a libgtkmm-2.4-dev -> installation worked, but error was still there


I tried this but it just don't work anyway:
Export GTK_PATH=$GTK_PATH:/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/ -> I get an error, I think I did something wrong with the command
sudo yum install gtk2-engines gtk-murrine-engine gtk-equinox-engine -> I get an error, I think the command is wrong. Ubuntu did not Know "yum"

I did not understand what I should do here?
-> the modification of adding the GTK_PATH to bash.bashrc
-> vi /etc/bash.bashrc -> append to file -> export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/ -> exist current shell and open a new one and check.

---

