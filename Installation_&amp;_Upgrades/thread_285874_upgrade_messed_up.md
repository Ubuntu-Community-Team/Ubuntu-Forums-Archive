---
title: "upgrade messed up"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by matt91 on 2006-10-27
i decided to upgrade ubuntu to 6.10 with the update manager as shown on [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) 

it downloaded all the packages successfully and i got a few errors through the update which i just canceled. "9 mins" from completing the install i got an error popup when it was installing ubuntu-desktop. i closed the message and the update manager closed. i then decided to restart and i can login to my desktop but when i run update manager i get this message:
> 
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

i did what it told me to do and synaptic shows me the samba package broken and i cannot update or remove it, i get the message:
> 
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb: subprocess new pre-removal script returned error exit status 102

is there any way to fix my ubuntu and finish upgrading?

thank you

---

### Post by useResa on 2006-10-27
I encountered exactly the same problem and found the answer [here]("http://www.ubuntuforums.org/showthread.php?t=285487")

What you should do is:
```
sudo rm -f /etc/rc2.d/K09samba
```Next I did ```
sudo apt-get install -f
```With the following result
> 
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2904kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 184664 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386.deb) ...
 * Stopping Samba daemons...                                             [ ok ] 
Unpacking replacement samba ...
Setting up samba (3.0.22-1ubuntu4) ...
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
 * Starting Samba daemons...                                             [ ok ] 


---

### Post by matt91 on 2006-10-27
thank you, that fixed it:D

---

