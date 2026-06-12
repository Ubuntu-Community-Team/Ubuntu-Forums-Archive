---
title: "clamav instalation prob..."
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by satti_bb on 2009-11-21
hi ,

iam facing a problem configuring clamav. the errors are like this..
apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav is already the newest version.
clamav set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up clamav-base (0.95.3+dfsg-1ubuntu0.09.04) ...
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.95.3+dfsg-1ubuntu0.09.04); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)

plzzzz anybody suggest me ...

---

