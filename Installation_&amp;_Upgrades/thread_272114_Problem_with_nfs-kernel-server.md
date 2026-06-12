---
title: "Problem with nfs-kernel-server"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by El Groover on 2006-10-05
Hi. Not a total noob, but don't understand this problem and can't find similar on the forums. This is Dapper Server, and am trying really hard not to install a GUI.

All seems to be working fine, until I try and upgrade. Here is the command:

> sudo apt-get update && sudo apt-get upgrade

And this is the result: (Note: sorry for so much stuff, but have never used a forum before, and the instructions said be explicit and include all errors...)

> Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 60B in 0s (80B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-server
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up nfs-kernel-server (1.0.7-3ubuntu2) ...
 * Exporting directories for NFS kernel daemon...                        [ ok ]
 * Starting rpc nfsd...                                                  [ ok ]
 * Starting rpc mountd...                                                [fail]
invoke-rc.d: initscript nfs-kernel-server, action "start" failed.
dpkg: error processing nfs-kernel-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't install anything else either. Suggestions welcomed.

---

### Post by El Groover on 2006-10-10
Bump - either this is a really, really difficult one that on-one can solve, or it is so easy no-one has bothered to reply. In either case, someone please answer, or suggest where to look.

Thanks.

---

### Post by El Groover on 2006-10-13
Right, well it seems no-one knows about this, which is a bit odd. With a considerable amount of help from someone who knows his way round the command line, it *appears* to be something to do with an error in the upgrade script. If I run:

sudo /etc/init.d/nfs-kernel-server stop

followed by

sudo /etc/init.d/nfs-kernel-server start

or even

sudo /etc/init.d/nfs-kernel-server restart

everything runs fine. The implication is that Upgrade fails to stop nfs-kernel-server before trying to start it. Because it thinks it is already running, it fails. I'm surprised no-one else has come across this. And, as it is failing, is it stopping anything else upgrading properly?

---

### Post by cinderella on 2006-10-17
> **El Groover said:**
> Right, well it seems no-one knows about this, which is a bit odd. With a considerable amount of help from someone who knows his way round the command line, it *appears* to be something to do with an error in the upgrade script. If I run:

sudo /etc/init.d/nfs-kernel-server stop

followed by

sudo /etc/init.d/nfs-kernel-server start

or even

sudo /etc/init.d/nfs-kernel-server restart

everything runs fine. The implication is that Upgrade fails to stop nfs-kernel-server before trying to start it. Because it thinks it is already running, it fails. I'm surprised no-one else has come across this. And, as it is failing, is it stopping anything else upgrading properly?


hi unlike u i am a newbie and i have the same problem. itried out what u said and it worked but im not sure if this is all that supposed to "start" once i run the command:

```
[COLOR="Red"]bulletproof@Bulletproof:~$ sudo /etc/init.d/nfs-kernel-server start[/COLOR]
 * Exporting directories for NFS kernel daemon... exportfs: /etc/exports [3]: No 'sync' or 'async' option specified for export "146.230.192.49:/nfsshare".
  Assuming default behaviour ('sync').
  NOTE: this default has changed from previous versions
                                                                         [ ok ]
 * Starting rpc nfsd...                                                  [ ok ]
 * Starting rpc mountd...                                                [COLOR="Red"][fail][/COLOR]
bulletproof@Bulletproof:~$ sudo /etc/init.d/nfs-kernel-server stop
 * Stopping rpc mountd...                                                [ ok ]
 * Stopping rpc nfsd...                                                  [ ok ]
 * Unexporting directories for NFS kernel daemon...                      [ ok ]
[COLOR="Red"]bulletproof@Bulletproof:~$ sudo /etc/init.d/nfs-kernel-server start[/COLOR]
 * Exporting directories for NFS kernel daemon... exportfs: /etc/exports [3]: No 'sync' or 'async' option specified for export "146.230.192.49:/nfsshare".
  Assuming default behaviour ('sync').
  NOTE: this default has changed from previous versions
                                                                         [ ok ]
 * Starting rpc nfsd...                                                  [ ok ]
[COLOR="Red"] * Starting rpc mountd...                                                [ ok ][/COLOR]
bulletproof@Bulletproof:~$
```

---

### Post by El Groover on 2006-10-17
Hi there. Are you running Dapper Desktop? I am running Dapper Desktop on this m/c and don't have a problem, but then I'm not running nfs server on this one. I have the issue on Dapper Server edition, which is running the nfs server. Clearly, there is an issue with nfs, but my knowledge becomes sketchy when trying to solve a problem from the command line.

---

### Post by El Groover on 2006-10-22
OK, problem solved, but with a lot of help, and in no way do I claim knowledge or credit for this.

As previously surmised, the issue arises because nfs-kernel-server is running when the configure tires to run. Consequently, the script fails because it has not stopped nfs-kernel-server to allow the configure to take place.

The fix is to shutdown nfs-kernel-server:
> ~$ sudo /etc/init.d/nfs-kernel-server stop

Then run configure:
> ~$ sudo dpkg --configure nfs-kernel-server

Can't remember what this does, but am including it as it is part of the process:

> ~$ sudo dpkg -s nfs-kernel-server

Which results in:
Package: nfs-kernel-server
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 316
Maintainer: Anibal Monsalve Salazar <anibal@debian.org>
Architecture: i386
Source: nfs-utils
Version: 1:1.0.7-3ubuntu2
Replaces: knfs, nfs-server
Provides: knfs, nfs-server
Depends: nfs-common (>= 1:0.3.3-3), debconf (>= 1.0), sysvinit (>= 2.80-1), libc6 (>= 2.3.4-1), libcomerr2 (>= 1.33-3), libkrb53 (>= 1.4.2), libnfsidmap1, libwrap0, lsb-base (>= 1.3-9ubuntu3)
Conflicts: knfs, nfs-server
Conffiles:
 /etc/exports fa071681b8e7f4eff1d6f5c4f43bf1d8
 /etc/default/nfs-kernel-server 04755047c69d355d9d103c6f10017ec6
 /etc/init.d/nfs-kernel-server a7ffa77cccbd398da30e35c4abe52d27
Description: Kernel NFS server support
 Use this package if you have a fairly recent kernel (2.2.13 or better)
 and you want to use the kernel-mode NFS server.  The user-mode NFS
 server in the "nfs-user-server" package is slower but more featureful
 and easier to debug than the kernel-mode server.
 .
 Upstream: SourceForge project "nfs", CVS module nfs-utils.

Finally run upgrade:
> ~$ sudo apt-get upgrade

...and all is well.

---

### Post by rubbrduck on 2007-11-14
Thanks a bunch, mate.

That helped a lot :-)

---

