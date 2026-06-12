---
title: "Upgrade from dapper to edgy: locale problems"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by WesleyWex on 2007-01-03
I was upgrading a xubuntu 6.06 to 6.10, following [this tutorial]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html") I found. Everything was fine until samba was upgraded.

This is what happened:
```
...
Preparing to replace sensible-mda 8.13.5-3ubuntu1.1 (using .../sensible-mda_8.13.8-2_i386.deb) ...
Unpacking replacement sensible-mda ...
Preparing to replace xinetd 1:2.3.14-0ubuntu1 (using .../xinetd_1%3a2.3.14-1_i386.deb) ...
Stopping internet superserver: xinetd.
Unpacking replacement xinetd ...
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've looked for many things.

export LC_ALL="en_US" does not work
edit /etc/environment does not work
can't install or reconfigure locale: obviously apt has dependencies broken

If I try to run "apt-get -f install", this is happens:
```
root@servidor:/home/wesley# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
859 not fully installed or removed.
Need to get 0B/2904kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US",
        LC_ALL = "en_US",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Preconfiguring packages ...
(Reading database ... 110661 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What do I do?

---

### Post by mikesignguy on 2007-01-04
got the same problem...please help

---

### Post by Sandlst on 2007-01-15
Have yall tried this?
[http://ubuntuforums.org/showthread.php?t=325102&highlight=locale+error]("http://ubuntuforums.org/showthread.php?t=325102&highlight=locale+error")

---

### Post by WesleyWex on 2007-03-19
First the samba problem was that the link it has created when installed was wrong. I was always wondering why it was not starting at boot, but never got to investigate.

I just removed and created a new link to it at /etc/rc2.d. It was redirecting to /samba, not ../init.d/samba.

Then I've mannually removed and installed samba again.

The locale problem was solved by doing this:

```
# locale-gen en_US.UTF-8
```
(I'm not sure if it was en_US or en_US.UTF-8)

Then just reconfigured locales.
```
# dpkg-reconfigure locales
```
This took a long time because now it rebuilt all locales.

Hope I've helped somebody. :)

---

