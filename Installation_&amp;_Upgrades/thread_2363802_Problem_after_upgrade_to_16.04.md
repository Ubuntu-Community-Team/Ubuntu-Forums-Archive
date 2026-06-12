---
title: "Problem after upgrade to 16.04"
date: 2017-06-14
forum: Installation &amp; Upgrades
---

### Post by satimis on 2017-06-14
Hi all,

Host - Ubuntu 16.04
VM - Ubuntu 16.04 upgrade from Ubuntu 14.04
Oracle VirtualBox

Each time running "sudo apt-get update ; sudo apt-get upgrade"

following warning will be display```

.....
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
Reading package lists... Done

```

Ran
&#10219; diff /etc/apt/apt.conf.d/50unattended-upgrades.ucf-old /etc/apt/apt.conf.d/50unattended-upgrades```

diff: /etc/apt/apt.conf.d/50unattended-upgrades.ucf-old: No such file or directory

```

Shall I run;```

sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist

```
to remove it?

Thanks

Regards
satimis

---

### Post by sccman on 2017-06-15
I would recommend keeping the file unless there is already another file to replace it. Unattended Upgrades involves security updates.

What is the output of:

```
ls -Alha /etc/apt/apt.conf.d
```

And:

```
cat /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
```

---

### Post by satimis on 2017-06-15
> **sccman said:**
> I would recommend keeping the file unless there is already another file to replace it. Unattended Upgrades involves security updates.

What is the output of:

```
ls -Alha /etc/apt/apt.conf.d
```

And:

```
cat /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
```

Hi,

&#10219; ls -Alha /etc/apt/apt.conf.d```

total 68K
drwxr-xr-x 2 root root 4.0K Jun 16 10:34 .
drwxr-xr-x 6 root root 4.0K Jan  4 11:15 ..
-rw-rw-r-- 1 root root   49 Apr 20  2015 00aptitude
-rw-rw-r-- 1 root root   40 Apr 20  2015 00trustcdrom
-rw-r--r-- 1 root root  769 Dec  9  2016 01autoremove
-r--r--r-- 1 root root 6.8K Jun 16 10:34 01autoremove-kernels
-rw-r--r-- 1 root root   42 Dec  9  2016 01-vendor-ubuntu
-rw-r--r-- 1 root root  129 Aug 22  2011 10periodic
-rw-r--r-- 1 root root  108 Aug 22  2011 15update-stamp
-rw-r--r-- 1 root root   85 Aug 22  2011 20archive
-rw-r--r-- 1 root root  243 Mar 11  2013 20dbus
-rw-r--r-- 1 root root 1.4K Apr 18  2016 50appstream
-rw-r--r-- 1 root root 2.3K Apr  3  2014 50unattended-upgrades
-rw-r--r-- 1 root root 2.6K May 19 23:47 50unattended-upgrades.ucf-dist
-rw-r--r-- 1 root root  182 Feb 23  2014 70debconf
-rw-r--r-- 1 root root  305 May 25  2016 99update-notifier

```

&#10219; cat /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist```

// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESM:${distro_codename}";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};

// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};

// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run 
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";

// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";

// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";

// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";

// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";

```

Thanks

Regards
satimis

---

### Post by sccman on 2017-06-16
Yeah you can remove the file. The file holds all the packages you'd update with apt-get upgrade in 14.04. 50unattended-upgrades without the extension is the new 16.04 upgrade file.

[https://askubuntu.com/questions/572976/what-to-do-now-update-just-after-install/573091#573091](https://askubuntu.com/questions/572976/what-to-do-now-update-just-after-install/573091#573091)

---

### Post by satimis on 2017-06-16
> **sccman said:**
> Yeah you can remove the file. The file holds all the packages you'd update with apt-get upgrade in 14.04. 50unattended-upgrades without the extension is the new 16.04 upgrade file.

[https://askubuntu.com/questions/572976/what-to-do-now-update-just-after-install/573091#573091](https://askubuntu.com/questions/572976/what-to-do-now-update-just-after-install/573091#573091)
I got it done.  Thanks

Regards
satimis

---

