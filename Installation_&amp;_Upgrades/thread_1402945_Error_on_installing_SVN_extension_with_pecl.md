---
title: "Error on installing SVN extension with pecl"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by thedp on 2010-02-09
Hello,
  I'm trying to install the following PHP extension: [http://php.net/manual/en/book.svn.php](http://php.net/manual/en/book.svn.php) But when I do **pecl install svn-beta** I receive an error message that it can't locate the **svn_client.h** file. I searched the net but couldn't find any useful reference to this error.


  Thank you for your help.
  

Installation result:
```


root@myUbuntu:/home/thedp# pecl install svn-beta
downloading svn-0.5.1.tgz ...
Starting to download svn-0.5.1.tgz (23,563 bytes)
.....done: 23,563 bytes
4 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
 1. Please provide the prefix of Subversion installation : autodetect

1-1, 'all', 'abort', or Enter to continue: 
 1. Please provide the prefix of the APR installation used with Subversion : autodetect

1-1, 'all', 'abort', or Enter to continue: 
building in /var/tmp/pear-build-root/svn-0.5.1
running: /tmp/pear/temp/svn/configure --with-svn --with-svn-apr
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for svn support... yes, shared
checking for specifying the location of apr for svn... yes, shared
checking for svn includes... configure: error: failed to find svn_client.h
ERROR: `/tmp/pear/temp/svn/configure --with-svn --with-svn-apr' failed
```

---

