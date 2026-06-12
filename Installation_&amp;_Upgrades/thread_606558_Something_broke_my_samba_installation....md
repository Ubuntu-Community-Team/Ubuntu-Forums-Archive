---
title: "Something broke my samba installation...?"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by Haise on 2007-11-08
This is on a 6.06 feisty server edition box.  I've been playing around with samba on one of my crappy computers that I use for various server purposes around the house, and after I restarted samba, it failed.  Thinking it was something weird, I just restarted the machine and logged back in.  I uninstalled it, reinstalled it, restarted, logged back in, still couldn't get it to work, uninstalled it, restarted it, and this is what I got when I tried to install it this time.

```


root@beowulf-3:/# apt-get install samba smbfs
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
Setting up samba (3.0.22-1ubuntu3.3) ...
/var/lib/dpkg/info/samba.postinst: line 23: /usr/share/debconf/confmodule: No such file or directory
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Haise on 2007-11-08
This has also affected the installation of pretty much anything else... the problem appears to be /usr/share/debconf/confmodule, but since I can't uninstall then reinstall debconf (it returns errors when I try to do so) what am I supposed to do...?

---

