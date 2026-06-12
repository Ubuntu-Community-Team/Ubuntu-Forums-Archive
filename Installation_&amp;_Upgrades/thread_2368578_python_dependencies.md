---
title: "python dependencies"
date: 2017-08-12
forum: Installation &amp; Upgrades
---

### Post by larrycrosby001 on 2017-08-12
Hello
I have been going around in circles trying to get package manager working or any install working for that matter. The following errors come up (see below). I have tried many things that have come up through google searches and end up back with the same set of errors. Is there anyway to just add all version of python back to this PC? I have used ubuntu for years as a general user, not a coder... Usually I find some simple commands and things just get fixed, this time not having a lot of luck. Any help will be appreciated. At this time no automated updates will run, no GUI software will install.

Thanks
Larry

system information:
```
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```
Errors I get:
```
larry@Dad-Precision-M6700:~$ sudo apt-get install -fReading package lists... Done
Building dependency tree... 0%
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
0 upgraded, 0 newly installed, 0 to remove and 157 not upgraded.
9 not fully installed or removed.
Need to get 0 B/10.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package python-six (--configure):
 package python-six is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: dependency problems prevent configuration of python-configobj:
 python-configobj depends on python-six; however:
  Package python-six is not installed.


dpkg: error processing package python-configobj (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
       No apport report written because MaxReports is reached already
                                                                     dpkg: dependency problems prevent configuration of python-cryptography:
 python-cryptography depends on python-six (>= 1.4.1); however:
  Package python-six is not installed.


dpkg: error processing package python-cryptography (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-html5lib:
 python-html5lib depends on python-six; however:
  Package python-six is not installed.


dpkg: error processing package python-html5lib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-openssl:
 python-openssl depends on python-cryptography (>= 0.7); however:
  Package python-cryptography is not configured yet.
 python-openssl depends on python-six; however:
  Package python-six is not installed.


dpkg: error processing package python-openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ndg-httpsclient:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                                          No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                                                                                                          python-ndg-httpsclient depends on python-openssl; however:
  Package python-openssl is not configured yet.


dpkg: error processing package python-ndg-httpsclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-urllib3:
 python-urllib3 depends on python-six; however:
  Package python-six is not installed.


dpkg: error processing package python-urllib3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-requests:
 python-requests depends on python-urllib3 (>= 1.13.1); however:
  Package python-urllib3 is not configured yet.
 python-requests depends on python-urllib3 (<< 1.13.2); however:
  Package python-urllib3 is not configured yet.


dpkg: error processing package python-requests (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of variety:
 variety depends on python-configobj; however:
  Package python-configobj is not configured yet.
 variety depends on python-requests; however:
  Package python-requests is not configured yet.


dpkg: error processing package variety (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-six
 python-configobj
 python-cryptography
 python-html5lib
 python-openssl
 python-ndg-httpsclient
 python-urllib3
 python-requests
 variety
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by vocx on 2017-08-12
> **larrycrosby001 said:**
> Hello
I have been going around in circles trying to get package manager working or any install working for that matter. The following errors come up (see below). I have tried many things that have come up through google searches and end up back with the same set of errors. Is there anyway to just add all version of python back to this PC? I have used ubuntu for years as a general user, not a coder... Usually I find some simple commands and things just get fixed, this time not having a lot of luck. Any help will be appreciated. At this time no automated updates will run, no GUI software will install.

Thanks
Larry

What did you do to start receiving these messages? Surely you installed something at some point and you started getting the errors. I remember a thread where a user installed a python package manually in "/usr/local/lib", or some directory like that, and the "apt" system would complain and throw strange errors.

If you can check whether there is a package there that was manually installed you may be able to correct the problem by removing it, even if temporarily. If the "dpkg" or "apt" programs use Python in some way, they may not work if there are some extraneous Python packages that are broken or incompatible with your current Python installation.

---

### Post by sccman on 2017-08-12
It looks like python-six is the hold-up for a good portion of those packages. The next question is...why?

Have you tried fixing all dependencies using apt or apt-get?

```
sudo apt -f install

**- AND/OR - **

sudo apt update --fix-missing
[B]
- AND/OR -[/B]

sudo dpkg --configure -a
```

[http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/)

---

