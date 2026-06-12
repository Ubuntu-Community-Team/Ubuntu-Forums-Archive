---
title: "Help me please ...install broken, can't fix"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Ambimom on 2006-10-26
How do I fix this?  I can't remove samba and I don't know how to repair it.  Nothing else will load. It says: > Error: BrokenCount>)

> ambimom@Ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 379 not upgraded.
Need to get 0B/2904kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 119758 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
 If I can't fix it, what do I do?  Can I load it from the live cd?  I'm baffled.

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

