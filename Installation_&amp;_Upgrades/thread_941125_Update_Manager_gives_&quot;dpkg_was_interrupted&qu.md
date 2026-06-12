---
title: "Update Manager gives &quot;dpkg was interrupted&quot;"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by cathodion on 2008-10-07
Hi,  I'm new to Ubuntu and fairly new to Linux in general.  

The problem I'm having is that when I run Update Manager and click Install Updates (no matter which updates I have checked), it pops up a window with the messages:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct 
the problem. 
E: _cache->open() failed, please report.
```

When I open a terminal and do "sudo dpkg --configure -a" it gives me:

```
dpkg: parse error, in file `/var/lib/dpkg/updates/0009' near line 1:
 newline in field name `/.'

```

When I output that file's contents, this is what I get (including prompts):

```
dustin@dustin-laptop:~$ cat /var/lib/dpkg/updates/0009
/.
/lib
/lib/tls
/lib/tls/i686
/lib/tls/i686/cmov
/lib/tls/i686/cmov/ld-2.7.so
/lib/tls/i686/cmov/libanl-2.7.so
/lib/tls/i686/cmov/libBrokenLocale-2.7.so
/lib/tls/i686/cmov/libc-2.7.so
/lib/tls/i686/cmov/libcidn-2.7.so
/lib/tls/i686/cmov/libcrypt-2.7.so
/lib/tls/i686/cmov/libdl-2.7.so
/lib/tls/i686/cmov/libm-2.7.so
/lib/tls/i686/cmov/libmemusage.so
/lib/tls/i686/cmov/libnsl-2.7.so
/lib/tls/i686/cmov/libnss_compat-2.7.so
/lib/tls/i686/cmov/libnss_dns-2.7.so
/lib/tls/i686/cmov/libnss_files-2.7.so
/lib/tls/i686/cmov/libnss_hesiod-2.7.so
/lib/tls/i686/cmov/libnss_nis-2.7.so
/lib/tls/i686/cmov/libnss_nisplus-2.7.so
/lib/tls/i686/cmov/libpcprofile.so
/lib/tls/i686/cmov/libpthread-2.7.so
/lib/tls/i686/cmov/libresolv-2.7.so
/lib/tls/i686/cmov/librt-2.7.so
/lib/tls/i686/cmov/libSegFault.so
/lib/tls/i686/cmov/libthread_db-1.0.so
/lib/tls/i686/cmov/libutil-2.7.so
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libc6-i686
/usr/share/doc/libc6-i686/changelog.Debdustin@dustin-laptop:~$ 

```

Would the lack of a newline at the end of that file be a problem?  

A little background: I installed Wubi and first ran Update Manager while running Firefox and maybe Pidgin.  At some point the computer froze: no mouse movement or anything.  I did a hard reboot and thought nothing of it.  Since then I've gotten the dpkg error in Update Manager.  The only things I've installed are a couple plugins for Firefox: gnash and del.icio.us.

Any help is appreciated.

---

### Post by Partyboi2 on 2008-10-07
try 
```
sudo mv /var/lib/dpkg/updates/0009 /var/lib/dpkg/updates/0009.old
```
then try updating again.

---

### Post by cathodion on 2008-10-07
Thanks for your response, Partyboy2.  I tried what you suggested, and then I got the same error for the file 0011.  So I did the same thing to it, renaming it to 0011.old, but got a similar error for 0012 when I tried to update.  

So then I tried moving everything out of that directory into a new directory under my home directory (hopefully this wasn't a bad idea).  When I ran Update Manager after that, it told me I had a package that was broken, and gives the error: 

```
E: /var/cache/apt/archives/libc6-i686_2.7-10ubuntu4_i386.deb: files list file 
for package `language-pack-gnome-en' contains empty filename

```

At this point I noticed that when I hovered over the update icon it told me to look at Package Manager from the right-click menu, so I did that.  When I look at language-pack-gnome-en's installed files, it's got a list of files, and the last one looks like this:

```
/usr/share/locale-langpack/en_CA/LC_MESSAGES/epiphany.#!/bin/sh

set -e

if [ "$1" = "remove" ]; then
```

And the rest of a shell script is after that.  I'm guessing this is not correct.

Package Manager won't let me remove language-pack-gnome-en: it gives me the same error about containing an empty filename.

---

### Post by iaculallad on 2008-10-07
Try doing this on your terminal:

```
sudo rm /var/lib/dpkg/updates/*
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by cathodion on 2008-10-08
updates/ was already empty. "sudo apt-get update" had no errors.  "sudo apt-get upgrade" told me to try using -f, which I did.  It then gave me the same error about the empty filename.  Here is the full log:

```
dustin@dustin-laptop:~$ sudo rm /var/lib/dpkg-/updates/*
[sudo] password for dustin: 
rm: cannot remove `/var/lib/dpkg/updates/*': No such file or directory
dustin@dustin-laptop:~$ cd /var/lib/dpkg/updates
dustin@dustin-laptop:/var/lib/dpkg/updates$ cd ..
dustin@dustin-laptop:/var/lib/dpkg$ sudo rm ./updates
rm: cannot remove `./updates': Is a directory
dustin@dustin-laptop:/var/lib/dpkg$ sudo rm ./updates/*
rm: cannot remove `./updates/*': No such file or directory
dustin@dustin-laptop:/var/lib/dpkg$ ls updates
dustin@dustin-laptop:/var/lib/dpkg$ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Get:1 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Get:2 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Get:3 http://us.archive.ubuntu.com hardy-updates/main Packages [315kB]
Get:4 http://us.archive.ubuntu.com hardy-updates/restricted Packages [6636B]
Get:5 http://us.archive.ubuntu.com hardy-updates/main Sources [90.3kB]
Get:6 http://us.archive.ubuntu.com hardy-updates/restricted Sources [908B]
Get:7 http://us.archive.ubuntu.com hardy-updates/universe Packages [100kB]
Get:8 http://us.archive.ubuntu.com hardy-updates/universe Sources [26.7kB]
Get:9 http://us.archive.ubuntu.com hardy-updates/multiverse Packages [20.1kB]
Get:10 http://us.archive.ubuntu.com hardy-updates/multiverse Sources [2795B]
Fetched 621kB in 6s (99.3kB/s)                                                 
Reading package lists... Done
dustin@dustin-laptop:/var/lib/dpkg$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.7-10ubuntu3) but 2.7-10ubuntu4 is installed
E: Unmet dependencies. Try using -f.
dustin@dustin-laptop:/var/lib/dpkg$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6-i686
The following packages will be upgraded:
  libc6-i686
1 upgraded, 0 newly installed, 0 to remove and 124 not upgraded.
Need to get 0B/1243kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/libc6-i686_2.7-10ubuntu4_i386.deb (--unpack):
 files list file for package `language-pack-gnome-en' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-i686_2.7-10ubuntu4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
dustin@dustin-laptop:/var/lib/dpkg$ 


```

The crash icon also appeared at this point.

---

### Post by Partyboi2 on 2008-10-08
try reinstalling language-pack-gnome-en
```
sudo apt-get --reinstall install language-pack-gnome-en
``` If that does not work and it still complains about "files list file for package `language-pack-gnome-en' contains empty filename" try moving the  language-pack-gnome-en file out of the way then reinstall the package.
 ```
sudo mv /var/lib/dpkg/info/language-pack-gnome-en.list language-pack-gnome-en.list.old
``````
sudo apt-get --reinstall install language-pack-gnome-en
```

---

### Post by cathodion on 2008-10-08
That worked, thanks!

I did have to move the file out of place.  Also, I did "sudo apt-get -f install" when the output suggested it.

It complained briefly about the missing file, but I guess it was supposed to:

```
dpkg: serious warning: files list file for package `language-pack-gnome-en' missing, assuming package has no files currently installed.
95798 files and directories currently installed.)
Preparing to replace libc6-i686 2.7-10ubuntu3 (using .../libc6-i686_2.7-10ubuntu4_i386.deb) ...

```

After that the Update Manager updates successfully, including the language-pack-gnome-en package.

---

