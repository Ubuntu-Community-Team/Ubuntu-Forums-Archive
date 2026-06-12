---
title: "GParted failing to install - perl-moduls error code 2..."
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by MrRiver on 2013-07-11
Hey guys,

New to Ubuntu and so far have been very much enjoying my experience with the OS. I have however run into an error when trying to install GParted and end up with this code:

```
$ sudo apt-get install gpartedReading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libgtkmm-2.4-1c2a
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils ntfsprogs kpartx dmraid gpart
The following NEW packages will be installed:
  gparted libgtkmm-2.4-1c2a
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/1,594 kB of archives.
After this operation, 6,955 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously unselected package libgtkmm-2.4-1c2a:amd64.
dpkg: unrecoverable fatal error, aborting:
 files list file for package `perl-modules' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I'm running Ubuntu 13.04 x64. The last thing I did before I began receiving this error when attempting to install gparted (and other apps) was modify OpenJDK to be able to associate .jar files with OpenJDK automatically when clicking on them using the guide found on askubuntu.com here: [http://askubuntu.com/questions/224463/how-do-i-reenable-opening-jar-files-by-double-clocking-on-them](http://askubuntu.com/questions/224463/how-do-i-reenable-opening-jar-files-by-double-clocking-on-them)

Would the modifications that I made cause the issue I am now having and should I revert the changes? (I have to admit I haven't actually tried this yet, but I will after posting) Or is this caused by something else entirely?

Thanks in advance for the help.

Cheers!
Joshua River

---

