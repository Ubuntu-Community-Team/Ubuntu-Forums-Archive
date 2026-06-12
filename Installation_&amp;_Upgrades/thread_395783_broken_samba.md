---
title: "broken samba"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by lukemack on 2007-03-28
hi,

I am getting this error in 6.10 server when trying to install samba (having removed it with apt-get).


E: Sub-process /usr/bin/dpkg returned an error code (1)

luke@DeepThought:/etc/rc2.d$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed
  samba
0 upgraded, 1 newly installed, 0 to remove and 41 not upgraded.
Need to get 0B/3028kB of archives.
After unpacking 7569kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 104588 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.22-1ubuntu4.1_i386.deb) ...
Setting up samba (3.0.22-1ubuntu4.1) ...
 * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
luke@DeepThought:/etc/rc2.d$ 

i have tried removing samba in synaptic, from the command line etc and tried removing samba links in the rc2 folder as as suggested elsewhere on the forum.

any ideas how i can fix this?

thanks,

<L>

---

### Post by lukemack on 2007-03-28
fixed - i had installed gsambad (big mistake) and this had overwritten smb.conf. fortunately, it made a backup first in /etc/samba. i renamed that to smb.conf, reinstalled and it all works fine.

does anyone have a GOOD experience with a samba gui?

---

