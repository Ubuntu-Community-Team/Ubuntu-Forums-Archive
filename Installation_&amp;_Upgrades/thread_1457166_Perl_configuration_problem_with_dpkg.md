---
title: "Perl configuration problem with dpkg"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by dotbart on 2010-04-18
Hello all,

I've encountered a large problem with my Ubuntu server.
Suddenly my Perl started giving hickups when trying to install/upgrade via apt.
A better explanation may be by showing the error log:
```

bartv.be:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "nl_BE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
Setting up perl (5.10.0-19lenny2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "nl_BE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 7.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 7.
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of apache2.2-common:
 apache2.2-common depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing apache2.2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.9-10+lenny7); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (>= 2.2.9-10+lenny7) | apache2-mpm-prefork (>= 2.2.9-10+lenny7) | apache2-mpm-event (>= 2.2.9-10+lenny7); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-perl:
 libxml-sax-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing libxml-sax-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on perl (>= 5.8); however:
  Package perl is not configured yet.
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not installed.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 perl
 apache2.2-common
 apache2-mpm-prefork
 apache2
 libxml-sax-perl
 libxml-sax-expat-perl
 libxml-simple-perl
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I figured dpkg was the one causing the problem here, digging through the errors, I could see that Perl couldn't find any imports.
I don't remember changing or upgrading perl.

I tried
```

bartv.be:~# dpkg-reconfigure perl
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "nl_BE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/sbin/dpkg-reconfigure line 8.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 8.

```and
```

bartv.be:~# apt-get --reinstall install perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sensible-mda
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "nl_BE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
Setting up perl (5.10.0-19lenny2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "nl_BE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 7.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 7.
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of apache2.2-common:
 apache2.2-common depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing apache2.2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.9-10+lenny7); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (>= 2.2.9-10+lenny7) | apache2-mpm-prefork (>= 2.2.9-10+lenny7) | apache2-mpm-event (>= 2.2.9-10+lenny7); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-perl:
 libxml-sax-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing libxml-sax-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on perl (>= 5.8); however:
  Package perl is not configured yet.
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not installed.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 perl
 apache2.2-common
 apache2-mpm-prefork
 apache2
 libxml-sax-perl
 libxml-sax-expat-perl
 libxml-simple-perl
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```As you can see, without success.

Does anyone have any ideas so I don't have to do a reinstall?


Thanks a million!

---

### Post by songochain on 2010-04-18
Same problem here. I lost spanish language.

BR.

---

### Post by Biospower5000 on 2010-08-13
1: run ```
dpkg-reconfigure locales
```
2: select all locales
3: selct your default language, in my case da_DK.UTF8
VOILA!!!
[B]
[/B]

---

### Post by Biospower5000 on 2010-08-14
remember to be root also:D

---

### Post by Biospower5000 on 2010-08-16
UPDATE!!! if you want english/american output, in mos programs select en_US.UTF8

---

### Post by Biospower5000 on 2010-08-18
UPDATE AGAIN!!!:

Remember if that dosen't work run ```
sudo apt-get install locales
```
sory for the many updates!:lolflag:

---

