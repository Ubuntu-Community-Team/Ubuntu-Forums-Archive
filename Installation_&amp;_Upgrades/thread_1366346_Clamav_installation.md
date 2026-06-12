---
title: "Clamav installation"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by jmlynn on 2009-12-28
Hi,

I used the Snaptic Package Manager to install Clamav, first without selecting the daemon, then add that after it failed to execute in command line:
root@mylinux:~# freshclam

I will get the following error: 
"freshclam: error while loading shared libraries: libclamav.so.6: cannot open shared object file: Permission denied"

Any idea?

Jeff

---

### Post by phillw on 2009-12-28
Hi,

if you didn't start the daemon, which is what freshclam is for - you can start it manually like this.
```
              freshclam -d -c 2

```

       This will run as a daemon and check 2 times per day for new database:
IMHO, It's easier to do full clamav install & let it look after it (one less thing to remember to do !!)

Regards,

Phill.

---

### Post by jmlynn on 2009-12-29
I did that, but didn't see anything visual after the install.  No added menu items anywhere that I can see, or do a manual click to invoke scanning as adhoc.

Here are the installed info:

jmlynn@Tecra-ubuntu:~$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libosip2-4 libpt-1.10.10-plugins-alsa libpt-1.10.10 libopal3.6.4
  libopenh323-1.18.0 libpt2.6.4-plugins libpt2.6.4 libexosip2-4
  libmediastreamer0 libpt-1.10.10-plugins-v4l libreadline5 libortp8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  clamav-base clamav-freshclam libclamav6
Suggested packages:
  clamav-docs libclamunrar6
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav6
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.2MB of archives.
After this operation, 26.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libclamav6.
(Reading database ... 122334 files and directories currently installed.)
Unpacking libclamav6 (from .../libclamav6_0.95.3+dfsg-1ubuntu0.09.10_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.95.3+dfsg-1ubuntu0.09.10_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.10_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.95.3+dfsg-1ubuntu0.09.10_i386.deb) ...
Processing triggers for man-db ...
/usr/bin/mandb: error while loading shared libraries: libgdbm.so.3: cannot open shared object file: Permission denied
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libclamav6 (0.95.3+dfsg-1ubuntu0.09.10) ...

Setting up clamav-base (0.95.3+dfsg-1ubuntu0.09.10) ...

Setting up clamav-freshclam (0.95.3+dfsg-1ubuntu0.09.10) ...
Replacing config file /etc/clamav/freshclam.conf with new version
 * Starting ClamAV virus database updater freshclam                      [ OK ] 

Setting up clamav (0.95.3+dfsg-1ubuntu0.09.10) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jmlynn@tecra-ubuntu:~$ 

Any idea?

Jeff

---

### Post by jmlynn on 2009-12-29
I found the doc on how to scan: #sudo clamscan -r /home

But I cannot run freshclam to update definitions

Jeff

---

### Post by jmlynn on 2009-12-29
when I ran freshclam:
#sudo freshclam

I got the following error:
freshclam: error while loading shared libraries: libclamav.so.6: cannot open shared object file: Permission denied

From what I gather, libclamav.so.6 is located in /usr/lib

Jeff

---

