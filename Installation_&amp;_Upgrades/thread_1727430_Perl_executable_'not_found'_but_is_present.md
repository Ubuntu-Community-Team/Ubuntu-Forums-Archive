---
title: "Perl executable 'not found' but is present"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by kgmeyer on 2011-04-12
I am attempting to install ActivePerl on a remote system logged in as root. I am using TeraTerm (SSH) as terminal. The Perl files are installed in a folder off the root folder and when I run the install.sh script, I get the message perl/bin/perl 'file or directory not found', even though it does exist. This is the script:-

#!/bin/sh

lib_path=perl/lib/CORE
# perl_path=/root/ActivePerl-5.12.3.1204-i686-linux-glibc-2.3.6-294330/perl/bin
perl_path=perl/bin


env -i \
   PATH=/usr/bin:/bin \
   HOME=$HOME \
   LD_LIBRARY_PATH=$lib_path \
   DYLD_LIBRARY_PATH=$lib_path \
   $perl_path/perl -Isupport/lib support/install.pl "$@"


Help will be appreciated.

Kenny.

---

### Post by hakermania on 2011-04-12
Use the output of "which perl"

---

### Post by kgmeyer on 2011-04-13
I have previously tried this and used '/usr/bin/perl' without success. There are additional executables in '/root/ActivePerl...../perl/bin' which need to run and these also fail. It is as though the directories at a lower level than the one where the shell script is, do not exist.
Thanks.

---

