---
title: "[problem]with php5 installation"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by KlMASDO444 on 2010-10-03
why make is not working here?
ls -l
acconfig.h        config.nice      INSTALL             makerpm              README.input_filter               README.TESTING2            svnclean.bat
acconfig.h.in     config.sub       install-sh          missing              README.MAILINGLIST_RULES          README.UNIX-BUILD-SYSTEM   tests
acinclude.m4      configure        libs                mkinstalldirs        README.namespaces                 README.WIN32-BUILD-SYSTEM  TODO
aclocal.m4        configure.in     LICENSE             netware              README.PARAMETER_PARSING_API      README.Zeus                TODO-5.1
build             CREDITS          ltmain.sh           NEWS                 README.PHP4-TO-PHP5-THIN-CHANGES  run-tests.php              TODO-PHP5
buildconf         ext              main                pear                 README.REDIST.BINS                sapi                       TSRM
buildconf.bat     EXTENSIONS       makedist            php5.spec.in         README.RELEASE_PROCESS            scripts                    UPGRADING
CODING_STANDARDS  footer           Makefile.frag       php.gif              README.SELF-CONTAINED-EXTENSIONS  server-tests-config.php    vcsclean
confdefs.h        generated_lists  Makefile.fragments  php.ini-development  README.STREAMS                    server-tests.php           win32
config.cache      genfiles         Makefile.gcov       php.ini-production   README.SUBMITTING_PATCH           snapshot                   Zend
config.guess      header           Makefile.global     README.EXTENSIONS    README.SVN-RULES                  stamp-h.in
config.log        include          Makefile.objects    README.EXT_SKEL      README.TESTING                    stub.c
root@ubuntu:/mnt/sda1/php-5.3.3# make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by SeijiSensei on 2010-10-03
Did you run ./configure first?

---

### Post by KlMASDO444 on 2010-10-04
> **SeijiSensei said:**
> Did you run ./configure first?
 yea man
./configure --prefix=/opt/php5

---

