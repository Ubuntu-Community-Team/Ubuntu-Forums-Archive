---
title: "HELP! 10 hours to load Edgy/samba broken/install hangs"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Ambimom on 2006-10-26
How do I remove Edgy?  It took me 10 full hours to download; once it did, 10 of the packages were broken.  I followed the advice to load via terminal, but my samba is broken and I have no idea how to fix it.
> E: /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb: subprocess new pre-removal script returned error exit status 102

It won't boot normally and I am utterly disgusted.](*,)  I can't add or remove anything and my hardware doesn't load. What do I do!

If I download the iso and make a boot cd, can I fix this? How?

Please.

---

### Post by magicfab on 2006-10-26
It's possible the upgrade missed some of the packages. What happens if you apt-get update and apt-get upgrade again ? What are all the exact error messages ? Usually apt makes suggestions of recovery/repair commands in such situations.

---

### Post by Ambimom on 2006-10-27
I have tried it all: > sudo apt-get -f install> sudo dpkg --configure -a> sudo apt-get install --reinstall packagename> sudo apt-get -f install> sudo dpkg --configure -a


This is the result:

> Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 380 not upgraded.
Need to get 0B/2904kB of archives.
After unpacking 123kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 119758 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I either reinstall dapper, which worked! or fix this?

---

### Post by Ambimom on 2006-10-27
Combed through the forums.  Found someone else with exactly the same problem.  This was the fix:

> rm -f /etc/rc2.d/K09samba

Yippeee seems to have done the trick!

---

### Post by magicfab on 2006-10-27
Just FYI, I also searched the Launchpad.net site for related bugs, and sure enough there is one:
[https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082](https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082)

Check at the end of it, the workarounf is similar to what you did.

---

