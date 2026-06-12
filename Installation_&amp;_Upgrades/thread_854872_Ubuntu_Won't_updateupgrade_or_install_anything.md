---
title: "Ubuntu Won't update/upgrade or install anything"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by mamut0o1 on 2008-07-09
Hello; I recently did an upgrade to my box and since then I lost my sound and what's worse I can not do an update or upgrade without getting the following 
message: E: Sub-process /usr/bin/dpkg returned an error code (100)

can any1 please help me before I light this thing up.
thanks

 Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             18761980   3780028  14028896  22% /
varrun                  127992       168    127824   1% /var/run
varlock                 127992         0    127992   0% /var/lock
udev                    127992        60    127932   1% /dev
devshm                  127992         0    127992   0% /dev/shm
lrm                     127992     34696     93296  28% /lib/modules/2.6.22-14-generic/volatile

I'm not running out of space.

---

### Post by Partyboi2 on 2008-07-10
We need more of the error message. Can you open a terminal and post the output to
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by mamut0o1 on 2008-07-10
> **Partyboi2 said:**
> We need more of the error message. Can you open a terminal and post the output to
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
Hello Thank you for taking the time to read my post; This is the output when I try sudo apt-get upgrade:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  procmail sensible-mda
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  ssl-cert
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-gnome-support libbind9-30 libdns32
  libisc32 libisccc30 libisccfg30 liblwres30 libpurple0 libsmbclient pidgin
  pidgin-data samba samba-common smbclient swat
18 upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0B/27.0MB of archives.
After unpacking 631kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
root@mamut-desktop:/home/mamut#

please let me know what you think.
thanks!

---

### Post by Partyboi2 on 2008-07-10
Is dpkg still installed? Maybe it is corrupt or missing.
```
dpkg -l |grep dpkg
```

---

### Post by mamut0o1 on 2008-07-14
This is what I got:
The program 'dpkg' is currently not installed.  To run 'dpkg' please ask your administrator to install the package 'dpkg'
bash: dpkg: command not found

then I did apt-get install dpkg and this is what I get;
oot@mamut-desktop:/home/mamut# apt-get install dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg is already the newest version.
The following packages will be REMOVED:
  procmail sensible-mda
0 upgraded, 0 newly installed, 2 to remove and 22 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 647kB disk space will be freed.
Do you want to continue [Y/n]? y
E: Sub-process /usr/bin/dpkg returned an error code (100)
root@mamut-desktop:/home/mamut# 

I cant get any further.

---

### Post by Partyboi2 on 2008-07-15
try
```
sudo apt-get -f install
``` then try installing the package, but I think you  need dpkg installed to install debs so you may need to [[COLOR=Blue]compile[/COLOR]]("http://www.tuxfiles.org/linuxhelp/softinstall.html") the package from [[COLOR=Blue]source [/COLOR]]("http://packages.ubuntu.com/search?keywords=dpkg&searchon=names&suite=all&section=all")or if you have the dpkg-deb package installed you could try following Post #10 from [URL="http://ubuntuforums.org/showthread.php?t=103087"][COLOR=Blue]here[/COLOR]
[/URL]

---

### Post by mamut0o1 on 2008-07-15
Hello; Thanks for your help; I tried forcing it and that didn't work so I'm going to compile the package from source, could you point me at the right direction on which source should I download?

thanks again for all your help.

---

### Post by Partyboi2 on 2008-07-15
If you are using hardy use [[COLOR=Blue]this[/COLOR]]("http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.16.6ubuntu3.tar.gz") one

---

### Post by mamut0o1 on 2008-07-23
Hello Thanks for your help; I spent so much time on this problem I decided to re-install ubuntu. That took care of it =)

thanks

---

### Post by TimSylvester on 2010-03-27
Looks like it's too late for you, but I had this same problem.  While running a "dist-upgrade" I got a dpkg error ("Sub-process /usr/bin/dpkg returned an error code (100)") and no installations or upgrades would work after that.  

Eventually, I discovered this:

```
/tmp/dpkg$ ls -l /usr/bin/dpkg*
---------- 1 root root 391920 2010-03-10 17:32 /usr/bin/dpkg
-rwxr-xr-x 1 root root   7105 2009-09-20 01:23 /usr/bin/dpkg-architecture
-rwxr-xr-x 1 root root  16261 2009-09-20 01:23 /usr/bin/dpkg-buildpackage
...
```In other words, my /usr/bin/dpkg had been cleared of all access rights for everyone by some part of the upgrade process.  After running:

```
sudo chmod 755 /usr/bin/dpkg
```I was able to "sudo apt-get upgrade dpkg" successfully.

---

