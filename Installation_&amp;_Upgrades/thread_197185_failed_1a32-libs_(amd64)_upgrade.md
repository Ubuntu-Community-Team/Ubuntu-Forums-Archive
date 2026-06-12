---
title: "failed 1a32-libs (amd64) upgrade"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by arthurk on 2006-06-15
Hello,

Used the Upgrade Manager to move to Dapper. Toward the end of the process an error message suggested using apt-get install -f to fix the problem. This too failed. I have included the session output. The following would seemb to be at the root:

dpkg-divert: rename involves overwriting `/usr/bin/ldd' withdifferent file `/usr/bin/ldd.amd64', not allowed

Any suggestions?

Thanks.

bking@tazenda:~/ati$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ia32-libs libglew1 libmagick9 openoffice.org-base
openoffice.org-calc openoffice.org-core openoffice.org-draw
openoffice.org-impress openoffice.org-math
openoffice.org-writer
Suggested packages:
  libwmf-bin unixodbc libmyodbc odbc-postgresql tdsodbc
mdbtools libmysql-java libpg-java libsapdbc-java
The following packages will be REMOVED:
  openoffice.org-bin
The following NEW packages will be installed:
  libglew1 libmagick9 openoffice.org-base
openoffice.org-calc openoffice.org-core openoffice.org-draw
openoffice.org-impress openoffice.org-math
openoffice.org-writer
The following packages will be upgraded:
  ia32-libs
1 upgraded, 9 newly installed, 1 to remove and 449 not
upgraded.
7 not fully installed or removed.
Need to get 0B/49.3MB of archives.
After unpacking 14.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113929 files and directories
currently installed.)
Preparing to replace ia32-libs 1.4ubuntu4 (using
.../ia32-libs_1.4ubuntu19_amd64.deb) ...
dpkg-divert: rename involves overwriting `/usr/bin/ldd' with
  different file `/usr/bin/ldd.amd64', not allowed
dpkg: error processing
/var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb
(--unpack):
 subprocess pre-installation script returned error exit
status 2
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bking@tazenda:~/ati$

---

### Post by drunken_sapo on 2006-06-30
Same problem but this time the conflict is with openoffice. Im using kbuntu dapper.
any ideas yet?
thanks in advance.
-----------------
Configurando ia32-libs-gtk (16) ...
ia32-libs-gtk: removing old diversion for /usr/lib/openoffice/program/soffice.bin
dpkg-divert: rename involves overwriting `/usr/lib/openoffice/program/soffice.bin' with
  different file `/usr/lib/openoffice/program/soffice.bin.real', not allowed
dpkg: error al procesar ia32-libs-gtk (--configure):

---

