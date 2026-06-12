---
title: "Having problems with apt-get upgrade"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Dragonuv on 2010-05-19
Whenever I type apt-get upgrade it gives me this:


```

root@vpstest:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  evolution-indicator language-pack-en python-apt xserver-common
  xserver-xorg-core
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2971kB of archives.
After this operation, 705kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
tar: ./md5sums: Cannot utime: Bad file descriptor
tar: ./control: Cannot utime: Bad file descriptor
tar: .: Cannot utime: Bad file descriptor
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a9.04+20090921_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
tar: ./postinst: Cannot utime: Bad file descriptor
tar: ./preinst: Cannot utime: Bad file descriptor
tar: ./prerm: Cannot utime: Bad file descriptor
tar: ./md5sums: Cannot utime: Bad file descriptor
tar: ./control: Cannot utime: Bad file descriptor
tar: .: Cannot utime: Bad file descriptor
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/python-apt_0.7.9~exp2ubuntu10.1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
tar: ./md5sums: Cannot utime: Bad file descriptor
tar: ./control: Cannot utime: Bad file descriptor
tar: .: Cannot utime: Bad file descriptor
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/xserver-common_2%3a1.6.0-0ubuntu14.2_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
tar: ./postinst: Cannot utimeNo apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         : Bad file descriptor
tar: ./preinst: Cannot utime: Bad file descriptor
tar: ./postrm: Cannot utime: Bad file descriptor
tar: ./conffiles: Cannot utime: Bad file descriptor
tar: ./md5sums: Cannot utime: Bad file descriptor
tar: ./control: Cannot utime: Bad file descriptor
tar: .: Cannot utime: Bad file descriptor
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.6.0-0ubuntu14.2_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
tar: ./postinst: Cannot utime: Bad file descriptor
tar: ./prerm: Cannot utime: Bad file descriptor
tar: ./postrm: Cannot utime: Bad file descriptor
tar: ./md5sums: Cannot utime: Bad file descriptor
tar: ./control: Cannot utime: Bad file descriptor
tar: .: Cannot utime: Bad file descriptor
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/evolution-indicator_0.1.13-0ubuntu1.1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a9.04+20090921_all.deb
 /var/cache/apt/archives/python-apt_0.7.9~exp2ubuntu10.1_amd64.deb
 /var/cache/apt/archives/xserver-common_2%3a1.6.0-0ubuntu14.2_all.deb
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.6.0-0ubuntu14.2_amd64.deb
 /var/cache/apt/archives/evolution-indicator_0.1.13-0ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```how can I fix this?
sudo apt-get install -f didn't work.

Thanks.

---

### Post by donovanh on 2010-05-25
I too have been suffering this issue, and cannot find a solution.

---

### Post by donovanh on 2010-05-25
Looking into it, it seems I need to install a newer version of "tar". However I haven't managed to work out how to.

---

### Post by vidkun on 2011-01-16
Not sure if you got this resolved, but I ran into the same thing trying to upgrade my server. Here is a solution that I found elsewhere that worked for me.

As a workaround, you can create a wrapper for tar that will add the --touch option:
  create a file named tar under /usr/local/sbin with the following content:
  > #!/bin/sh
exec /bin/tar --touch -"$@"  Do:
  > chmod +x /usr/local/sbin/tar  Now run aptitude dist-upgrade to continue the upgrade process. Delete this file after installation has completed.

---

### Post by flounder2 on 2011-12-15
Thanks vidkun. Your fix just worked for me and got me through an upgrade from karmic.
:D

---

