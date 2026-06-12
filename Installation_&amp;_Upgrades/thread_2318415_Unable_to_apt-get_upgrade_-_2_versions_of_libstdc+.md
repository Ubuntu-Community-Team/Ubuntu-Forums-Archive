---
title: "Unable to apt-get upgrade - 2 versions of libstdc++ installed?"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by liste on 2016-03-25
Hello,

I'm unable to log in to Unity on my Ubuntu 14.04 desktop machine, I believe because I have broken packages.  When I log in to TTY and try to do an apt-get upgrade, I get the following errors:

```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libstdc++-4.8-dev-armhf-cross : Depends: libstdc++6-armhf-cross (>= 4.8.4-2ubuntu1~14.04.1cross0.11.1) but 4.8.2-16ubuntu4cross0.11 is installed
 libstdc++6-armhf-cross : Depends: gcc-4.8-arm-linux-gnueabihf-base (= 4.8.2-16ubuntu4cross0.11) but 4.8.4-2ubuntu1~14.0.4.1cross0.11.1 is installed
#: Unmet dependencies. Try using -f
```

Also, if I do a apt-get -f upgrade, I get the following errors:

```
Unpacking libstdc++6-armhf-cross (4.8.4-2ununtu1~14.04.1cross0.11.1) over (4.8.2-16ubuntu4cross0.11) ...
dpkg: eror processing archive /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:amd64 4.8.4-2ubuntu1~14.04.1
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried a couple things, including rebooting the machine and moving the __init__.py file, but to no avail.  I've also tried a apt-get dist-upgrade, without any success.  It's always coming back to those two errors.  I don't know if I'm missing any other important information, so just le me know if I can provide something else of use.  Thanks!

---

### Post by ubfan1 on 2016-03-26
Are you trying to set up a cross development environment for armhf?  I have done this by putting the non-host code in my own directory and not trying to "install" it in system areas.  Avoids all the confusion of having executables for different architecture with the same name, or having to chose a link to point to one of them.  Example below for setting up the variables needed for the arm env.
MY_ARM_BASE=${HOME}/dev/toolchain/arm-2008q3
C_INCLUDE_PATH=${MY_ARM_BASE}/lib/gcc/arm-none-linux-gnueabi/4.3.2/include:${MY_ARM_BASE}/lib/gcc/arm-none-linux-gnueabi/4.3.2/include-fixed
LIBRARY_PATH=${MY_ARM_BASE}/arm-none-linux-gnueabi/libc/lib:${MY_ARM_BASE}/arm-none-linux-gnueabi/libc/usr/lib
CPLUS_INCLUDE_PATH=${MY_ARM_BASE}/arm-none-linux-gnueabi/include/c++/4.3.2
#OBJC_INCLUDE_PATH
COMPILER_PATH=${MY_ARM_BASE}/bin
#LD_RUN_PATH
#GPROF_PATH
#######
CC=${COMPILER_PATH}/gcc
CXX=${COMPILER_PATH}/g++
RANLIB=${COMPILER_PATH}/ranlib
STRIP=${COMPILER_PATH}/strip
export C_INCLUDE_PATH LIBRARY_PATH CPLUS_INCLUDE_PATH COMPILER_PATH
export CC CXX RANLIB STRIP

---

### Post by liste on 2016-03-26
Thank you for the suggestion.  I have removed my GCC4.8 (hopefully that was the right one), but I'm still unable to login.  I guess the two issues were unrelated.  I now have no errors when I do an apt-get upgrade, so that was definitely the issue that I outlined in my post.

Thank you for your help!

**EDIT** - nope, I think the issue might still be with GCC.  I have this error in my .xsession-errors:

```

init: update-notifier-crash (/var/crash/libstdc++6-armhf-cross.0.crash) main process (8001) killed by TERM signal

```

**Edit 2** - I'm going to mark this thread as solved and start a new one, as I believe the issue is unrelated.

---

### Post by bbatten on 2016-03-26
I think this is a duplicate of the problem I reported here:
[http://ubuntuforums.org/showthread.php?t=2318377](http://ubuntuforums.org/showthread.php?t=2318377)

---

### Post by liste on 2016-03-26
Hi bbatten - it certainly looks like a very similar issue.  I found by Googling "usr/share/gcc-4.8/python/libstdcxx/__init__.py" that there are a fair number of results from the past day or two.  Just add the search criteria for "past week".  This one looks hopeful, although I decided to do an update to 16.04 beta (which is currently running), so I can't say whether it will work or not:

[http://ubuntuforums.org/showthread.php?t=2318371](http://ubuntuforums.org/showthread.php?t=2318371)

I'll post an update with the result of my release upgrade once it finishes (currently about 10%).

---

