---
title: "[SOLVED] Gimp upgrades problems.  Possible file system errors."
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by destroyingworld on 2007-10-16
I have been running gutsy on my laptop since July but for the past month I misplaced my power cord and have not kept pace with upgrades.  I finally found it and I started to try and catch up with the upgraded packages.  Upgrading GIMP failed.   I also tried to remove it without success.  Here is the result of `apt-get -f install`

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  xvnc4viewer xdg-user-dirs-gtk
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gimp libgimp2.0 libgnome-media0
Suggested packages:
  gimp-help-en gimp-help gimp-python libgimp-perl gimp-data-extras
Recommended packages:
  gimp-gnomevfs gimp-libcurl
The following packages will be upgraded:
  gimp libgimp2.0 libgnome-media0
3 upgraded, 0 newly installed, 0 to remove and 597 not upgraded.
1 not fully installed or removed.
Need to get 0B/4920kB of archives.
After unpacking 881kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 133733 files and directories currently installed.)
Preparing to replace gimp 2.3.18-1ubuntu2 (using .../gimp_2.4.0~rc3-1ubuntu7_i386.deb) ...
Unpacking replacement gimp ...
dpkg: error processing /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu7_i386.deb (--unpack):
 unable to create `./usr/share/doc/libgimp2.0/README.MIDI': Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libgimp2.0 2.3.18-1ubuntu2 (using .../libgimp2.0_2.4.0~rc3-1ubuntu7_i386.deb) ...
Unpacking replacement libgimp2.0 ...
dpkg: error processing /var/cache/apt/archives/libgimp2.0_2.4.0~rc3-1ubuntu7_i386.deb (--unpack):
 unable to stat `./usr/share/doc/libgimp2.0/README' (which I was about to install): Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libgnome-media0 2.18.0-2ubuntu3 (using .../libgnome-media0_2.20.1-0ubuntu1_i386.deb) ...
Unpacking replacement libgnome-media0 ...
dpkg: error processing /var/cache/apt/archives/libgnome-media0_2.20.1-0ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/share/doc/libgnome-media0' (which I was about to install): Permission denied
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu7_i386.deb
 /var/cache/apt/archives/libgimp2.0_2.4.0~rc3-1ubuntu7_i386.deb
 /var/cache/apt/archives/libgnome-media0_2.20.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

running ls on /usr/share/doc/libgimp2.0 is as follows

```

p:/usr/share/doc/libgimp2.0$ ls -la
total 50
drwxr-xr-x    2 root root   288 2007-07-18 14:04 .
drwxr-xr-x 1494 root root 51000 2007-10-15 01:41 ..
?---------    ? ?    ?        ?                ? AUTHORS
?---------    ? ?    ?        ?                ? changelog.Debian.gz
?---------    ? ?    ?        ?                ? changelog.gz
?---------    ? ?    ?        ?                ? copyright
?---------    ? ?    ?        ?                ? NEWS.gz
?---------    ? ?    ?        ?                ? README
?---------    ? ?    ?        ?                ? README.Debian
?---------    ? ?    ?        ?                ? TODO.Debian

```
with all files shown in red.

Attempts to remove the directory has the following result.

```

:/usr/share/doc$ sudo rm -rf libgimp2.0/
rm: cannot lstat `libgimp2.0//README': Permission denied

```

Also, when I attempted to upgrade, /usr/bin/gimp-remote-2.3 could not be removed.  Trying to ls the file results in:

```

ls -l gimp-remote-2.3* 
ls: gimp-remote-2.3: Permission denied

```

Trying to mv it results in

```

$ sudo mv gimp-remote-2.3 gimp-remote-2.3.old
mv: cannot stat `gimp-remote-2.3': Permission denied

```

My root partition is formatted with reiserfs.

Any ideas?

---

### Post by destroyingworld on 2007-10-16
Turns out it was due to filesystem errors.  I rebooted in recovery mode and remounted the root partition read-only and then ran reiserfsck
```
#mount -o ro,remount /dev/sda8 /
#reiserfsck
```

Busy upgrading now.

---

