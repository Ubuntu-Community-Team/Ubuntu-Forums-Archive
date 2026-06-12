---
title: "Need b43 from ubuntu universe repository but cant go online"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by sbryant31 on 2010-11-26
Hey guys. I've got a compaq mini (the bestbuy doorbuster sale one). I'm trying to install ubuntu netbook remix on it, and I need to get the WIFI working. I have the following wireless card:

product BCM4313 802.11b/g LP-PHY

I've been searching around and apparently "B43" package is my ticket.

According to [https://help.ubuntu.com/community/WifiDocs/Driver/b43]("https://help.ubuntu.com/community/WifiDocs/Driver/b43"), I can download the "firmware" package from [http://archive.ubuntu.com/ubuntu/dists/]("http://archive.ubuntu.com/ubuntu/dists/"). So I downloaded "packages.gz" and "packages.bz2." and I stuck them on my thumb drive. 

But when I try to extract it, all I get is a 20mb file called "packages" and I don't understand how to use it. It's not a series of .deb files like I need. How do I find the b43 firmware package?

---

### Post by sbryant31 on 2010-11-26
I was getting weird errors when I installed it with the software manager. I uninstalled it and tried to install at the command line. I got this error:

Building initial module for 2.6.35-22-generic
/usr/sbin/dkms line 35: patch: command not found
Error! Application of patch 001-MODULE_LICENSE.patch failed.
check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build for more information.
traceback (most recent call last):
 File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report),'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/bcmwl -kernel-source.0.crash'

---

### Post by kerry_s on 2010-11-26
don't make more then 1 thread on the same subject.
see your other thread:
[http://ubuntuforums.org/showthread.php?p=10167718#post10167718](http://ubuntuforums.org/showthread.php?p=10167718#post10167718)

---

### Post by sbryant31 on 2010-11-26
I didnt make two threads, it was an error with the forums. I happened to be looking at this one when I responded to your posts

---

### Post by kerry_s on 2010-11-26
alright i'll see if a mod can fix it.

---

### Post by Elfy on 2010-11-26
> **sbryant31 said:**
> I didnt make two threads, it was an error with the forums. I happened to be looking at this one when I responded to your posts

> **kerry_s said:**
> alright i'll see if a mod can fix it.

Done.

@sbryant31 - in future you can use the Report button on the left pane and ask one of us to close one :)

---

