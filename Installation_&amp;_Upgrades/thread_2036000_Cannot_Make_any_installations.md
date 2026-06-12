---
title: "Cannot Make any installations"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by sbiyyala on 2012-07-31
I am reasonably new to Linux Ubuntu. I am using ubuntu 12.04. I am unable to make even small installations 
eg: $ sudo apt-get install tree

**Output ::**
---------------------------------------------
Reading package lists...
Building dependency tree...
Reading state information...
tree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 qmail
 qmail-run

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            E: Sub-process /usr/bin/dpkg returned an error code (1)

----------------------------------------------
I have spent quite a lot of time and am clueless. Please help.

-

---

### Post by zvacet on 2012-08-02
Try with

```
sudo dpkg --configure -a
```

---

### Post by sbiyyala on 2012-08-09
Hello, thanks. But I got the same exact result ::

[B]Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 qmail
 qmail-run
[/B]

---

### Post by johnathansmith on 2012-08-09
Do you add some new "sources" in update manager recently?

---

### Post by Lasall on 2012-08-09
Hi sbiyyala,

edit your **/etc/hostname** and setup your hostname.

Verify it with:
```
hostname -f
```

Regards
Lasall

---

