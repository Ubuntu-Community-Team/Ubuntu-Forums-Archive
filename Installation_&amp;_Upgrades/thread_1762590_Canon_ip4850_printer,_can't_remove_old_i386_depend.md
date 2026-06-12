---
title: "Canon ip4850 printer, can't remove old i386 dependancies"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Groucho_Aus on 2011-05-19
I'm trying to get a Canon ip4850 printer installed on a fairly new upgrade to 64-bit Narhwal. I want to install the cnijfilter-common_3.40-1_amd64.deb and cnijfilter-ip4800series_3.40-1_amd64.deb packages, (;atest Canon drivers) but get the following error:

dpkg: error processing /home/name/cnijfilter-ip4800series-3.40-1-deb/packages/cnijfilter-common_3.40-1_amd64.deb (--install): 
 cnijfilter-common: 3.40-1 (Multi-Arch: no) is not co-installable with cnijfilter-common:i386 3.20-1 (Multi-Arch: no) which is currently installed 

How do I remove the old i386 3.20-1 arch? I've tried sudo apt-get remove, and this is the result.

name@name:~$ sudo apt-get remove cnijfilter-common
[sudo] password for name: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'cnijfilter-common' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.

Tried:

name@name:~$ sudo dpkg --purge cnijfilter-common
dpkg: warning: there's no installed package matching cnijfilter-common
name@name:~$ sudo dpkg --purge cnijfilter-common

Thanks in advance.

---

### Post by pspierce on 2011-05-31
Same issue.  Frustrating.

---

### Post by guillaumev on 2011-06-07
Hi,

Here is the solution (assuming you had an ip3600series installed before, but for other printers you can follow the same procedure):

```
sudo dpkg -r cnijfilter-ip3600series:i386
``````
sudo dpkg -r cnijfilter-common:i386
```

---

### Post by Groucho_Aus on 2011-06-09
Worked perfectly, thanks [guillaumev]("http://ubuntuforums.org/member.php?u=948448")

I love this place :)

---

