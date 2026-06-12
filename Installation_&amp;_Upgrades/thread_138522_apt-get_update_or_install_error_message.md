---
title: "apt-get update or install error message"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by bawhux on 2006-03-02
Hi....guy's i have a problem with apt-get update my kubuntu 5.10, there are the error message is :
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apt-spy
0 upgraded, 1 newly installed, 0 to remove and 89 not upgraded.
Need to get 27.7kB of archives.
After unpacking 184kB of additional disk space will be used.
Get:1 [http://ubuntu.ubaya.ac.id](http://ubuntu.ubaya.ac.id) breezy/universe apt-spy 3.1-13 [27.7kB]
Fetched 27.7kB in 3s (8295B/s)
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /disk in /etc/fstab or /etc/mtab
E: Problem executing scripts DPkg::Pre-Invoke 'fh-full'
E: Sub-process returned an error code
bawhux@d3b1an:~$
What's wrong with my setting.....please help me (newbie)
thx....

---

### Post by soonindallas on 2006-03-02
please post results of

```
sudo fdisk -l /dev/hda1
```

and

```
cat /etc/fstab
```

---

### Post by bawhux on 2006-03-02
Thank's about your reply :::
but this result is :
bawhux@d3b1an:~$ sudo apt-get install apt-spy
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apt-spy
0 upgraded, 1 newly installed, 0 to remove and 89 not upgraded.
Need to get 0B/27.7kB of archives.
After unpacking 184kB of additional disk space will be used.
mount: can't find /disk in /etc/fstab or /etc/mtab
E: Problem executing scripts DPkg::Pre-Invoke 'fh-full'
E: Sub-process returned an error code
bawhux@d3b1an:~$ 
what is wrong 
                                      :mad:

---

### Post by Xian on 2006-03-02
Why did you not supply the info that soonindallas asked for?? The first problem is with your /etc/fstab file. That particular error message is telling you to place a blank line at the end of that file. Do just that and then post back with the contents the file so it can be reviewed.

---

