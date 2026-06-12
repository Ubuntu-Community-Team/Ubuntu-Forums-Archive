---
title: "Samba Upgrade on 6.06"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Hotei on 2007-05-17
Another one that came out of the blue...

Got the notification that there were updates available.  OK, downloaded and installed the updates and it broke Samba!  Here is the output of the install...

root@raiden:/root# apt-get -f install
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
Need to get 2849kB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba 3.0.22-1ubuntu3.3 [2849kB]
Fetched 2849kB in 16s (175kB/s)
Preconfiguring packages ...
(Reading database ... 98533 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.2 (using .../samba_3.0.22-1ubuntu3.3_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea on how to fix this?

Thanks

---

### Post by Hotei on 2007-05-17
OK, manually removed /etc/rc2.d/K09samba and re-ran apt-get -f install...

This worked but I have some other erros...

update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba

What is this about?  Did the package get posted broken or has something weird changed on my system.  Everything has been installed from the repositories.

---

### Post by wpshooter on 2007-05-17
> **Hotei said:**
> OK, manually removed /etc/rc2.d/K09samba and re-ran apt-get -f install...

This worked but I have some other erros...

update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba

What is this about?  Did the package get posted broken or has something weird changed on my system.  Everything has been installed from the repositories.

This is the result you get when software in released without being **PROPERLY** tested first !!!  Please note that I said properly.

---

### Post by Hotei on 2007-05-17
If that is the honest answer, that is sad news.

---

### Post by aalit on 2007-05-31
I found the answer to this problem on [https://answers.launchpad.net/ubuntu/+question/3583](https://answers.launchpad.net/ubuntu/+question/3583) It worked fine. Good luck!

---

