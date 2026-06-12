---
title: "problem with synaptic package"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by Rahmat on 2007-09-13
Hello everyone,

This is the message i got when i launch Synaptic package what should i do?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Pumalite on 2007-09-13
did you run: sudo dpkg --configure -a?

---

### Post by Rahmat on 2007-09-13
yes i did but didn't work.  This is the last 2 lines of errors i got from the terminal.

"dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer"

---

### Post by Pumalite on 2007-09-13
There are a couple of other thing you might try:

sudo dpkg --remove --force-remove-<packagename>

dpkg-divert --remove /usr/lib/<packagename>

sudo apt-get remove --purge <packagename>

You might want to look at this: [http://ubuntuforums.org/showthread.p...=force+removal](http://ubuntuforums.org/showthread.p...=force+removal)

---

### Post by Rahmat on 2007-09-13
i appreciate your quick response but i dont know which package to replace <packagename>.  Besides, when i try to install packages from the repository is still brin the same problem.

What next to be done pleaseeeeeeeeeeeee

---

### Post by Pumalite on 2007-09-13
Look at this thread and see if it helps you:
[http://ubuntuforums.org/showthread.php?t=549929](http://ubuntuforums.org/showthread.php?t=549929)

---

### Post by Rahmat on 2007-09-13
Thank you for the reply

I tried the procedure on the thread this what i got

admin@admin-desktop:~$ sudo apt-get clean
Password:
Sorry, try again.
Password:
admin@admin-desktop:~$ sudo apt-get autoremove
E: Invalid operation autoremove
admin@admin-desktop:~$ sudo apt-get clean
admin@admin-desktop:~$ su
Password:
root@admin-desktop:/home/admin# apt-get clean
root@admin-desktop:/home/admin# apt-get autoremove
E: Invalid operation autoremove
root@admin-desktop:/home/admin# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper/main Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 7B in 31s (0B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# apt-get install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# dpkg --configure -a
dpkg: status database area is locked by another process
root@admin-desktop:/home/admin# apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 276 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.admin@admin-desktop:~$ sudo apt-get clean
Password:
Sorry, try again.
Password:
admin@admin-desktop:~$ sudo apt-get autoremove
E: Invalid operation autoremove
admin@admin-desktop:~$ sudo apt-get clean
admin@admin-desktop:~$ su
Password:
root@admin-desktop:/home/admin# apt-get clean
root@admin-desktop:/home/admin# apt-get autoremove
E: Invalid operation autoremove
root@admin-desktop:/home/admin# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper/main Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 7B in 31s (0B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# apt-get install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# dpkg --configure -a
dpkg: status database area is locked by another process
root@admin-desktop:/home/admin# apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 276 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@admin-desktop:/home/admin# dpkg --configure -a
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
root@admin-desktop:/home/admin# rm launchpad-integration*
rm: cannot remove `launchpad-integration*': No such file or directory
root@admin-desktop:/home/admin#


    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@admin-desktop:/home/admin# dpkg --configure -a
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
root@admin-desktop:/home/admin# rm launchpad-integration*
rm: cannot remove `launchpad-integration*': No such file or directory
root@admin-desktop:/home/admin#


am sure u will understand it. expecting your reply soonest. thank you

---

### Post by sctech29169 on 2007-09-13
F-protec is an antivirus application that may have gotten an upgrade from F-prot, but not Ubuntu. 

"installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux"

FTP to the site and you will find under "pub" there is no linux directory if you log in anonymously.

There is your problem. If you linked to this from a webpage ... OOPS, the webmaster goofed. Send an email to them.

I had something like this happen. While you were doing command line entries, did you have synaptic PM open? If so, that would cause the lock to fail. If it still doesn't work and is not a "critical use" machine, try a shut down and restart. Even then, you will not be able to get F-prot until the link is fixed.

Rodney

---

### Post by Pumalite on 2007-09-13
> **Rahmat said:**
> Thank you for the reply

I tried the procedure on the thread this what i got

admin@admin-desktop:~$ sudo apt-get clean
Password:
Sorry, try again.
Password:
admin@admin-desktop:~$ sudo apt-get autoremove
E: Invalid operation autoremove
admin@admin-desktop:~$ sudo apt-get clean
admin@admin-desktop:~$ su
Password:
root@admin-desktop:/home/admin# apt-get clean
root@admin-desktop:/home/admin# apt-get autoremove
E: Invalid operation autoremove
root@admin-desktop:/home/admin# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper/main Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 7B in 31s (0B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# apt-get install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# dpkg --configure -a
dpkg: status database area is locked by another process
root@admin-desktop:/home/admin# apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 276 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.admin@admin-desktop:~$ sudo apt-get clean
Password:
Sorry, try again.
Password:
admin@admin-desktop:~$ sudo apt-get autoremove
E: Invalid operation autoremove
admin@admin-desktop:~$ sudo apt-get clean
admin@admin-desktop:~$ su
Password:
root@admin-desktop:/home/admin# apt-get clean
root@admin-desktop:/home/admin# apt-get autoremove
E: Invalid operation autoremove
root@admin-desktop:/home/admin# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://www.ubuntume.com](http://www.ubuntume.com) dapper/main Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 7B in 31s (0B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# apt-get install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@admin-desktop:/home/admin# dpkg --configure -a
dpkg: status database area is locked by another process
root@admin-desktop:/home/admin# apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 276 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@admin-desktop:/home/admin# dpkg --configure -a
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
root@admin-desktop:/home/admin# rm launchpad-integration*
rm: cannot remove `launchpad-integration*': No such file or directory
root@admin-desktop:/home/admin#


    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@admin-desktop:/home/admin# dpkg --configure -a
Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from [ftp://ftp.f-prot.com/pub/linux/](ftp://ftp.f-prot.com/pub/linux/)
No such directory `pub/linux/'.

    Download failed. Please make sure that
    your computer is connected to the Internet.
    If you see this error although you are
    connected, either the server is down or the
    download location has changed. In the latter
    case you can still download the files manually.
    Please file a bug report against
    f-prot-installer!
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
root@admin-desktop:/home/admin# rm launchpad-integration*
rm: cannot remove `launchpad-integration*': No such file or directory
root@admin-desktop:/home/admin#


am sure u will understand it. expecting your reply soonest. thank you

This I got from another thread (it's not mine), but has worked for others. Take a look at it and see if you can get something useful to you:

To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".
__________________

---

### Post by tgalati4 on 2007-09-13
Try removing it first:

>sudo apt-get remove f-prot

Then reinstall from the website, or don't reinstall.  Do you really need it?  Are you behind a cable or DSL model with a firewall?

---

### Post by Rahmat on 2007-09-17
Thank you very much for your contributions.

First i would like to add, from my understanding i think F-prot is a firewall.  But I still get my program installed with the error message.  My question is now "is there any implication for still bringing the error message and i still get my proram installed from the repository?"

I have tried the option of opening the "status file" in /var/lib/dpkg directory and i found out that the status is "install ok installed" without changing it but i tried to use "install reinstreq half-installed" maybe it would work but i could not save because is a read only file with no permission to save.

I av tried all the suggestion but it did not work and i would appreciate if i can get the email to mail to ftp link "ftp://ftp.f-prot.com/pub/linux/" cos i got error when i open the link.

Am not on DSL am on cable.

What should i do next?  Should i ignore it?  but it was never like that before now so i need your assistance please.

Thank you so much once again for your effort. am awaiting the solution.

---

### Post by matogrosso on 2007-09-19
"but i could not save because is a read only file with no permission to save"
Try using sudo mode to edit the file.

Something like:

>sudo gedit filename.ext

Where filename is name of the file you want to edit.

If that doesn't work, then you can take the radical step of becoming root. 
>su -

Maybe before that you need to define a root password:
> passwd root

Ubuntu developers don't like it and strongly advise people against creating root users. That is because "sudo" is just as good, but a lot safer. If you do decide to use root, please be very careful and remember to exit the root user after you've finished with what you were doing

> exit

As root you can write and/or delete ANY file in you system.

---

### Post by Rahmat on 2007-09-20
Hurray!


The error has finally been fixed

i followed this step
1. I Edit the /var/lib/dpkg/status file: and open the status file at the terminal with the super user priviledge.  I navigated to cd /var/lib/dpkg and then type "gedit status" it open the file and i searched for the package name i.e. f-prot, and manually change the status from "install reinstreq half-installed" to "install ok installed". 

This helped me and i have no error messages when installing packages.

Thank you so much.

---

### Post by otek on 2007-09-20
> **Rahmat said:**
> Hurray!


The error has finally been fixed

i followed this step
1. I Edit the /var/lib/dpkg/status file: and open the status file at the terminal with the super user priviledge.  I navigated to cd /var/lib/dpkg and then type "gedit status" it open the file and i searched for the package name i.e. f-prot, and manually change the status from "install reinstreq half-installed" to "install ok installed". 

This helped me and i have no error messages when installing packages.

Thank you so much.

Thank you so much, this saved my problem!

---

### Post by otek on 2007-09-20
It did NOT fix my problem :). I'm sorry for hijacking your thread but i have a really similiar problem. I can now access the update program and synaptic, but nothing gets installed, it downloads the packages, then just quits. And its not some setting, it only has to do with the deluge install..

---

