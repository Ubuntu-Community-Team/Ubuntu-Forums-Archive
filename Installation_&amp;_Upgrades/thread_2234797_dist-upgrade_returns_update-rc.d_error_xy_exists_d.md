---
title: "dist-upgrade returns update-rc.d error: xy exists during rc.d purge (use -f to force)"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by Rocketeer on 2014-07-17
```

sudo dist-upgrade
sudo: dist-upgrade: command not found
tristan@rocketserver:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  plexmediaserver
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
44 not fully installed or removed.
Need to get 0 B/66.8 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously unselected package plexmediaserver.
(Reading database ... 143502 files and directories currently installed.)
Preparing to replace plexmediaserver 0.9.9.10.458-008ea34-debian (using .../plexmediaserver_0.9.9.12.504-3e7f93c-debian_amd64.deb) ...
Killing Plex Media Server: done
update-rc.d: /etc/init.d/plexmediaserver exists during rc.d purge (use -f to force)
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Killing Plex Media Server: done
update-rc.d: /etc/init.d/plexmediaserver exists during rc.d purge (use -f to force)
dpkg: error processing /var/cache/apt/archives/plexmediaserver_0.9.9.12.504-3e7f93c-debian_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/plexmediaserver_0.9.9.12.504-3e7f93c-debian_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I already tried to "force" and "purge" things, but without luck.

---

### Post by ian-weisser on 2014-07-17
Plex is not in the Ubuntu repositories.
You should tell the maintainer of wherever you get plex from that their package's pre-removal script is broken.

The error message is quite clear:
```
update-rc.d: /etc/init.d/plexmediaserver exists during rc.d purge (use -f to force)
```

It means that you must manually delete /etc/init.d/plexmediaserver until the maintainer fixes the package's pre-removal script.

---

### Post by Rocketeer on 2014-07-19
Yes, it seems so. I tried to manually install the package (downloaded from the original website) via dpkg and it worked flawlessly (however it asked, if I want to keep or overwrite a config file). Thanks for the answer though!

---

