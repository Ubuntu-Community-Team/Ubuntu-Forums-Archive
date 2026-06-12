---
title: "update problems"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by wickedninjalo on 2007-10-01
I went to install updates and it gave me an error and said this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I and did what it told me and I got this

Setting up clamav-getfiles (0.6-1) ...
eicar.com md5sum mismatch, file needs downloading
curl --remote-name [http://www.eicar.org/download/eicar.com](http://www.eicar.org/download/eicar.com)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  2:23:06 --:--:--     0

and it sits there forever....obvously

please tell me how to fix this absolute beginner talk

btw im running 7.04 FF 64 bit

---

### Post by Pumalite on 2007-10-01
Did you run:
sudo dpkg --configure -a

---

### Post by wickedninjalo on 2007-10-03
yes I did as I said in the original post, and I get this

Setting up clamav-getfiles (0.6-1) ...
eicar.com md5sum mismatch, file needs downloading
curl --remote-name [http://www.eicar.org/download/eicar.com](http://www.eicar.org/download/eicar.com)
% Total % Received % Xferd Average Speed Time Time Time Current
Dload Upload Total Spent Left Speed
0 0 0 0 0 0 0 0 --:--:-- 2:23:06 --:--:-- 0

and it sits there forever

---

### Post by Pumalite on 2007-10-03
Try this:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by wickedninjalo on 2007-10-03
Unfortunately I am a beginner and I would  need to be told the name of the package to be removed

---

### Post by Pumalite on 2007-10-03
I think you got stuck in the middle of installing clamav
Try:
locate clamav

---

### Post by Elotero on 2007-10-03
Yo.. im having the exact same problem.. i have had this problem for awhile now.. i can install any new packages.. this problem almost made me quit Ubuntu...  

I got the little sunblast red icon  (you have 112 updates available)
I click the icon
Click Install Updates.
 E: dpkg was interupted, you must manually run dpkg --configure -a to correct the problem. E:_cache ->open()failed please report

---

### Post by Elotero on 2007-10-03
Oh yea.. im on FF 7.04.... and i pulled this move in the terminal:sudo dpkg --configure -a... i presssed enter... asked for my password.. i gave it.. and NADA.. it took me to the terminal again.. does this mean its fixed?

---

### Post by Elotero on 2007-10-03
GREAT! now i try and run the little sunfire red icon "update manager"... and i get this message... 


E:the package virtualbox needs to be reinstalled, but i cant find an archive for it.... 

This system has no common sense.. if you cant find it.. dont f****n install it then!!!!!



This sucks.. i cant install ANY packages because of this BS... it has been like this for a few months already... i want my laptop back! and i feel like i only have half a machine.. and i was obviously trying to get virtualbox so i can use something that really "just works" ... please... can anyone help? if not.. can anyone help me install XP back? im sick and tired of this ...

---

### Post by Pumalite on 2007-10-03
sudo dpkg --remove --force-remove-reinstreq virtualbox
Then reinstall virtualbox if need be

---

### Post by Elotero on 2007-10-03
Damn.. youre pretty good..  my package manager is working now.. thank you... and i dont mean to sound rude... i really want to say goodbye to windows.. but you can see where the frustration would come from.... no experience with terminals can make for some very frustrating moments.. once again thank you....

---

### Post by Pumalite on 2007-10-03
You are welcome. You'll always have the Ubuntu Forum.

---

### Post by wickedninjalo on 2007-10-03
I did what you said and I got all this

root@joe-laptop:~# locate clamav
/etc/rc0.d/K20clamav-freshclam
/etc/rc0.d/K20clamav-daemon
/etc/logcheck/ignore.d.paranoid/clamav-daemon
/etc/logcheck/ignore.d.paranoid/clamav-milter.dpkg-new
/etc/logcheck/ignore.d.server/clamav-daemon
/etc/logcheck/ignore.d.server/clamav-freshclam
/etc/logcheck/ignore.d.server/clamav-milter.dpkg-new
/etc/rc4.d/S20clamav-daemon
/etc/rc4.d/S20clamav-freshclam
/etc/default/clamav-daemon
/etc/default/clamav-milter.dpkg-new
/etc/init.d/clamav-daemon
/etc/init.d/clamav-freshclam
/etc/init.d/clamav-milter.dpkg-new
/etc/mail/m4/clamav-milter.m4.dpkg-new
/etc/network/if-down.d/clamav-freshclam-ifupdown
/etc/network/if-up.d/clamav-freshclam-ifupdown
/etc/ppp/ip-down.d/clamav-freshclam-ifupdown
/etc/ppp/ip-up.d/clamav-freshclam-ifupdown
/etc/rc5.d/S20clamav-daemon
/etc/rc5.d/S20clamav-freshclam
/etc/logrotate.d/clamav-daemon
/etc/logrotate.d/clamav-freshclam
/etc/clamav
/etc/clamav/onerrorexecute.d
/etc/clamav/onupdateexecute.d
/etc/clamav/virusevent.d
/etc/clamav/freshclam.conf
/etc/clamav/clamd.conf
/etc/rc3.d/S20clamav-daemon
/etc/rc3.d/S20clamav-freshclam
/etc/rc6.d/K20clamav-freshclam
/etc/rc6.d/K20clamav-daemon
/etc/rc2.d/S20clamav-daemon
/etc/rc2.d/S20clamav-freshclam
/etc/rc1.d/K20clamav-freshclam
/etc/rc1.d/K20clamav-daemon
/var/cache/apt/archives/clamav-getfiles_0.6-1_all.deb
/var/cache/apt/archives/clamav-testfiles_0.91.1-1ubuntu3~feisty1_all.deb
/var/cache/apt/archives/clamav-milter_0.91.1-1ubuntu3~feisty1_amd64.deb
/var/cache/apt/archives/clamav_0.91.1-1ubuntu3~feisty1_amd64.deb
/var/cache/apt/archives/clamav-base_0.91.1-1ubuntu3~feisty1_all.deb
/var/cache/apt/archives/clamav-docs_0.91.1-1ubuntu3~feisty1_all.deb
/var/cache/apt/archives/clamav-freshclam_0.91.1-1ubuntu3~feisty1_amd64.deb
/var/cache/apt/archives/clamav-daemon_0.91.1-1ubuntu3~feisty1_amd64.deb
/var/cache/apt/archives/libclamav2_0.91.1-1ubuntu3~feisty1_amd64.deb
/var/log/clamav
/var/log/clamav/freshclam.log
/var/log/clamav/clamav.log
/var/lib/ucf/cache/:etc:clamav:clamd.conf
/var/lib/ucf/cache/:etc:clamav:freshclam.conf
/var/lib/ucf/cache/:etc:logrotate.d:clamav-daemon
/var/lib/clamav-getfiles
/var/lib/clamav
/var/lib/clamav/daily.inc
/var/lib/clamav/daily.inc/COPYING
/var/lib/clamav/daily.inc/daily.hdb
/var/lib/clamav/daily.inc/daily.ndu
/var/lib/clamav/daily.inc/daily.cfg
/var/lib/clamav/daily.inc/daily.fp
/var/lib/clamav/daily.inc/daily.zmd
/var/lib/clamav/daily.inc/daily.wdb
/var/lib/clamav/daily.inc/daily.mdb
/var/lib/clamav/daily.inc/daily.info
/var/lib/clamav/daily.inc/daily.pdb
/var/lib/clamav/daily.inc/daily.hdu
/var/lib/clamav/daily.inc/daily.ndb
/var/lib/clamav/daily.inc/daily.db
/var/lib/clamav/daily.inc/daily.mdu
/var/lib/clamav/main.inc
/var/lib/clamav/main.inc/COPYING
/var/lib/clamav/main.inc/main.hdb
/var/lib/clamav/main.inc/main.fp
/var/lib/clamav/main.inc/main.ndb
/var/lib/clamav/main.inc/main.info
/var/lib/clamav/main.inc/main.zmd
/var/lib/clamav/main.inc/main.mdb
/var/lib/clamav/main.inc/main.db
/var/lib/clamav/mirrors.dat
/var/lib/dpkg/info/clamav.list
/var/lib/dpkg/info/libclamav2.md5sums
/var/lib/dpkg/info/clamav-getfiles.templates
/var/lib/dpkg/info/clamav-base.templates
/var/lib/dpkg/info/clamav-base.list
/var/lib/dpkg/info/clamav-freshclam.postinst
/var/lib/dpkg/info/clamav-milter.md5sums
/var/lib/dpkg/info/clamav-freshclam.config
/var/lib/dpkg/info/libclamav2.shlibs
/var/lib/dpkg/info/clamav-daemon.postrm
/var/lib/dpkg/info/clamav-base.postrm
/var/lib/dpkg/info/clamav-freshclam.postrm
/var/lib/dpkg/info/clamav-base.postinst
/var/lib/dpkg/info/clamav-milter.list
/var/lib/dpkg/info/clamav-docs.list
/var/lib/dpkg/info/clamav-freshclam.prerm
/var/lib/dpkg/info/clamav-docs.md5sums
/var/lib/dpkg/info/clamav-base.config
/var/lib/dpkg/info/clamav-milter.postrm
/var/lib/dpkg/info/clamav-getfiles.postrm
/var/lib/dpkg/info/clamav-getfiles.list
/var/lib/dpkg/info/clamav-freshclam.conffiles
/var/lib/dpkg/info/clamav-daemon.md5sums
/var/lib/dpkg/info/clamav-milter.conffiles
/var/lib/dpkg/info/clamav-freshclam.list
/var/lib/dpkg/info/libclamav2.postinst
/var/lib/dpkg/info/clamav-freshclam.md5sums
/var/lib/dpkg/info/clamav-base.md5sums
/var/lib/dpkg/info/clamav-daemon.prerm
/var/lib/dpkg/info/clamav-getfiles.postinst
/var/lib/dpkg/info/clamav-daemon.list
/var/lib/dpkg/info/clamav-freshclam.templates
/var/lib/dpkg/info/clamav-daemon.conffiles
/var/lib/dpkg/info/clamav-testfiles.md5sums
/var/lib/dpkg/info/clamav-daemon.postinst
/var/lib/dpkg/info/clamav-milter.prerm
/var/lib/dpkg/info/clamav-getfiles.md5sums
/var/lib/dpkg/info/clamav-testfiles.list
/var/lib/dpkg/info/libclamav2.postrm
/var/lib/dpkg/info/clamav.md5sums
/var/lib/dpkg/info/clamav-getfiles.config
/var/lib/dpkg/info/clamav-milter.postinst
/var/lib/dpkg/info/libclamav2.list
/usr/bin/clamav-getfiles
/usr/sbin/clamav-milter
/usr/lib/libclamav.so.2.0.7
/usr/lib/libclamav.so.2
/usr/share/clamav-testfiles
/usr/share/clamav-testfiles/debugm.c
/usr/share/clamav-testfiles/clam.zip
/usr/share/clamav-testfiles/clam.exe.bz2
/usr/share/clamav-testfiles/clam-v3.rar
/usr/share/clamav-testfiles/clam-v2.rar
/usr/share/clamav-testfiles/clam.exe
/usr/share/clamav-testfiles/clam.cab
/usr/share/man/man8/clamav-milter.8.gz
/usr/share/man/man8/clamav-getfiles.8.gz
/usr/share/clamav-getfiles
/usr/share/clamav-getfiles/freshclam-wrapper
/usr/share/doc/clamav-base
/usr/share/doc/clamav-base/NEWS.Debian.gz
/usr/share/doc/clamav-base/BUGS
/usr/share/doc/clamav-base/changelog.Debian.gz
/usr/share/doc/clamav-base/changelog.gz
/usr/share/doc/clamav-base/README.Debian.gz
/usr/share/doc/clamav-base/copyright
/usr/share/doc/clamav-base/AUTHORS
/usr/share/doc/clamav-base/examples
/usr/share/doc/clamav-base/examples/clamd.conf
/usr/share/doc/clamav-base/README.gz
/usr/share/doc/clamav-base/FAQ
/usr/share/doc/clamav-testfiles
/usr/share/doc/clamav-testfiles/NEWS.Debian.gz
/usr/share/doc/clamav-testfiles/BUGS
/usr/share/doc/clamav-testfiles/changelog.Debian.gz
/usr/share/doc/clamav-testfiles/changelog.gz
/usr/share/doc/clamav-testfiles/README.Debian.gz
/usr/share/doc/clamav-testfiles/copyright
/usr/share/doc/clamav-testfiles/AUTHORS
/usr/share/doc/clamav-testfiles/README.gz
/usr/share/doc/clamav-testfiles/FAQ
/usr/share/doc/clamav-docs
/usr/share/doc/clamav-docs/signatures.pdf
/usr/share/doc/clamav-docs/NEWS.Debian.gz
/usr/share/doc/clamav-docs/BUGS
/usr/share/doc/clamav-docs/clam.eps.gz
/usr/share/doc/clamav-docs/changelog.Debian.gz
/usr/share/doc/clamav-docs/changelog.gz
/usr/share/doc/clamav-docs/README.Debian.gz
/usr/share/doc/clamav-docs/html
/usr/share/doc/clamav-docs/html/node11.html
/usr/share/doc/clamav-docs/html/img1.png
/usr/share/doc/clamav-docs/html/node28.html
/usr/share/doc/clamav-docs/html/node26.html
/usr/share/doc/clamav-docs/html/node15.html
/usr/share/doc/clamav-docs/html/next.png
/usr/share/doc/clamav-docs/html/node43.html
/usr/share/doc/clamav-docs/html/node42.html
/usr/share/doc/clamav-docs/html/node23.html
/usr/share/doc/clamav-docs/html/node8.html
/usr/share/doc/clamav-docs/html/node34.html
/usr/share/doc/clamav-docs/html/node41.html
/usr/share/doc/clamav-docs/html/node1.html
/usr/share/doc/clamav-docs/html/node31.html
/usr/share/doc/clamav-docs/html/node10.html
/usr/share/doc/clamav-docs/html/node18.html
/usr/share/doc/clamav-docs/html/node32.html
/usr/share/doc/clamav-docs/html/node12.html
/usr/share/doc/clamav-docs/html/node49.html
/usr/share/doc/clamav-docs/html/node21.html
/usr/share/doc/clamav-docs/html/node17.html
/usr/share/doc/clamav-docs/html/node29.html
/usr/share/doc/clamav-docs/html/node2.html
/usr/share/doc/clamav-docs/html/node27.html
/usr/share/doc/clamav-docs/html/node9.html
/usr/share/doc/clamav-docs/html/node48.html
/usr/share/doc/clamav-docs/html/node7.html
/usr/share/doc/clamav-docs/html/node54.html
/usr/share/doc/clamav-docs/html/node19.html
/usr/share/doc/clamav-docs/html/node44.html
/usr/share/doc/clamav-docs/html/node51.html
/usr/share/doc/clamav-docs/html/clamdoc.css
/usr/share/doc/clamav-docs/html/next_g.png
/usr/share/doc/clamav-docs/html/clamdoc.html
/usr/share/doc/clamav-docs/html/node47.html
/usr/share/doc/clamav-docs/html/footnode.html
/usr/share/doc/clamav-docs/html/node53.html
/usr/share/doc/clamav-docs/html/contents.png
/usr/share/doc/clamav-docs/html/prev.png
/usr/share/doc/clamav-docs/html/node16.html
/usr/share/doc/clamav-docs/html/index.html
/usr/share/doc/clamav-docs/html/node40.html
/usr/share/doc/clamav-docs/html/node33.html
/usr/share/doc/clamav-docs/html/img3.png
/usr/share/doc/clamav-docs/html/node13.html
/usr/share/doc/clamav-docs/html/node38.html
/usr/share/doc/clamav-docs/html/img4.png
/usr/share/doc/clamav-docs/html/node35.html
/usr/share/doc/clamav-docs/html/img2.png
/usr/share/doc/clamav-docs/html/node36.html
/usr/share/doc/clamav-docs/html/prev_g.png
/usr/share/doc/clamav-docs/html/node46.html
/usr/share/doc/clamav-docs/html/node30.html
/usr/share/doc/clamav-docs/html/up.png
/usr/share/doc/clamav-docs/html/node14.html
/usr/share/doc/clamav-docs/html/node6.html
/usr/share/doc/clamav-docs/html/node5.html
/usr/share/doc/clamav-docs/html/node22.html
/usr/share/doc/clamav-docs/html/node45.html
/usr/share/doc/clamav-docs/html/node4.html
/usr/share/doc/clamav-docs/html/node3.html
/usr/share/doc/clamav-docs/html/node20.html
/usr/share/doc/clamav-docs/html/node52.html
/usr/share/doc/clamav-docs/html/node24.html
/usr/share/doc/clamav-docs/html/node37.html
/usr/share/doc/clamav-docs/html/node50.html
/usr/share/doc/clamav-docs/html/node25.html
/usr/share/doc/clamav-docs/html/up_g.png
/usr/share/doc/clamav-docs/html/node39.html
/usr/share/doc/clamav-docs/copyright
/usr/share/doc/clamav-docs/clamav-mirror-howto.pdf
/usr/share/doc/clamav-docs/clamdoc.tex.gz
/usr/share/doc/clamav-docs/AUTHORS
/usr/share/doc/clamav-docs/signatures.tex.gz
/usr/share/doc/clamav-docs/clamav-mirror-howto.tex.gz
/usr/share/doc/clamav-docs/README.gz
/usr/share/doc/clamav-docs/FAQ
/usr/share/doc/clamav-docs/clamdoc.pdf
/usr/share/doc/libclamav2
/usr/share/doc/libclamav2/NEWS.Debian.gz
/usr/share/doc/libclamav2/BUGS
/usr/share/doc/libclamav2/changelog.Debian.gz
/usr/share/doc/libclamav2/changelog.gz
/usr/share/doc/libclamav2/README.Debian.gz
/usr/share/doc/libclamav2/copyright
/usr/share/doc/libclamav2/AUTHORS
/usr/share/doc/libclamav2/README.gz
/usr/share/doc/libclamav2/FAQ
/usr/share/doc/clamav-milter
/usr/share/doc/clamav-milter/INSTALL.gz
/usr/share/doc/clamav-milter/README.Debian
/usr/share/doc/clamav-milter/NEWS.Debian.gz
/usr/share/doc/clamav-milter/BUGS
/usr/share/doc/clamav-milter/changelog.Debian.gz
/usr/share/doc/clamav-milter/changelog.gz
/usr/share/doc/clamav-milter/README.Debian.gz
/usr/share/doc/clamav-milter/copyright
/usr/share/doc/clamav-milter/AUTHORS.gz
/usr/share/doc/clamav-milter/README.gz
/usr/share/doc/clamav-milter/FAQ
/usr/share/doc/clamav-getfiles
/usr/share/doc/clamav-getfiles/changelog.Debian.gz
/usr/share/doc/clamav-getfiles/copyright
/usr/share/doc/clamav-daemon
/usr/share/doc/clamav-daemon/NEWS.Debian.gz
/usr/share/doc/clamav-daemon/BUGS
/usr/share/doc/clamav-daemon/changelog.Debian.gz
/usr/share/doc/clamav-daemon/changelog.gz
/usr/share/doc/clamav-daemon/README.Debian.gz
/usr/share/doc/clamav-daemon/copyright
/usr/share/doc/clamav-daemon/AUTHORS.gz
/usr/share/doc/clamav-daemon/README.gz
/usr/share/doc/clamav-daemon/FAQ
/usr/share/doc/clamav-freshclam
/usr/share/doc/clamav-freshclam/mirror-list.gz
/usr/share/doc/clamav-freshclam/NEWS.Debian.gz
/usr/share/doc/clamav-freshclam/BUGS
/usr/share/doc/clamav-freshclam/changelog.Debian.gz
/usr/share/doc/clamav-freshclam/changelog.gz
/usr/share/doc/clamav-freshclam/README.Debian.gz
/usr/share/doc/clamav-freshclam/copyright
/usr/share/doc/clamav-freshclam/AUTHORS.gz
/usr/share/doc/clamav-freshclam/examples
/usr/share/doc/clamav-freshclam/examples/daily.cvd
/usr/share/doc/clamav-freshclam/examples/main.cvd
/usr/share/doc/clamav-freshclam/examples/freshclam.conf
/usr/share/doc/clamav-freshclam/README.gz
/usr/share/doc/clamav-freshclam/FAQ
/usr/share/doc/clamav
/usr/share/doc/clamav/NEWS.Debian.gz
/usr/share/doc/clamav/BUGS
/usr/share/doc/clamav/changelog.Debian.gz
/usr/share/doc/clamav/changelog.gz
/usr/share/doc/clamav/README.Debian.gz
/usr/share/doc/clamav/copyright
/usr/share/doc/clamav/AUTHORS.gz
/usr/share/doc/clamav/examples
/usr/share/doc/clamav/examples/phishing
/usr/share/doc/clamav/examples/phishing/update_iana_data.sh
/usr/share/doc/clamav/examples/phishing/regex_opt.py
/usr/share/doc/clamav/examples/phishing/update_iana_tld.sh
/usr/share/doc/clamav/examples/phishing/why.py
/usr/share/doc/clamav/examples/phishing/whitelist_test.c
/usr/share/doc/clamav/examples/phishing/test
/usr/share/doc/clamav/examples/phishing/test/urltest.h
/usr/share/doc/clamav/examples/phishing/test/COPYING.gz
/usr/share/doc/clamav/examples/phishing/test/Makefile.am
/usr/share/doc/clamav/examples/phishing/test/install-sh.gz
/usr/share/doc/clamav/examples/phishing/test/configure.gz
/usr/share/doc/clamav/examples/phishing/test/aclocal.m4.gz
/usr/share/doc/clamav/examples/phishing/test/configure.in
/usr/share/doc/clamav/examples/phishing/test/urltest.c
/usr/share/doc/clamav/examples/phishing/test/Makefile.in.gz
/usr/share/doc/clamav/examples/phishing/test/config.sub.gz
/usr/share/doc/clamav/examples/phishing/test/regex_list_test.h
/usr/share/doc/clamav/examples/phishing/test/test-config.h.in
/usr/share/doc/clamav/examples/phishing/test/regex_test.txt
/usr/share/doc/clamav/examples/phishing/test/pdomain.c.gz
/usr/share/doc/clamav/examples/phishing/test/NEWS.gz
/usr/share/doc/clamav/examples/phishing/test/ltmain.sh.gz
/usr/share/doc/clamav/examples/phishing/test/AUTHORS
/usr/share/doc/clamav/examples/phishing/test/regex_list_test.c.gz
/usr/share/doc/clamav/examples/phishing/test/config.guess.gz
/usr/share/doc/clamav/examples/phishing/test/pdomain.h
/usr/share/doc/clamav/examples/phishing/test/ChangeLog
/usr/share/doc/clamav/examples/phishing/test/runner.c
/usr/share/doc/clamav/examples/phishing/test/README
/usr/share/doc/clamav/examples/phishing/test/depcomp.gz
/usr/share/doc/clamav/examples/phishing/test/autogen.sh
/usr/share/doc/clamav/examples/phishing/generate_tables.c.gz
/usr/share/doc/clamav/examples/entitynorm
/usr/share/doc/clamav/examples/entitynorm/generate_entitylist.c.gz
/usr/share/doc/clamav/examples/entitynorm/INSTALL.gz
/usr/share/doc/clamav/examples/entitynorm/COPYING.gz
/usr/share/doc/clamav/examples/entitynorm/test-config.h
/usr/share/doc/clamav/examples/entitynorm/Makefile.am
/usr/share/doc/clamav/examples/entitynorm/configure.gz
/usr/share/doc/clamav/examples/entitynorm/entities
/usr/share/doc/clamav/examples/entitynorm/entities/xhtml-lat1.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isotech.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isotech(2).ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isocyr1.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/mmlextra.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isoamsa.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isogrk2.ent
/usr/share/doc/clamav/examples/entitynorm/entities/isomfrk.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isopub.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isodia.ent
/usr/share/doc/clamav/examples/entitynorm/entities/isolat1.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/xhtml-symbol.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isogrk3.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isogrk1.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isomopf.ent
/usr/share/doc/clamav/examples/entitynorm/entities/isoamsr.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/mmlalias.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isocyr2.ent
/usr/share/doc/clamav/examples/entitynorm/entities/isocyr2(2).ent
/usr/share/doc/clamav/examples/entitynorm/entities/isonum.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isoamsc.ent
/usr/share/doc/clamav/examples/entitynorm/entities/isoamsn.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isogrk4.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/xhtml-special.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isodia(2).ent
/usr/share/doc/clamav/examples/entitynorm/entities/isogrk3(2).ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isoamsa(2).ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isoamso.ent
/usr/share/doc/clamav/examples/entitynorm/entities/isoamsb.ent
/usr/share/doc/clamav/examples/entitynorm/entities/isomscr.ent.gz
/usr/share/doc/clamav/examples/entitynorm/entities/isobox.ent.gz
/usr/share/doc/clamav/examples/entitynorm/aclocal.m4.gz
/usr/share/doc/clamav/examples/entitynorm/configure.in
/usr/share/doc/clamav/examples/entitynorm/Makefile.in.gz
/usr/share/doc/clamav/examples/entitynorm/fix_dbs.sh
/usr/share/doc/clamav/examples/entitynorm/postprocess.c
/usr/share/doc/clamav/examples/entitynorm/fixdb.c.gz
/usr/share/doc/clamav/examples/entitynorm/test-config.h.in
/usr/share/doc/clamav/examples/entitynorm/Makefile.gz
/usr/share/doc/clamav/examples/entitynorm/NEWS.gz
/usr/share/doc/clamav/examples/entitynorm/AUTHORS
/usr/share/doc/clamav/examples/entitynorm/libtool.gz
/usr/share/doc/clamav/examples/entitynorm/ChangeLog
/usr/share/doc/clamav/examples/entitynorm/README
/usr/share/doc/clamav/examples/entitynorm/generate_encoding_aliases.c
/usr/share/doc/clamav/examples/entitynorm/autogen.sh
/usr/share/doc/clamav/examples/clamdwatch
/usr/share/doc/clamav/examples/clamdwatch/clamdwatch.tar.gz
/usr/share/doc/clamav/examples/clamdmon
/usr/share/doc/clamav/examples/clamdmon/clamdmon-1.0.tar.gz
/usr/share/doc/clamav/examples/clampipe
/usr/share/doc/clamav/README.gz
/usr/share/doc/clamav/FAQ
/usr/share/endeavour2/help/avscan/icon_clamav_48x48.gif
/usr/share/lintian/overrides/clamav-base
/usr/share/lintian/overrides/clamav-milter
/usr/share/lintian/overrides/clamav-getfiles
/usr/share/lintian/overrides/clamav-daemon
/usr/share/lintian/overrides/clamav-freshclam
/usr/share/lintian/overrides/clamav
root@joe-laptop:~#

---

### Post by wickedninjalo on 2007-10-03
I fixed it and got rid of clamav, but when I get done updating and I get this

E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 255

what does this mean?

---

