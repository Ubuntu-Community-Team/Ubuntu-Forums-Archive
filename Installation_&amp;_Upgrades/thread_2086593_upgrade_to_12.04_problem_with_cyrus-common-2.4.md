---
title: "upgrade to 12.04 problem with cyrus-common-2.4"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by melipone on 2012-11-21
[CENTER]
[LEFT]hi!

I'm having problems after my upgrade with the cyrus-common-2.4 package. Here's a trace of the error. There seems to be some circularity. Any suggestions on how to get around that?

myriam@playground:~$ sudo apt-get install cyrus-common-2.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cyrus-common-2.4 is already the newest version.
cyrus-common-2.4 set to manually installed.
The following packages were automatically installed and are no longer required:
  ttf-sazanami-mincho cups-driver-gutenprint libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cyrus-common-2.4 (2.4.12-2) ...
Converting from /var/lib/cyrus/deliver.db (berkeley-nosync) to /tmp/deliver.db.ZDFWlqlp (skiplist)
fatal error: can't open old database
dpkg: error processing cyrus-common-2.4 (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of cyrus-common-2.2:
 cyrus-common-2.2 depends on cyrus-common-2.4; however:
  Package cyrus-common-2.4 is not configured yet.
dpkg: error processing cyrus-common-2.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cyrus-imapd-2.4:
 cyrus-imapd-2.4 depends on cyrus-common-2.4 (= 2.4.12-2); however:
  Package cyrus-common-2.4 is not configured yet.
dpkg: error processing cyrus-imapd-2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cyrus-imapd-2.2:
 cyrus-imapd-2.2 depends on cyrus-imapd-2.4; however:
  Package cyrus-imapd-2.4 is not configured yet.
dpkg: error processing cyrus-imapd-2.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  Errors were encountered while processing:
 cyrus-common-2.4
 cyrus-common-2.2
 cyrus-imapd-2.4
 cyrus-imapd-2.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
myriam@playground:~$ 


[/LEFT]
[/CENTER]

---

