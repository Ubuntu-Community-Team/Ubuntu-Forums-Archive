---
title: "update's broken"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by check123 on 2007-02-28
need a hand..

a few days ago during an update, i received an error message:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

i ran the "sudo apt-get install -f"

i get the following:
aaa@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
39 not fully installed or removed.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 113876 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


and ideas?

---

### Post by nyinge on 2007-03-01
Try this first:
```
  apt-get remove --purge samba --dry-run  
```
It won't actually remove samba but only a simulation.  Look out for any error messages.  If none, issue the same command without "--dry-run".

Then, reinstall samba:
```
  apt-get install samba  
```

See if it still complains.

---

### Post by check123 on 2007-03-24
thanks nyinge for your time,

here's what i got

bill2@ubuntu:~$ sudo apt-get remove --purge samba --dry-run
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 27 not upgraded.
39 not fully installed or removed.
Purg samba [3.0.22-1ubuntu3.1]
Conf libc6-i686 (2.3.6-0ubuntu20.4 Ubuntu:6.06/dapper-updates)
Conf language-pack-en (1:6.06+20070129 Ubuntu:6.06/dapper-updates)
Conf language-pack-en-base (1:6.06+20070129 Ubuntu:6.06/dapper-updates)
Conf libisc11 (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf libdns21 (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf libisccc0 (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf libisccfg1 (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf libbind9-0 (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf liblwres9 (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf bind9-host (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf dnsutils (1:9.3.2-2ubuntu1.2 Ubuntu:6.06/dapper-security)
Conf app-install-data-commercial (5.3 Ubuntu:6.06/dapper-updates)
Conf libgtk2.0-bin (2.8.20-0ubuntu1.1 Ubuntu:6.06/dapper-security)
Conf libgtk2.0-0 (2.8.20-0ubuntu1.1 Ubuntu:6.06/dapper-security)
Conf libgtk2.0-common (2.8.20-0ubuntu1.1 Ubuntu:6.06/dapper-security)
Conf flashplugin-nonfree (9.0.31.0.1ubuntu1~dapper1 Ubuntu:6.06/dapper-backports)
Conf gtk2-engines-pixbuf (2.8.20-0ubuntu1.1 Ubuntu:6.06/dapper-security)
Conf libc6-dev (2.3.6-0ubuntu20.4 Ubuntu:6.06/dapper-updates)
Conf libconvert-asn1-perl (0.19-1 Ubuntu:6.06/dapper)
Conf libdigest-md4-perl (1.5-1 Ubuntu:6.06/dapper)
Conf libdigest-sha1-perl (2.10-1 Ubuntu:6.06/dapper)
Conf libnet-ssleay-perl (1.25-2build1 Ubuntu:6.06/dapper)
Conf libio-socket-ssl-perl (0.97-2build1 Ubuntu:6.06/dapper)
Conf libjcode-pm-perl (2.03-1 Ubuntu:6.06/dapper)
Conf libnet-ldap-perl (1:0.33-2 Ubuntu:6.06/dapper)
Conf libpq4 (8.1.8-0ubuntu6.06.1 Ubuntu:6.06/dapper-security)
Conf libunicode-map-perl (0.112-9 Ubuntu:6.06/dapper)
Conf libunicode-map8-perl (0.12-2 Ubuntu:6.06/dapper)
Conf libunicode-maputf8-perl (1.09-6 Ubuntu:6.06/dapper)
Conf linux-686 (2.6.15.26 Ubuntu:6.06/dapper-security)
Conf linux-restricted-modules-common (2.6.15.12-28.1 Ubuntu:6.06/dapper-security)
Conf python2.4-samba (3.0.22-1ubuntu3.2 Ubuntu:6.06/dapper-security)
Conf samba-common (3.0.22-1ubuntu3.2 Ubuntu:6.06/dapper-security)
Conf samba-doc (3.0.22-1ubuntu3.2 Ubuntu:6.06/dapper-security)
Conf smbclient (3.0.22-1ubuntu3.2 Ubuntu:6.06/dapper-security)
Conf libcrypt-smbhash-perl (0.12-1 Ubuntu:6.06/dapper)
Conf smbldap-tools (0.9.2-3 Ubuntu:6.06/dapper)
Conf synaptic (0.57.8ubuntu13 Ubuntu:6.06/dapper-updates)
Conf libsmbclient (3.0.22-1ubuntu3.2 Ubuntu:6.06/dapper-security)
bill2@ubuntu:~$ sudo apt-get remove --purge samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 27 not upgraded.
39 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113874 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
bill2@ubuntu:~$ apt-get install samba
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bill2@ubuntu:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
39 not fully installed or removed.
Need to get 2845kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba 3.0.22-1ubuntu3.2 [2845kB]
Fetched 2845kB in 10s (263kB/s)
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 113876 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nyinge on 2007-03-24
Hello check123,
I found this [thread]("http://ubuntuforums.org/showthread.php?p=2121155") for you.  It's very similar to your problem.  How does it go?

---

### Post by check123 on 2007-03-26
thanks again for your time.

i have now begun to get updates.  samba is still not quite right, however i dont use it much.

maybe the next overhaul it will fix it.

thanks again.

---

### Post by Tayeb on 2007-03-31
I have about the same problem,

```
sudo apt-get remove --purge samba --dry-run
```

I go this

[HTML]Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Purg samba [3.0.22-1ubuntu3.1]
[/HTML]

When I took off the " --dry-run" part
here is what I got

[HTML]Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking, 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148389 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
tayeb@tayeb-laptop:~$ sudo apt-get remove --purge samba --dry-run
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Purg samba [3.0.22-1ubuntu3.1]
tayeb@tayeb-laptop:~$
tayeb@tayeb-laptop:~$ sudo apt-get remove --purge samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking, 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148389 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

Can you please help, every time I try to do some update it tells me that I have a broken package.
Thanks

---

