---
title: "Cannot uninstall lighttpd after Dapper-&gt;Edgy upgrade"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by kolanos on 2007-02-21
Hi,

I upgraded from Dapper to Edgy about a week ago and everything for the most part seems to be working. However since the lighttpd package has been complaining almost non-stop.  During the Dapper->Edgy upgrade process the lighttpd package did produce errors, perhaps something went wrong there. 

Apparently there's a version of lighttpd newer than the one I have installed, however the package currently installed on my system will not allow me to remove it, upgrade it, or anything else (that I've tried).

For example, when I attempt to run "sudo apt-get remove lighttpd" I get the following:

> 
kolanos@kolanos:~$ sudo apt-get remove lighttpd
Reading package lists... Done
Building dependency tree... Done
The following packages were automatically installed and are no longer required:
  lighttpd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  lighttpd
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 848kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 186327 files and directories currently installed.)
Removing lighttpd ...
 * Stopping web server lighttpd                                          [fail] 
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing lighttpd (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting web server lighttpd                                          [ ok ] 
Errors were encountered while processing:
 lighttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)


When I attempt an "apt-get upgrade lighttpd" it produces almost the exact same error message.

It seems to fail when attempting to stop the server, but when I run "sudo update-rc.d lighttpd defaults" it says it's already there, so the initscript should be able to stop it (I can stop/start it manually).

I've tried almost every other way to remove a package that I can think of (dpkg, aptitude, etc.), if anyone can shed some light on this I would really apprecaited it.

Is there any way during a "make install" to overwrite the existing copy of lighttpd instead of attempting to remove it? That might fix whatever is wrong with the initscript (assuming that is the problem). When I attempt to compile and install from the source it complains that lighttpd is already installed and that no action needs to be performed.

I may not have tried everything (I'm not an advanced Ubuntu user by any means), so if you have any ideas please let me know.

Thanks in advance!

---

### Post by kolanos on 2007-02-21
Although likely not a recommended course of action, canen's suggestion here did the trick:
[http://www.ubuntuforums.org/showthread.php?t=240580&highlight=lighttpd](http://www.ubuntuforums.org/showthread.php?t=240580&highlight=lighttpd)

---

