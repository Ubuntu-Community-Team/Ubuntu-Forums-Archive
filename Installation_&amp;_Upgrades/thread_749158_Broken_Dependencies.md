---
title: "Broken Dependencies"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by anuban on 2008-04-08
I faced the Broken Dependencies error while doing a regular update today. Please help.
I have tried two methods mentioned in other threads but none work.
sudo apt-get install -f
sudo dpkg --configure -a
I still have the broken dependencies.
Attached is a grab of the error I am getting.
Please help...

---

### Post by jrib on 2008-04-08
Pastebin your sources.list and the output of 'apt-cache policy liblaunchpad-integration1'.  liblaunchpad-integration1 does not seem to be available in gutsy...

---

### Post by junkiepilot on 2008-04-08
I've got exactly the same error....how do I fix it?

Sudo apt-get install -f.......ends with the following errors

Since this problem evolution will no longer start.......surely this has borked quite a few machines?

rastallp@rastallp-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  liblaunchpad-integration1
The following NEW packages will be installed
  liblaunchpad-integration1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/17.7kB of archives.
After this operation, 172kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 100633 files and directories currently installed.)
Unpacking liblaunchpad-integration1 (from .../liblaunchpad-integration1_0.1.18_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb (--unpack):
 trying to overwrite `/usr/share/icons/hicolor/16x16/apps/lpi-bug.png', which is also in package liblaunchpad-integration0
Errors were encountered while processing:
 /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rastallp@rastallp-laptop:~$

---

### Post by junkiepilot on 2008-04-09
Bump

---

### Post by Peter09 on 2008-04-09
You must be using Hardy.

This is resolved in the next upgrades. Just update your packages again and it will be fixed. If you are using Hardy you can expect this to happen occasionally as it is still in development.

System->Administration->Updatemanager

This will allow you to do an update straight away.

PC

---

### Post by junkiepilot on 2008-04-09
I am using hardy and it's the updates that caused this issue.

Update Manager does not fix the issue as it will not install the update listed below.

---

### Post by Peter09 on 2008-04-09
I had this error yesterday. Just click through the upgrade manager boxes until you get to the CHECK button. Click that and it will go back to the repositories to check for new packages. Once its got those it will bring them down and resolve the problems.

p.s. don't try and install the broken stuff, just ignore it or cancel any requests that pop up to install it. Just get to the CHECK button without doing anything else.

PC

---

### Post by warp99 on 2008-04-09
> **junkiepilot said:**
> I've got exactly the same error....how do I fix it?

Sudo apt-get install -f.......ends with the following errors

Since this problem evolution will no longer start.......surely this has borked quite a few machines?

rastallp@rastallp-laptop:~$ sudo apt-get install -f

This is the wrong string. The correct string is:

```
sudo apt-get -f install
```
or use
```
sudo apt-get -f remove
```

From the man pages:
```
-f, --fix-broken
          Fix; attempt to correct a system with broken dependencies in place.
          This option, when used with install/remove, can omit any packages to
          permit APT to deduce a likely solution. Any Package that are
          specified must completely correct the problem. The option is
          sometimes necessary when running APT for the first time; APT itself
          does not allow broken package dependencies to exist on a system. It
          is possible that a system’s dependency structure can be so corrupt
          as to require manual intervention (which usually means using
          dselect(8) or dpkg --remove to eliminate some of the offending
          packages). Use of this option together with -m may produce an error
          in some situations. Configuration Item: APT::Get::Fix-Broken.

```

That will complete the install or if not remove the packages being installed.

---

### Post by junkiepilot on 2008-04-09
All fixed now.....thanks all!

---

