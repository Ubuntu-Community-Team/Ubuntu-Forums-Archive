---
title: "apt-get apt-mirror Clearsigned file isn't valid, got 'NODATA'"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by haiko22012 on 2015-03-20
I have a local mirror running with apt-mirror. This was fine for more then a year, since some days I am getting this error


```
sudo apt-get update
Holen: 1 [http://192.168.0.100](http://192.168.0.100) trusty InRelease [246 B]
Holen: 2 [http://192.168.0.100](http://192.168.0.100) trusty-updates InRelease [246 B]
Holen: 3 [http://192.168.0.100](http://192.168.0.100) trusty-backports InRelease [246 B]
Holen: 4 [http://192.168.0.100](http://192.168.0.100) trusty-security InRelease [246 B]
Holen: 5 [http://192.168.0.100](http://192.168.0.100) trusty InRelease [246 B]litting up /var/lib/apt/lists/partial/192.168.0.100_ubuntu_dists_trusty_InRelease into data and signature failed
Ign [http://192.168.0.100](http://192.168.0.100) trusty InRelease
E: GPG-Fehler: [http://192.168.0.100](http://192.168.0.100) trusty InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)



```if I am deleting the InRelease file it works fine also with the normal Repos of Ubuntu for archive.ubuntu.com.
After refreshing apt-mirror InRelease is back in [http://192.168.0.100/ubuntu/dists/trusty/](http://192.168.0.100/ubuntu/dists/trusty/) and all the other Repo-mirros.
Than the error is back.

```
xxx@big100:/var/www/html/ubuntu/dists/trusty$ ls -la
insgesamt 57572
drwxr-xr-x 6 root root     4096 Mär 19 03:05 .
drwxr-xr-x 5 root root     4096 Mär 15 21:20 ..
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-amd64.bz2
-rw-r--r-- 1 root root 29389429 Mai  9  2014 Contents-amd64.gz
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-amd64.xz
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-i386.bz2
-rw-r--r-- 1 root root 29446732 Mai  9  2014 Contents-i386.gz
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-i386.xz
-rw-r--r-- 1 root root      246 Mär  2 02:46 InRelease
drwxr-xr-x 5 root root     4096 Mär 15 21:20 main
drwxr-xr-x 5 root root     4096 Mär 15 21:20 multiverse
-rw-r--r-- 1 root root    58512 Mai  8  2014 Release
-rw-r--r-- 1 root root      933 Mai  8  2014 Release.gpg
drwxr-xr-x 5 root root     4096 Mär 15 21:20 restricted
drwxr-xr-x 5 root root     4096 Mär 15 21:20 universe

```

I found this fix..
```
cat fixpackage 
#!/bin/bash
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update 
sudo apt-get dist-upgrade

```

but it did not help for me.
It seems that apt-get update does not downloads all the keys and Release files.


```
xxx@air199:/var/lib/apt/lists/partial$ ls
192.168.0.100_security_dists_trusty-security_InRelease
192.168.0.100_ubuntu_dists_trusty-backports_InRelease
192.168.0.100_ubuntu_dists_trusty_InRelease
192.168.0.100_ubuntu_dists_trusty-updates_InRelease

```

```
xxx@air199:/var/lib/apt/lists$ ls -la
insgesamt 12
drwxr-xr-x  3 root root 4096 Mär 19 15:32 .
drwxr-xr-x 10 root root 4096 Mär 19 16:12 ..
-rw-r-----  1 root root    0 Mär 19 15:32 lock
drwxr-xr-x  2 root root 4096 Mär 20 06:41 partial

```

I am getting the same thing from all client computer of apt-mirror.

Thanx Haiko

---

### Post by dino99 on 2015-03-20
how are the rights set for the mirror ? maybe some package upgrade have change them

---

### Post by haiko22012 on 2015-03-20
I deleted for this reason in the [http://192.168.0.100/ubuntu/dists/]("http://192.168.0.100/ubuntu/dists/trusty/") the trusty, trusty-backports and trusty-backups directories and made 

```
sudo apt-mirror
```

the mirror.list looks like this...

```
xxx@big100:~$ cat /etc/apt/mirror.list 
############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
#set limit_rate 50K
set nthreads 20
set _tilde 0
#
############# end config ##############
set cleanscript /var/spool/apt-mirror/var/clean.sh
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
#deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-proposed main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
#deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-proposed main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
#security
deb-i386 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
deb-amd64 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
#partner
deb-i386 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-amd64 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-amd64 [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu) trusty main
deb-amd64 [http://ppa.launchpad.net/mythbuntu/0.28/ubuntu](http://ppa.launchpad.net/mythbuntu/0.28/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/mythbuntu/0.28/ubuntu](http://ppa.launchpad.net/mythbuntu/0.28/ubuntu) trusty main
#extras
deb-amd64 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-i386 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
#sunflower
deb-i386 [http://ppa.launchpad.net/atareao/sunflower/ubuntu](http://ppa.launchpad.net/atareao/sunflower/ubuntu) trusty main
deb-amd64 [http://ppa.launchpad.net/atareao/sunflower/ubuntu](http://ppa.launchpad.net/atareao/sunflower/ubuntu) trusty main
#vbox
deb-i386 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib
deb-amd64 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib
#silver
deb-amd64 [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
deb-amd64 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu) trusty main
deb-amd64 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
deb-amd64 [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) trusty main
deb-amd64 [http://dl.google.com/linux/musicmanager/deb/](http://dl.google.com/linux/musicmanager/deb/) stable main
deb-i386 [http://dl.google.com/linux/musicmanager/deb/](http://dl.google.com/linux/musicmanager/deb/) stable main
deb-amd64 [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
deb-i386 [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
deb-amd64 [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) trusty main
deb-amd64 [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu) trusty main
deb-i386 [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu) trusty main


clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
clean [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)
clean [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
clean [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)
clean [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu)
clean [http://ppa.launchpad.net/mythbuntu/0.28/ubuntu](http://ppa.launchpad.net/mythbuntu/0.28/ubuntu)
clean [http://ppa.launchpad.net/atareao/sunflower/ubuntu](http://ppa.launchpad.net/atareao/sunflower/ubuntu)
clean [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)
clean [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu)
clean [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu)
clean [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu)
clean [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu)
clean [http://dl.google.com/linux/musicmanager/deb/](http://dl.google.com/linux/musicmanager/deb/)
clean [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/)
clean [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu)
clean [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu)
```

---

### Post by haiko22012 on 2015-03-20
I can download all fies by wget or browser.

```
xxx@big100:/var/www$ ls -la
insgesamt 12
drwxr-xr-x  3 root     root     4096 Dez  5 11:15 .
drwxr-xr-x 13 root     root     4096 Dez  5 11:15 ..
drwxr-xr-x  2 www-data www-data 4096 Feb 17 01:28 html

```

```
xxx@big100:/var/www/html$ ls -la
insgesamt 56
drwxr-xr-x 2 www-data www-data 4096 Feb 17 01:28 .
drwxr-xr-x 3 root     root     4096 Dez  5 11:15 ..
lrwxrwxrwx 1 www-data www-data   58 Dez  5 11:22 canonical -> /var/spool/apt-mirror/mirror/archive.canonical.com/ubuntu/
lrwxrwxrwx 1 www-data www-data   69 Jan 18 15:45 diesch -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/diesch/testing/ubuntu/
lrwxrwxrwx 1 www-data www-data   54 Feb 17 01:28 extras -> /var/spool/apt-mirror/mirror/extras.ubuntu.com/ubuntu/
lrwxrwxrwx 1 www-data www-data   74 Jan  2 22:47 mc3man -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/mc3man/trusty-media/ubuntu/
lrwxrwxrwx 1 www-data www-data   66 Jan 18 15:42 musicmanager -> /var/spool/apt-mirror/mirror/dl.google.com/linux/musicmanager/deb/
lrwxrwxrwx 1 www-data www-data   69 Dez  5 12:43 mythbuntu_0.27 -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/mythbuntu/0.27/ubuntu/
lrwxrwxrwx 1 www-data www-data   69 Jan  4 17:30 mythbuntu_0.28 -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/mythbuntu/0.28/ubuntu/
lrwxrwxrwx 1 www-data www-data   70 Jan  2 22:47 noobslab -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/noobslab/themes/ubuntu/
lrwxrwxrwx 1 www-data www-data   71 Dez 15 16:05 pipelight -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/pipelight/stable/ubuntu/
lrwxrwxrwx 1 www-data www-data   56 Dez  5 12:38 security -> /var/spool/apt-mirror/mirror/security.ubuntu.com/ubuntu/
lrwxrwxrwx 1 www-data www-data   72 Dez  5 12:40 sunflower -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/atareao/sunflower/ubuntu/
lrwxrwxrwx 1 www-data www-data   64 Jan 18 15:43 talkplugin -> /var/spool/apt-mirror/mirror/dl.google.com/linux/talkplugin/deb/
lrwxrwxrwx 1 www-data www-data   69 Jan 18 15:47 tiheum -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/tiheum/equinox/ubuntu/
lrwxrwxrwx 1 www-data www-data   68 Feb 11 18:49 tlp -> /var/spool/apt-mirror/mirror/ppa.launchpad.net/linrunner/tlp/ubuntu/
lrwxrwxrwx 1 www-data www-data   55 Dez  5 11:21 ubuntu -> /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/
lrwxrwxrwx 1 www-data www-data   71 Dez  5 12:35 vbox -> /var/spool/apt-mirror/mirror/download.virtualbox.org/virtualbox/debian/

```

```
xxx@big100:/var/www/html/ubuntu/dists/trusty$ ls -la
insgesamt 57572
drwxr-xr-x 6 root root     4096 Mär 19 03:05 .
drwxr-xr-x 5 root root     4096 Mär 15 21:20 ..
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-amd64.bz2
-rw-r--r-- 1 root root 29389429 Mai  9  2014 Contents-amd64.gz
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-amd64.xz
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-i386.bz2
-rw-r--r-- 1 root root 29446732 Mai  9  2014 Contents-i386.gz
-rw-r--r-- 1 root root      246 Mär  2 02:46 Contents-i386.xz
-rw-r--r-- 1 root root      246 Mär  2 02:46 InRelease
drwxr-xr-x 5 root root     4096 Mär 15 21:20 main
drwxr-xr-x 5 root root     4096 Mär 15 21:20 multiverse
-rw-r--r-- 1 root root    58512 Mai  8  2014 Release
-rw-r--r-- 1 root root      933 Mai  8  2014 Release.gpg
drwxr-xr-x 5 root root     4096 Mär 15 21:20 restricted
drwxr-xr-x 5 root root     4096 Mär 15 21:20 universe
```

---

### Post by haiko22012 on 2015-03-20
finally I modified /usr/bin/apt-mirror

# add_url_to_download( $url . "InRelease" );

in two lines. The Inrelease file disappeared in the mirror.

---

### Post by Spency on 2016-03-05
> **haiko22012 said:**
> finally I modified /usr/bin/apt-mirror

# add_url_to_download( $url . "InRelease" );

in two lines. The Inrelease file disappeared in the mirror.

This worked for me. After making your modifications, I was able to successfully run apt-get update && apt-get upgrade on the computer with the InRelease nodata issue. 
Afterwards, I reversed the changes in /usr/bin/apt-mirror, allowed apt-mirror to repopulate the InRelease files, and then ran an update again on the same computer to see if the issue persisted - it seems the issue was completely resolved during the upgrade.

---

### Post by oldos2er on 2016-03-05
Old thread closed.

---

