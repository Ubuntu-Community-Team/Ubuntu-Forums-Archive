---
title: "Samba installation package causing woe"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by sazu on 2006-07-27
Greetings all!

Quite simply, yesterday I wanted to share some files between my computers, and I wanted to install samba. Problem was that I had to delegate the task to someone else, and by the time I came back, it was installed but I was told that there were some weird errors. Well, things worked fine, and I started upgrading my system this morning. After the upgrade of compiz and compiz-gnome, it throws an error message saying that samba install can't be completed. I tried with:

```
sudo apt-get remove samba
```
AND
```
sudo apt-get -f remove samba
```

But all I get is:

```
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 95644 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am not such an expert in the packaging system of Debian/Ubuntu, so I better not start mastering around. Anyone has a thought on how to either fix the problem, or get rid of the conflicting package?

---

