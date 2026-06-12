---
title: "APT Package"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by mtechman on 2012-09-28
So my apt package broke and I was having issues running it and was unable to reinstall it using synaptic package manager. So I removed it completely planning on reinstalling it manually from source. However I am having issues doing so. 

root@Xavior:~/apt-0.8.16~exp12ubuntu10.3# ./configure
configure: error: cannot run /bin/bash buildlib/config.sub
root@Xavior:~/apt-0.8.16~exp12ubuntu10.3# make
make: autoconf: Command not found
make: *** [configure] Error 127
root@Xavior:~/apt-0.8.16~exp12ubuntu10.3# make install
make: *** No rule to make target `install'.  Stop.
root@Xavior:~/apt-0.8.16~exp12ubuntu10.3# 

any ideas?

---

### Post by Starcruiser322 on 2012-09-28
You only "make" when you are compiling source. You can't do it with a package, you have to use a package manager or open a downloaded package in one.

---

### Post by kc1di on 2012-09-28
why not download it from here and install it with dpkg -i 
[http://packages.ubuntu.com/search?keywords=apt]("http://packages.ubuntu.com/search?keywords=apt")

---

### Post by mtechman on 2012-09-28
I did what you said and got the following

matthew@Xavior:~$ sudo dpkg -i apt_0.8.16~exp12ubuntu10.2_amd64.deb
(Reading database ... 392009 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.2 (using apt_0.8.16~exp12ubuntu10.2_amd64.deb) ...
Unpacking replacement apt ...
dpkg: dependency problems prevent configuration of apt:
 apt depends on libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10.2); however:
  Package libapt-pkg4.12 is not installed.
dpkg: error processing apt (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 apt

---

### Post by mtechman on 2012-09-28
I found the right package and now everything works. thanks

---

### Post by kc1di on 2012-09-28
> **mtechman said:**
> I found the right package and now everything works. thanks

if that solved the problem please mark thread as solved.
Thanks.
Good Luck :)

---

