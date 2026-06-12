---
title: "texlive-* breaks apt on lucid upgrade"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Blake Morgan on 2010-05-11
OK, so I recently upgraded to Lucid, and now I'm getting an error from apt saying it can't remove certain programs, with a dpkg error 1.

When i issue: sudo apt-get -f install, I get:


kaek@mythos:/etc$ sudo apt-get -f install 
[sudo] password for kaek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  anyevent-perl texlive-common libfreebob0 libtalloc1 libopal3.6.4
  libsgmls-perl kdebase-runtime-data-common libqt4-phonon libxklavier15
  latex-xft-fonts libswfdec-0.8-0 libprotobuf3 libsad2 libpolkit-qt0 libosp5
  xfce4-volumed libcvaux1 docbook-dsssl libsp1c2 lmodern libknotificationitem1
  libftgl2 libcompress-bzip2-perl thunderbird mplayer-nogui libostyle1c2
  libgupnp-1.0-2 xulrunner-1.9.1-gnome-support libboost-date-time1.40.0
  liblo0ldbl libdns53 libindicate-gtk1 gtk2-ex-formfactory-perl
  libjack0.100.0-0 libiso9660-5 libprojectm2 libaudutil1 sp libass3
  linux-source-2.6.31 nvidia-185-libvdpau luatex libisccc50 liblzma0 openjade
  libpt2.6.4-plugins libindicate3 libx264-67 libprojectm-data
  python-gtksourceview kde-icons-oxygen sgmlspl python-nautilusburn liblwres50
  mplayer-skins xulrunner-1.9.1 libntfs-3g54 libbind9-50 libglib2-ruby
  libffado1 libcv1 kdebase-workspace-libs4+5 libgdata5 libtotem-plparser12
  firefox-3.5-branding libmozjs0d libhighgui1 libpt2.6.4 libisccfg50
  libboost-serialization1.40.0 rhino redland-utils libdb4.7 texlive-doc-base
  firefox-3.5-gnome-support libmyth-0.22-0 texlive-base-bin-doc liblsofui4
  libisc50 libossp-uuid15 libhttp-response-encoding-perl
  kdebase-runtime-bin-kde4 tex-common libparted1.8-12 libgssdp-1.0-1
  libboo2.0-cil
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  jadetex texlive-base texlive-font-utils texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base
  texlive-latex-base-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-luatex texlive-pstricks
  texlive-pstricks-doc
0 upgraded, 0 newly installed, 13 to remove and 76 not upgraded.
13 not fully installed or removed.
After this operation, 293MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 629229 files and directories currently installed.)
Removing jadetex ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.kCt0VKcH
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.3xxXhMAa
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.JLfrGSlL
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsr
dpkg: error processing jadetex (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing texlive-pstricks ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.7pccATM7
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.CjnG7oNX
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.xM3K69uP
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-pstricks (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing texlive-luatex ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.tDjAbSxH
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.C3cI872S
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.4WC30cTj
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-luatex (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing texlive-latex-recommended ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.hhTO5kze
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.6lLhgK39
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.RNUJKDyw
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-latex-recommended (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-latex-base ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.qUZNvOez
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.ugNdoC7J
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.zqwbobF7
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: map
dpkg: error processing texlive-latex-base (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-generic-recommended ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.1Z8XuUnq
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.7KEPb8Lh
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.IP3VMHan
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-generic-recommended (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-fonts-recommended ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.X6hBsaG5
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.T7GDMbRN
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.mlSsB2ze
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: map
dpkg: error processing texlive-fonts-recommended (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-font-utils ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.owfDz5Jg
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.qS0nZJE2
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.ACTZ3iHJ
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-font-utils (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-base ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.TC52PpYM
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.pvClPiE0
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.Flb2kRta
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: map
dpkg: error processing texlive-base (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-fonts-recommended-doc ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.Ukyx9Arx
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.iRLBHnNb
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.SwaF8oJM
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-fonts-recommended-doc (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-latex-base-doc ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.USy3g53h
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.1O1wJtsi
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.SIUD7aiZ
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-latex-base-doc (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-latex-recommended-doc ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.rHPkB1Ao
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.AFONAziV
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.EmCGWESr
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-latex-recommended-doc (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing texlive-pstricks-doc ...

update-updmap --quiet failed. Output has been stored in
/tmp/checkrun.PNVzKeQE
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.NQ1k9WHz
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.SrpgqIEI
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

unknown option: lsrfull
dpkg: error processing texlive-pstricks-doc (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for menu ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 jadetex
 texlive-pstricks
 texlive-luatex
 texlive-latex-recommended
 texlive-latex-base
 texlive-generic-recommended
 texlive-fonts-recommended
 texlive-font-utils
 texlive-base
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
kaek@mythos:/etc$ 

So I open Synaptic, to see the list of installed files. Nothing. Except for the package "jadetex", which lists two files:

/etc/texmf/fmt.d/40jadetex.cnf
/etc/texmf/texmf.d/96JadeTeX.cnf, but...

kaek@mythos:/etc$ cd /etc/texmf
-bash: cd: /etc/texmf: No such file or directory

So I'm at a total loss as to what to do. Any and all suggestions would be greatly appreciated.

---

### Post by Blake Morgan on 2010-05-12
UPDATE: I got an error message from the Update Manager saying my software index was broken. How do I go about repairing it?

---

### Post by dino99 on 2010-05-12
as a general workaround: clean the system and make some room:

- into synaptic repo (sources.list): check that you only have genuine lucid repo activated, no ppa or third party

- then clean, autoclean, autoremove, update, install -f

if you still have complaint about texlive* files: install locate, gconf-cleaner and bleachbit
1) with "locate" + package (texlive*): you find the path(s) for that file, then you can delete it
2) gconf-cleaner will clean some left behind issues (yes to all)
3) bleachbit make more room, but take time to read each setting

sudo dpkg --configure -a
sudo shutdown -F -r now (force a fsck on next boot)

---

### Post by Blake Morgan on 2010-05-12
Dino99: Thank you, thank you, thank you! 

I had already disabled the 3rd party repos, but I was poking around in the man pages for dpkg and coming up empty. 

For clarification, I followed Dino99's sequence thusly:

sudo apt-get clean
sudo apt-get autoclean
and so on through to:

sudo apt-get -f install 

That seemed to fix things without needing to go to the additional steps of using locate, gconf-cleaner & bleachbit. I followed those suggestions later as an abundance of caution.

---

