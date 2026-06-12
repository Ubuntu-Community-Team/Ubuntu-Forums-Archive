---
title: "E: Internal Error, Could not perform immediate configuration (2) on libattr1"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by midhund on 2010-03-27
Hi, 
  I am working with Ubuntu latest version. While installing via **apt-get install** i tried to abort that by pressing **Ctrl+Z**. It terminate successfully ;). But next time when i tried to use apt-get, i got some error "lock" and "temporally unavailable" something like that and[FONT=monospace]
[/FONT]
**[FONT=monospace] [/FONT]I unfortunately i delete the /var/lib/dkpg folder.**


after that i cant install anything from apt-get, getting an error.
  ```
E: Internal Error, Could not perform immediate configuration (2) on libattr1
```  so how can i solve this issue?
  Actual Error:
  ```
mittu@tutorboy:~$ sudo apt-get install htmldoc
[sudo] password for mittu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adduser apt apt-utils base-files base-passwd ca-certificates consolekit coreutils dbus debconf debconf-i18n debianutils defoma dpkg e2fslibs e2fsprogs
  file findutils fontconfig-config gawk gcc-4.4-base gnupg gpgv htmldoc-common ifupdown initscripts insserv libacl1 libattr1 libblkid1 libbz2-1.0 libc-bin

  libc6 libc6-i686 libck-connector0 libcomerr2 libcurl
      perl perl-base perl-modules psmisc readline-common sed sgml-base shared-mime-info sysv-rc sysvinit-utils ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
      tzdata ubuntu-keyring ucf upstart uuid-runtime whiptail x11-common xml-core zlib1g
    0 upgraded, 141 newly installed, 0 to remove and 0 not upgraded.
    Need to get 0B/58.6MB of archives.
    After this operation, 217MB of additional disk space will be used.
    Do you want to continue [Y/n]? y
    E: Internal Error, Could not perform immediate configuration (2) on libattr1
```

---

### Post by tom4everitt on 2010-03-27
Sorry dude, but you deleted a systems folder probably containing important info. If you want you can try to recreate it:

sudo mkdir /var/lib/dpkg

and try again to see if the system can restore it someway, but I doubt it.


What happens when you press ctrl+z is that you STOP (or pause) the process, you don't terminate it. You can start a stopped process again with 

fg %N  (or bg %N to run it in background)

where N is the number of the job, which you can find with the 'jobs' command.

To kill a process you do ctrl+c, although I wouldn't recommend killing apt processes, since it may corrupt your system.


Anyway, I'm afraid you will have to reinstall your system to fix this :)

---

### Post by biowee on 2010-04-19
The package of "libattr1" was in errors from the repository. You should download the package from the correct repository site and then install it. Or you should edit the repository site without any errors into your sources.list.

Finally, update and install packages again.

---

