---
title: "xulrunner and Firexox after upgrade"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by dpickston on 2009-12-23
Hi,

I seem to be having a problem getting xulrunner and therefore 
firefox-3.5 to work. I'm browsing using Konqueror.

The result of running

sudo dpkg --configure -a

Gives the following below. Would any of you kind folks have a possible solution, otherwise I'm going to start the liquid part of the festivities early as this has been giving me a good few problems.

Many thanks.

 
"Setting up xulrunner-1.9.1 (1.9.1.6+nobinonly-0ubuntu0.9.10.1) ...
Segmentation fault
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of moonlight-plugin-mozilla:
 moonlight-plugin-mozilla depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing moonlight-plugin-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of couchdb-bin:
 couchdb-bin depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing couchdb-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-dev:
 xulrunner-1.9.1-dev depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-dbg:
 xulrunner-1.9.1-dbg depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-dev:
 xulrunner-dev depends on xulrunner-1.9.1-dev (>= 1.9.1.6+nobinonly); however:
  Package xulrunner-1.9.1-dev is not configured yet.
dpkg: error processing xulrunner-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on xulrunner-1.9.1 (>= 1.9.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-branding:
 firefox-3.5-branding depends on firefox-3.5 (= 3.5.6+nobinonly-0ubuntu0.9.10.1); however:
  Package firefox-3.5 is not configured yet.
dpkg: error processing firefox-3.5-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prism:
 prism depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing prism (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb-bin (>= 0.10.0-0ubuntu3); however:
  Package couchdb-bin is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-testsuite-dev:
 xulrunner-1.9.1-testsuite-dev depends on xulrunner-1.9.1-dev (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1-dev is not configured yet.
dpkg: error processing xulrunner-1.9.1-testsuite-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-testsuite:
 xulrunner-1.9.1-testsuite depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-testsuite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozzemberek:
 mozzemberek depends on firefox-3.5 | iceweasel (>= 3) | abrowser-3.5 | thunderbird (>= 3~) | thunderbird-3.0 | icedove (>= 3~) | xulrunner-1.9 | xulrunner-1.9.1 | xulrunner-1.9.2; however:
  Package firefox-3.5 is not configured yet.
  Package iceweasel is not installed.
  Package abrowser-3.5 is not installed.
  Version of thunderbird on system is 2.0.0.23+build1+nobinonly-0ubuntu1.
  Package thunderbird-3.0 is not installed.
  Package icedove is not installed.
  Package xulrunner-1.9 is not installed.
  Package xulrunner-1.9.1 is not configured yet.
  Package xulrunner-1.9.2 is not installed.
dpkg: error processing mozzemberek (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.5; however:
  Package firefox-3.5 is not configured yet.
 firefox depends on firefox-3.5-branding; however:
  Package firefox-3.5-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch:
 python-desktopcouch depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch-records:
 python-desktopcouch-records depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch-records (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not installed.
  Package firefox-3.5 which provides firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.1
 yelp
 moonlight-plugin-mozilla
 couchdb-bin
 ubuntu-desktop
 xulrunner-1.9.1-dev
 xulrunner-1.9.1-dbg
 xulrunner-dev
 ubuntu-docs
 firefox-3.5
 firefox-3.5-branding
 gnome-user-guide
 prism
 desktopcouch
 xulrunner-1.9.1-gnome-support
 xulrunner-1.9.1-testsuite-dev
 xulrunner-1.9.1-testsuite
 mozzemberek
 firefox
 evolution-couchdb
 python-desktopcouch
 python-desktopcouch-records
 ubufox"

---

### Post by dpickston on 2009-12-23
Any help?






> **dpickston said:**
> Hi,

I seem to be having a problem getting xulrunner and therefore 
firefox-3.5 to work. I'm browsing using Konqueror.

The result of running

sudo dpkg --configure -a

Gives the following below. Would any of you kind folks have a possible solution, otherwise I'm going to start the liquid part of the festivities early as this has been giving me a good few problems.

Many thanks.

 
"Setting up xulrunner-1.9.1 (1.9.1.6+nobinonly-0ubuntu0.9.10.1) ...
Segmentation fault
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of moonlight-plugin-mozilla:
 moonlight-plugin-mozilla depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing moonlight-plugin-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of couchdb-bin:
 couchdb-bin depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing couchdb-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-dev:
 xulrunner-1.9.1-dev depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-dbg:
 xulrunner-1.9.1-dbg depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-dev:
 xulrunner-dev depends on xulrunner-1.9.1-dev (>= 1.9.1.6+nobinonly); however:
  Package xulrunner-1.9.1-dev is not configured yet.
dpkg: error processing xulrunner-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on xulrunner-1.9.1 (>= 1.9.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-branding:
 firefox-3.5-branding depends on firefox-3.5 (= 3.5.6+nobinonly-0ubuntu0.9.10.1); however:
  Package firefox-3.5 is not configured yet.
dpkg: error processing firefox-3.5-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prism:
 prism depends on xulrunner-1.9.1; however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing prism (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb-bin (>= 0.10.0-0ubuntu3); however:
  Package couchdb-bin is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-testsuite-dev:
 xulrunner-1.9.1-testsuite-dev depends on xulrunner-1.9.1-dev (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1-dev is not configured yet.
dpkg: error processing xulrunner-1.9.1-testsuite-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-testsuite:
 xulrunner-1.9.1-testsuite depends on xulrunner-1.9.1 (= 1.9.1.6+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-testsuite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozzemberek:
 mozzemberek depends on firefox-3.5 | iceweasel (>= 3) | abrowser-3.5 | thunderbird (>= 3~) | thunderbird-3.0 | icedove (>= 3~) | xulrunner-1.9 | xulrunner-1.9.1 | xulrunner-1.9.2; however:
  Package firefox-3.5 is not configured yet.
  Package iceweasel is not installed.
  Package abrowser-3.5 is not installed.
  Version of thunderbird on system is 2.0.0.23+build1+nobinonly-0ubuntu1.
  Package thunderbird-3.0 is not installed.
  Package icedove is not installed.
  Package xulrunner-1.9 is not installed.
  Package xulrunner-1.9.1 is not configured yet.
  Package xulrunner-1.9.2 is not installed.
dpkg: error processing mozzemberek (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.5; however:
  Package firefox-3.5 is not configured yet.
 firefox depends on firefox-3.5-branding; however:
  Package firefox-3.5-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch:
 python-desktopcouch depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch-records:
 python-desktopcouch-records depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch-records (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not installed.
  Package firefox-3.5 which provides firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.1
 yelp
 moonlight-plugin-mozilla
 couchdb-bin
 ubuntu-desktop
 xulrunner-1.9.1-dev
 xulrunner-1.9.1-dbg
 xulrunner-dev
 ubuntu-docs
 firefox-3.5
 firefox-3.5-branding
 gnome-user-guide
 prism
 desktopcouch
 xulrunner-1.9.1-gnome-support
 xulrunner-1.9.1-testsuite-dev
 xulrunner-1.9.1-testsuite
 mozzemberek
 firefox
 evolution-couchdb
 python-desktopcouch
 python-desktopcouch-records
 ubufox"

---

### Post by dpickston on 2009-12-24
Hellllllppppppp! What a nightmare.....any ideas at all please?:confused:

---

