---
title: "adept claims all updates broken due to failing package"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by bluearcus on 2006-07-09
I've managed to get through a breezy->dapper upgrade without too much pain (principally because I knew where all the pain would be in advance... dist-upgrade, grub, X11), but now have one annoying gremlin with my nice new kubuntu desktop that I can't crack.

Any package actions in adept finish with an error report that the attempted action has failed. 

Looking with apt-get/dpkg at what's going on, the failure is in the mldonkey-server packages's install/uninstall scripts, and these are trying to be re-run on every package management action:

```
mike@skenfrith:/usr/share$ sudo apt-get remove mldonkey-server
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  mldonkey-server
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 8151kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 111580 files and directories currently installed.)
Removing mldonkey-server ...
Stopping MLDonkey: mlnetNo process in pidfile `/var/run/mlnet.pid' found running; none killed.
invoke-rc.d: initscript mldonkey-server, action "stop" failed.
dpkg: error processing mldonkey-server (--remove):
 subprocess pre-removal script returned error exit status 1
Starting MLDonkey: mlnetinstall: invalid option -- f
Try `install --help' for more information.
invoke-rc.d: initscript mldonkey-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mldonkey-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I really want to use the adept auto-update features, so would like to fix this.

Obviously, I've tried -r and --purge of the offedning package, and force options, but get the same error and it doesn't remove.

Any idea how I can fix the problem. Presumably I can remove the mldonkey-server package record somehow from package management, even if the package hasn't been properly uninstalled.

Regards,

Mike

---

### Post by lzap on 2006-07-20
Did you solve the problem? Same in Dapper Drake...

---

### Post by linear on 2006-07-20
The post [here]("http://www.ubuntuforums.org/showthread.php?t=186672") has good advice on dealing with broken dependencies.

---

### Post by jaalburquerque on 2006-07-21
I'm also running Dapper Drake (ubuntu 6.06, if I'm not mistaken) and ran into the same problem.  I found a discussion explaining that there is a problem with the /etc/init.d/mldonkey-server configuration file ([https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/42632]("https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/42632")).

The way I fixed this was by:
1) editing the /etc/init.d/mldonkey-sever file (as root)

2) finding the "install" line that reads:
install -o mldonkey -g mldoney -m 755 -f $PIDFILE

3) changing the above line so that it reads
install -o mldonkey -g **mldonkey** -m 755 -d $(dirname $PIDFILE)
(notice that "mldonkey" is mispelled after the -g originally).

After that I uninstalled it with synaptic.  I had to uninstall a second time before it was successful, but I was able to uninstall the misbehaving package.

I also had to remove the user and group "mldonkey" and change the ownership of /var/run back from "mldonkey:mldonkey" to "root:root" (as I think it should be) using:
$ sudo chown root:root /var/run

The discussion I referenced above states that there is a newer version that sould avoid the problems we have encountered, but I have not re-installed this package as of yet and am testing aMule (which does operate nicely).

Good luck everyone!

---

