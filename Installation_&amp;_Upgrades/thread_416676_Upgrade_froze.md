---
title: "Upgrade froze"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by gman2004 on 2007-04-21
My upgrade froze, if I reboot will it continue or I will have to do a clean install.
It froze while installing the upgrade.

---

### Post by DougieFresh4U on 2007-04-21
From the terminal try **sudo apt-get -f install** then **sudo dpkg --configure -a** Let me know what happens

---

### Post by gman2004 on 2007-04-21
I can't use terminal. Everything is frozen, shall I reboot?

---

### Post by DougieFresh4U on 2007-04-21
Can you alt-F2 for terminal? If not iI would say yes reboot and then try the codes I had posted. Sorry to hear your misfortune:(

---

### Post by gman2004 on 2007-04-21
I rebooted and in terminal I typed the commands.
It's working. What stage it will restore? Is it going to go back to edgy or it will continue the upgrade?

---

### Post by gman2004 on 2007-04-21
It finished with these error:
[HTML]Errors were encountered while processing:
 openoffice.org-impress
 openoffice.org-draw
 acpid
 gnucash
 openoffice.org-calc
 openoffice.org-writer
 python-examples
[/HTML]

---

### Post by DougieFresh4U on 2007-04-21
Whats it saying in terminal? It should pick up but I don't know how far you were in the upgrade proccess. Had it gotten all the packages and was it unpacking or setting up, also how were you doing the upgrade, update manager or from the terminal? EDIT: try the **sudo apt-getr -f install** then **sudo dpkg --configure -a**

---

### Post by gman2004 on 2007-04-21
I did on terminal apt-get -f again and it started the upgrade again.
I think it works:) 

Thank you, That's what Ubuntu is all about!
Thank you again.

---

### Post by DougieFresh4U on 2007-04-21
No problem :) Let us know if all goes ok. I am no "guru" but I have learned from my mistakes and trial and error and of course from the Ubuntu community

---

### Post by gman2004 on 2007-04-21
Unfortunately, I don't  think things went right.
Add of course your help is welcomed.
[HTML]*********@Main:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 gnome-power-manager
 gnome-session
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML] [HTML]**********@Main:~$ sudo dpkg --configure -a
Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 ubuntu-desktop
 acpi-support
 powermanagement-interface
 gnome-power-manager
 gnome-session
[/HTML]

---

### Post by lmc on 2008-02-05
does anyone have a solution to this that doesnt involve wiping my partition???

I have the EXACT same problem, I tried doing "sudo dpkg --configure -a" and that only did so much then still spat out
```
lmc@lmc:~$ sudo dpkg --configure -a
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ]
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 kubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 kubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 kubuntu-desktop

```


arghhhhhhhh. any clues at all?? how do I configure acpid since this seems to keep flagging up as an error??

---

### Post by lmc on 2008-02-05
found this!!!

[http://ubuntuforums.org/showthread.php?p=4276823#post4276823](http://ubuntuforums.org/showthread.php?p=4276823#post4276823)


and the important bit is > 
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
sudo dpkg --configure -a



and this worked. I did the first step twice to make sure it was stopped.

let me know if this works for you!

---

