---
title: "libkrb5.so.26 problems"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by sabhain on 2016-02-28
Hi everyone,

I'm recovering from larger system stability issues, documented here:

[http://ubuntuforums.org/showthread.php?t=2315206&p=13447057#post13447057]("http://ubuntuforums.org/showthread.php?t=2315206&p=13447057#post13447057")

One of the last things is to fix an installation of minecraft that has always worked.  When I attempt a reconfigure or remove / reinstall, I get the following:

```
sudo apt-get install minecraft-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  minecraft-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/9,334 B of archives.
After this operation, 156 kB of additional disk space will be used.
Selecting previously unselected package minecraft-installer.
(Reading database ... 542868 files and directories currently installed.)
Preparing to unpack .../minecraft-installer_0.1+r12~ubuntu14.04.1_amd64.deb ...
Unpacking minecraft-installer (0.1+r12~ubuntu14.04.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up minecraft-installer (0.1+r12~ubuntu14.04.1) ...
curl: error while loading shared libraries: libkrb5.so.26: cannot open shared object file: No such file or directory
chmod: cannot access ‘/usr/share/minecraft’: No such file or directory
chmod: cannot access ‘/usr/share/minecraft/minecraft.jar’: No such file or directory
dpkg: error processing package minecraft-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 minecraft-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've done my research and know that libkrb5.so.26 is provided by package: libkrb5-26-heimdal

I have that installed.  I have done a reconfigure to be sure it is installed correctly.  However, despite all the package information which indicates that libkrb5-26-heimdal provides libkrb.so.26, the object file does NOT exist in my system.  I'm not sure what to do to force it to be there, but both with reconfigures and removal / install .. libkrb5.so.26 doesn't appear, and then the above installation which relies on it fails.

What am I missing here?  I'm not sure if I should forcibly get a binary of libkrb5.so.26 and drop it in the required location?  Or symlink something else?

Any suggestions or recommendations are appreciated.

Thanks!

---

### Post by sabhain on 2016-02-28
Hi,

Solved this by downloading the package from launchpad.net and reinstalling using dpkg.

---

