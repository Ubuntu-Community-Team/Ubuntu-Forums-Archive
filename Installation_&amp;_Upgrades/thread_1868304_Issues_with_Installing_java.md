---
title: "Issues with Installing java"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by keityo on 2011-10-24
Hello,

I'm having a tough time installing java.  I have tried installing openjdk, oracle's jdk 7, and sun java 6 to no avail.  I tried the following command to add to the PPA with the following results:

sudo add-apt-repository ppa:ferramroberto/java

You are about to add the following PPA to your system:
 LffL Java
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 80, in <module>
    print " %s" % (ppa_info["description"] or "")
UnicodeEncodeError: 'ascii' codec can't encode character u'\xfc' in position 99: ordinal not in range(128 )


What does this mean, and what can I do to fix it?  Also, is there an easy way to install oracle's jdk 7?  Thanks in advance!

---

### Post by raja.genupula on 2011-10-24
> **keityo said:**
> Hello,

I'm having a tough time installing java.  I have tried installing openjdk, oracle's jdk 7, and sun java 6 to no avail.  I tried the following command to add to the PPA with the following results:

sudo add-apt-repository ppa:ferramroberto/java

You are about to add the following PPA to your system:
 LffL Java
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 80, in <module>
    print " %s" % (ppa_info["description"] or "")
UnicodeEncodeError: 'ascii' codec can't encode character u'\xfc' in position 99: ordinal not in range(128 )


What does this mean, and what can I do to fix it?  Also, is there an easy way to install oracle's jdk 7?  Thanks in advance!


hey man

Go with this 

[http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html)

all the best.

---

### Post by keityo on 2011-10-24
Thanks!  I tried to use alien to convert the rpm to a .deb package, but it didn't work out.  Also, I found some instructions that told me how to manually install using the tar file, but for some reason, it just doesn't work.  Any advice on the error message above?  Thanks again!

---

### Post by raja.genupula on 2011-10-24
> **keityo said:**
> Thanks!  I tried to use alien to convert the rpm to a .deb package, but it didn't work out.  Also, I found some instructions that told me how to manually install using the tar file, but for some reason, it just doesn't work.  Any advice on the error message above?  Thanks again!

Hi man 

just type java by opening your terminal , then it will show A way with available packages with installation command and choose jdk named one in the list.

All the best.

---

### Post by keityo on 2011-10-27
Thanks for the reply!
However, I have no luck.  I checked the package manager, and it says that openjdk-7-jdk (amd64) is installed.  When I type in "java" in the terminal:

The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

I tried to install it again:

sudo apt-get install openjdk-7-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 185 not upgraded.

Not sure what is going on...
This is making me angry...

---

### Post by raja.genupula on 2011-10-27
> **keityo said:**
> Thanks for the reply!
However, I have no luck.  I checked the package manager, and it says that openjdk-7-jdk (amd64) is installed.  When I type in "java" in the terminal:

The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

I tried to install it again:

sudo apt-get install openjdk-7-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 185 not upgraded.

Not sure what is going on...
This is making me angry...

Hi man 

open this link ...its a binary package 

[http://download.oracle.com/otn-pub/java/jdk/7/jdk-7-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7/jdk-7-linux-i586.tar.gz)

from this you can install .

---

### Post by keityo on 2011-10-27
Cool.  How do you install a tar file in kubuntu?

---

### Post by raja.genupula on 2011-10-28
right click on it and click at extract then , 

Evary tar file consists of README file  and it consists of installation process , other wise give me the  contents of that folder i am gonna explain you.

All The Best.

---

### Post by apollothethird on 2012-02-06
> **keityo said:**
> Cool.  How do you install a tar file in kubuntu?

Hi, Keityo.  I can identify with your frustration.  I'm wondering if you ever got the tarball installed and how you did it?

If you succeeded, the community would appreciate closure for others that are having the same problem.

> **raja.genupula said:**
> right click on it and click at extract then , 

Evary tar file consists of README file  and it consists of installation  process , other wise give me the  contents of that folder i am gonna  explain you.

All The Best.

Hi, Raja.  Extracting a tarball is simple.  Most tarballs have some install script or INSTALL readme.txt file.  However the one you linked to doesn't have this.  It has a "README.html" that has one line which points to the license agreement.  Of course there's other important information, but it doesn't show any clear steps of how to actually install the package on the system.

This is the content of the extracted tar ball:

```

total 19700
drwxr-xr-x 8 ljames ljames     4096 2012-02-06 11:59 .
drwxrwxr-x 3 ljames ljames     4096 2012-02-06 11:58 ..
drwxr-xr-x 5 ljames ljames     4096 2011-11-30 15:08 man
drwxr-xr-x 3 ljames ljames     4096 2011-11-30 15:08 include
-rw-r--r-- 1 ljames ljames 19945282 2011-11-30 15:08 src.zip
drwxr-xr-x 5 ljames ljames     4096 2011-11-30 15:08 jre
-r--r--r-- 1 ljames ljames      114 2011-11-30 15:08 README.html
drwxr-xr-x 2 ljames ljames     4096 2011-11-30 15:08 bin
-r--r--r-- 1 ljames ljames     3339 2011-11-30 15:08 COPYRIGHT
drwxr-xr-x 4 ljames ljames     4096 2011-11-30 15:08 db
-rw-r--r-- 1 ljames ljames      444 2011-11-30 15:08 release
drwxr-xr-x 3 ljames ljames     4096 2011-11-30 15:08 lib
-r--r--r-- 1 ljames ljames       40 2011-11-30 15:08 LICENSE
-r--r--r-- 1 ljames ljames   172252 2011-11-30 15:08 THIRDPARTYLICENSEREADME.txt

```It's not clear if the bin file should be merged with /bin off the root of the filesystem, and if the include file should be merged with the /include file off the filesystem.

Hopefully someone will provide some insight to spare me of copying the files all over the place in a trial and error method until I stumble onto a combination that works.

I'm sure for someone who knows the answer is simple, and it'll eventually be simple for me also.

Like Keityo I already tried to convert the RPM file using alien.  The results is:
```

ljames@ubunzeus:~/install$ sudo alien --script jdk-7u2-linux-x64.rpm 
[sudo] password for ljames: 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_prep
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/jdk
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libverify.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/headless/libmawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64/headless:/usr/java/jdk1.7.0_02/jre/lib/amd64/headless/..').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libjava.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libverify.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libverify.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libj2pkcs11.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libjpeg.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libjaas_unix.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/xawt/libmawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64/xawt:/usr/java/jdk1.7.0_02/jre/lib/amd64/xawt/..').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libjsound.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libJdbcOdbc.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libJdbcOdbc.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libJdbcOdbc.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libunpack.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libfontmanager.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libmanagement.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libsctp.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnio.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnio.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libnet.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libdcpr.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libsunec.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libjava.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libsunec.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libt2k.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfontmanager.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfontmanager.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libjsoundalsa.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libmawt.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libjawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libjawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/librmi.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libattach.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libkcms.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libzip.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libmlib_image.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libj2pcsc.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libj2gss.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jdk1.7.0_02/jre/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: dependency on libJdbcOdbc.so could be avoided if "debian/jdk/usr/java/jdk1.7.0_02/jre/lib/amd64/libJdbcOdbc.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libnsl.so.1 could be avoided if "debian/jdk/usr/java/jdk1.7.0_02/bin/javaws debian/jdk/usr/java/jdk1.7.0_02/jre/bin/javaws" were not uselessly linked against it (they use none of its symbols).
dh_gencontrol
dh_md5sums
dh_builddeb
dpkg-deb: error: parsing file 'debian/jdk/DEBIAN/control' near line 2 package 'jdk':
 error in Version string '1.7.0_02-1': invalid character in version number
dh_builddeb: dpkg-deb --build debian/jdk .. returned exit code 2
make: *** [binary-arch] Error 25
ljames@ubunzeus:~/install$ 

```

Thanks in advance for any input!

Edit: By the way, I'll be using this with the Eclipse environment.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by raja.genupula on 2012-02-06
Hi man , please start a new thread . It will be useful to you only for  better solution .

---

### Post by apollothethird on 2012-02-07
> **raja.genupula said:**
> Hi man , please start a new thread . It will be useful to you only for  better solution .

Sure thing, Raja.  Hopefully you'll contribute to how you have yours working.

I'll bring the resolution back to this thread for others who are following it.

Please look at:
Can someone tell me how to install the Oracle java sdk (Ubuntu/Eclipse)?:
[http://ubuntuforums.org/showpost.php?p=11671576&postcount=1](http://ubuntuforums.org/showpost.php?p=11671576&postcount=1)


Thanks again!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by raja.genupula on 2012-02-08
Hi what are you getting if you type java and javac in you terminal ?

---

### Post by apollothethird on 2012-02-12
> **raja.genupula said:**
> Hi what are you getting if you type java and javac in you terminal ?

Hi, Raja.  Just extracting the tarball and not performing any installation steps a user would get whatever was installed (if anything) by default.  Looking at a duplicated computer in my network (one of similar installation and configuration) I get:

```

ljames@mckdav:~$ java 
The program 'java' can be found in the following packages: 
 * gcj-4.4-jre-headless 
 * gcj-4.6-jre-headless 
 * openjdk-6-jre-headless 
 * gcj-4.5-jre-headless 
 * openjdk-7-jre-headless 
Try: sudo apt-get install <selected package> 
ljames@mckdav:~$  

```and

```

ljames@mckdav:~$ javac 
The program 'javac' can be found in the following packages: 
 * openjdk-6-jdk 
 * ecj 
 * gcj-4.4-jdk 
 * gcj-4.6-jdk 
 * gcj-4.5-jdk 
 * openjdk-7-jdk 
Try: sudo apt-get install <selected package> 
ljames@mckdav:~$  

```Ubuntu's intelligent search shows how to install a similar package for the application found.  Of course the search path is searched for the command and by default it's:

```

ljames@mckdav:~$ echo $PATH 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 
ljames@mckdav:~$  

```I already asked if a person should copy the files from the tarball into one of those directories.  Most installation procedures would do this.  Also if a user used the apt-get to install from the repository this would happen.  However, it wouldn't be the version that the OP and me were trying to install.  We were trying to install the latest version from Oracle that we downloaded.

Again, just extracting the tarball will not perform usability without important install steps.  I'm surprised that no install steps are included with the tarball.  Ub of course, there is support on forums such as this where experience people will provide the installation steps, of which I'll do in my next message.

I just wanted to take the time to answer your question.  I appreciate you taking the time to post messages and suggestions in this thread.  I hope you may learn from my followup with the installatin steps (in my next message) as well as the linked new thread posted in my previous message will fill the gaps for you in case you attempt to help another user with a another tarball.

Again, thank you kindly for keeping the topic alive with your attempts to help.

By the way, I will mention that going to the bin directory of the extracted tarball and typing, "./java" or "./javac", will bring up the programs, but that wouldn't be a resolution for the Eclipse environment.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2012-02-12
> **keityo said:**
> Cool.  How do you install a tar file in kubuntu?

Hi, Keityo.  As Raja said, most tarball have install instructions.  However, this tarball doesn't.

There are many ways of installing the files on your system.  I'll provide you with a very convenient method.  By now you might have gotten OpenJava to work (by installing more than just the jdk part you mentioned in one of your questions.  There are more than one package involved to have the full Java programming support.

You can have the full programming support with the tarball Raja linked to you.

You can perform these steps:

```

(Download the jdk package... ie jdk-7u2-linux-x64.tar.gz)
$ tar xjvf jdk-7u2-linux-x64.tar.gz
(move the extracted director to /opt/java)
$ sudo mkdir /opt/jdk
$ sudo mv jdk1.7.0_02 /opt/jdk/
(Set the JAVA_HOME variable)
export JAVA_HOME=/opt/jdk/jdk1.7.0_02
(Set your path variable... for commandline support Eclipse will use the JAVA_HOME variable)
(You can set the path variable via the command line or make it automatic by putting the line
in your .bashrc file)
export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH

```That's just 4 quick steps and you have full Oracle Java support with the latest version from their site.

I don't think you'd have any problems with those steps.  Hopefully you'll test them and mark the topic SOLVED so that others having the same problem can benefit by easily finding a thread with a workable resolution.

Marking the topic solved when it's no longer an issue is a great way to give back to the community.

Have a nice day!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by cybergalvez on 2012-02-12
This is how I did it:

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

