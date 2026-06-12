---
title: "undefined symbol: Perl_Iwatchok_ptp"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Deathcon_1 on 2010-03-27
I was attempting to update my server today and I got this strange error listed above.  I can do an apt-get update, but not an apt-get upgrade, as seen below:

```
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
/usr/bin/perl: symbol lookup error: /usr/lib/libperl.so.5.10: undefined symbol: Perl_Iwatchok_ptp
Setting up chkrootkit (0.48-10) ...
/usr/bin/perl: symbol lookup error: /usr/lib/libperl.so.5.10: undefined symbol: Perl_Iwatchok_ptp
dpkg: error processing chkrootkit (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up html2text (1.3.2a-14) ...
/usr/bin/perl: symbol lookup error: /usr/lib/libperl.so.5.10: undefined symbol: Perl_Iwatchok_ptp
dpkg: error processing html2text (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on html2text; however:
  Package html2text is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
Setting up landscape-common (1.4.4-0ubuntu0.9.10) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          /usr/bin/perl: symbol lookup error: /usr/lib/libperl.so.5.10: undefined symbol: Perl_Iwatchok_ptp
dpkg: error processing landscape-common (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 chkrootkit
 html2text
 debhelper
 landscape-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't update this server at the moment and it's getting very, very annoying as I'm sure you can imagine.

---

