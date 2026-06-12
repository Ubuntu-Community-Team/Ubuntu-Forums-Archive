---
title: "ispconfig on ubuntu 6.10"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by ferjchte on 2008-01-23
I used the [Perfect Ubuntu Setup]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10") to install Ubuntu. Everything went smooth until I tried installed ISPConfig. I got this error:


```
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for a supported version of gcc... ok (4.0.3)
checking for gcc bug PR27603... ok, bug not present
[COLOR="Red"]checking for gcc bug PR28045... configure: error: your compiler has gcc PR28045 bug, use a different compiler, see http://gcc.gnu.org/bugzilla/show_bug.cgi?id=28045
ERROR: Could not configure ClamAV[/COLOR]
cd: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
mv: cannot stat `binaries/aps.tar.gz': No such file or directory
mv: cannot stat `binaries/spamassassin.tar.gz': No such file or directory
mv: cannot stat `binaries/uudeview.tar.gz': No such file or directory
mv: cannot stat `binaries/clamav.tar.gz': No such file or directory
mv: cannot stat `binaries/cronolog': No such file or directory
mv: cannot stat `binaries/cronosplit': No such file or directory
mv: cannot stat `binaries/ispconfig_tcpserver': No such file or directory
mv: cannot stat `binaries/zip': No such file or directory
mv: cannot stat `binaries/unzip': No such file or directory
tar: spamassassin.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `spamassassin': No such file or directory
tar: uudeview.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `uudeview': No such file or directory
tar: clamav.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `clamav': No such file or directory
tar: aps.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./setup2: line 873: ispconfig_tmp/php/bin/php: No such file or directory
ERROR: The PHP binary coming with ISPConfig does not work properly on your system! The installation routine stops here!
```


I read that I might have to install an earlier version of GCC and make a dir for the ISPConfig install, which I tried, but I still get the same error. Any Ideas? Please help.

---

### Post by rocknix on 2008-02-07
I get the same error, someone please help.  

Thanks.

---

