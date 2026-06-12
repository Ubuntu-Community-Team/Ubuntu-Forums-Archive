---
title: "Help Me With this error Please"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by Bloodhawlk on 2012-01-17
root@bt:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  nmap
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/3,596kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5091 package 'magictree':
 error in Version string 'r1492-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 14777 package 'udptunnel':
 error in Version string 'r16-bt2': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 18694 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 21239 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 35244 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 39661 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
dpkg: error processing /var/cache/apt/archives/nmap_5.61-bt1_amd64.deb (--unpack):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/nmap_5.61-bt1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Scott Baker on 2012-01-17
Ok, quick question here. What the heck were you attempting to do before you got this message ?? It helps considerably if you provide all of the information needed. Were you attempting a download, were you upgrading an existing package, were you running a program, what was it that you were doing that led to this error??  ](*,)

---

### Post by ptrakk on 2012-01-30
lol you were converting backtrack to ubuntu. i did that too and got the same errors.

i bet you could just

```
sudo gedit /var/lib/dpkg/status
```


and remove the versions that are giving you trouble.:popcorn:



.:edit:.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
just edited that file but i used replace(ctrl+h) and I replaced:

"Version: b" -to-> "Version: 1337b"
"Version: r" -to-> "Version: 1337r"

without quotes and all is good.

---

