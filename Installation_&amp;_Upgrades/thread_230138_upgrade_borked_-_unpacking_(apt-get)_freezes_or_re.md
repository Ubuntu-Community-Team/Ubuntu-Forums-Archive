---
title: "upgrade borked - unpacking (apt-get) freezes or reboots"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by bjelko on 2006-08-05
OK, so I recently upgraded from breezy to dapper.  I am a long time Gentoo user and have been installing Ubuntu (in particular Kubuntu) on various machines.  Overall I have been very impressed - thanks for the great work!

However, the upgrade to Dapper did not go very smoothly.  I followed the upgrade instructions.  Updated and upgraded all the breezy packages that were installed, then changed all occurrences of "breezy" in the the sources.list file to "dapper" ran "sudo apt-get update && sudo apt-get dist-upgrade" then things did not go well...

First problem was a kernel panic regarding modules during the "dist-upgrade".  Thankfully the machine booted to the console.  I was then able to run "sudo dpkg --configure -a" as instructed by apt...

This looked like everything was going well, packages were being upgraded and configured and it seemed to install correctly.  However, when I try to install anything now, I am being told by apt that:

```
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: wpasupplicant but it is not installed
E: Unmet dependencies. Try using -f.
```

When I run "apt-get -f install" I receive the following:

```
The following extra packages will be installed:
  sysklogd wpasupplicant
Suggested packages:
  libengine-pkcs11-openssl
The following NEW packages will be installed:
  wpasupplicant
The following packages will be upgraded:
  sysklogd
1 upgraded, 1 newly installed, 0 to remove and 455 not upgraded.
3 not fully installed or removed.
Need to get 0B/259kB of archives.
After unpacking 545kB of additional disk space will be used.
```

however when I run this, the PC either hangs or reboots itself when unpacking sysklogd (the first package being installed) and I cannot do anything else with apt-get unless I run the fix install first, but this keeps failing...

I ran dselect and it reports to me that sysklogd, klogd, and ubuntu-minimal are broken, however everything I try fails...  I even ran "dpkg -i /var/cache/apt/sysklogd..." to see if I could reinstall and it freezes the PC everytime while unpacking...

Any help or insight would be greatly appreciated...

---

### Post by bjelko on 2006-08-07
This is a follow up...

So ubuntu-minimal indicates that it depends on wpasupplicant, so I couldn't use apt-get or aptitude to install this given the error message above, so I opted to use "dpkg -i" to attempt an install of wpasupplicant.  This install was successful!

So, naturally, since sysklogd is the first package being installed during the fix, I tried to install sysklogd using "dpkg -i" as well.  Not so lucky, this caused the machine to reboot itself while unpacking.

When I check the Info on the sysklogd package the system reports sysklogd as being "partially installed"...  I cannot remove it, nor can I reinstall it without the same freeze or reboot problem.

So, I suspect the problem is with the combination of my system and the sysklogd package.  The kicker is, I cannot move on with the upgrade until this is resolved, any thoughts or suggestions would be greatly appreciated!

---

### Post by linear on 2006-08-07
My only suggestion: try working through the troubleshooting steps in [this thread]("http://www.ubuntuforums.org/showthread.php?t=186672"). You may need to clean up sources.list, then work through removing packages that have unmet dependencies.

---

