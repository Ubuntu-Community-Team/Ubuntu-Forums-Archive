---
title: "Ubuntu Server 12.04 LTS - Samba Issues with removing"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by jamielsykes on 2013-11-04
Hi All,

I am currently having issues with trying to remove Samba from my Ubuntu Server box. 

```
sudo apt-get remove samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  samba
0 upgraded, 0 newly installed, 1 to remove and 63 not upgraded.
2 not fully installed or removed.
Need to get 0 B/235 kB of archives.
After this operation, 23.4 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing samba (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So upon receiving this error I have tried to update samba


```
sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2.8) but it is not going to be installed
         Depends: samba-common-bin
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I then tried to apt-get -f install

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba samba-common samba-common-bin
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools ctdb
The following NEW packages will be installed
  samba-common samba-common-bin
The following packages will be upgraded:
  samba
1 upgraded, 2 newly installed, 0 to remove and 63 not upgraded.
2 not fully installed or removed.
Need to get 0 B/14.8 MB of archives.
After this operation, 19.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 170022 files and directories currently installed.)
Preparing to replace procps 1:3.2.8-11ubuntu6 (using .../procps_1%3a3.2.8-11ubuntu6_amd64.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/procps not found.
dpkg: warning: subprocess old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/procps not found.
dpkg: error processing /var/cache/apt/archives/procps_1%3a3.2.8-11ubuntu6_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100
invoke-rc.d: unknown initscript, /etc/init.d/procps not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Selecting previously unselected package samba.
Preparing to replace samba 2:3.6.3-2ubuntu2.6 (using .../samba_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/nmbd not found.
dpkg: warning: subprocess old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/nmbd not found.
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100

+ . /usr/share/debconf/confmodule
+ [ !  ]
+ PERL_DL_NONLAZY=1
+ export PERL_DL_NONLAZY
+ [  ]
+ exec /usr/share/debconf/frontend /var/lib/dpkg/info/samba.postinst abort-upgrade 2:3.6.3-2ubuntu2.8
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ INITCONFFILE=/etc/default/samba
+ umask 022
+ [ -r /etc/default/samba ]
+ db_get samba/run_mode
+ _db_cmd GET samba/run_mode
+ _db_internal_IFS=     


+ IFS= 
+ printf %s\n GET samba/run_mode
+ IFS=     


+ IFS=
 read -r _db_internal_line
+ RET=daemons
+ return 0
+ RUN_MODE=daemons
+ TMPFILE=/etc/default/samba.dpkg-tmp
+ sed -e s/^[[:space:]]*RUN_MODE[[:space:]]*=.*/RUN_MODE="daemons"/
+ chmod a+r /etc/default/samba.dpkg-tmp
+ mv -f /etc/default/samba.dpkg-tmp /etc/default/samba
+ db_get samba/generate_smbpasswd
+ _db_cmd GET samba/generate_smbpasswd
+ _db_internal_IFS=     


+ IFS= 
+ printf %s\n GET samba/generate_smbpasswd
+ IFS=     


+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ GENERATE_SMBPASSWD=true
+ db_stop
+ echo STOP
+ umask 066
+ [ true = true -a ! -e /var/lib/samba/passdb.tdb -a ! -e /etc/samba/smbpasswd ]
+ getent/var/lib/dpkg/info/samba.postinst: 61: /var/lib/dpkg/info/samba.postinst: cannot create /etc/samba/smbpasswd: Directory nonexistent
+ mksmbpasswd
 passwd
+ pdbedit -i smbpasswd -e tdbsam -d 0
Can't load /etc/samba/smb.conf - run testparm to debug it
+ rm /etc/samba/smbpasswd
rm: cannot remove `/etc/samba/smbpasswd': No such file or directory
+ umask 022
+ dpkg --compare-versions 2:3.6.3-2ubuntu2.8 lt-nl 3.0.25b-2
+ dpkg --compare-versions 2:3.6.3-2ubuntu2.8 lt-nl 2:3.5.4~dfsg-2
+ [ -z 2:3.6.3-2ubuntu2.8 ]
+ [ daemons = daemons ]
+ update-inetd --disable netbios-ssn
+ getent group sambashare
+ [ ! -e /var/lib/samba/usershares ]
+ update-alternatives --install /usr/bin/smbstatus smbstatus /usr/bin/smbstatus.samba3 10 --slave /usr/share/man/man1/smbstatus.1.gz smbstatus.1.gz /usr/share/man/man1/smbstatus.samba3.1.gz
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
+ [ -e /etc/init/smbd.conf ]
+ invoke-rc.d smbd start
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
+ exit 100
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Selecting previously unselected package samba-common.
Unpacking samba-common (from .../samba-common_2%3a3.6.3-2ubuntu2.8_all.deb) ...
Selecting previously unselected package samba-common-bin.
Unpacking samba-common-bin (from .../samba-common-bin_2%3a3.6.3-2ubuntu2.8_amd64.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/procps_1%3a3.2.8-11ubuntu6_amd64.deb
 /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If anyone could offer some suggestions on a next step it would be greatly appreciated.

Thank you very much
Jamie

---

### Post by jamielsykes on 2013-11-05
To Solve the below issue I managed to do the following commands

```

touch [COLOR=#000000][FONT=Ubuntu Mono]/etc/init.d/procps
[/FONT][/COLOR]touch [COLOR=#000000][FONT=Ubuntu Mono]/etc/init.d/nmbd
[/FONT][/COLOR]touch [COLOR=#000000][FONT=Ubuntu Mono]/etc/init.d/smbd[/FONT][/COLOR]

```


Thanks
Jamie

---

