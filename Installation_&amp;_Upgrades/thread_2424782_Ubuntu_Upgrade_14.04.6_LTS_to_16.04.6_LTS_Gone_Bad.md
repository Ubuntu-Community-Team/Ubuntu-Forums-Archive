---
title: "Ubuntu Upgrade 14.04.6 LTS to 16.04.6 LTS Gone Bad"
date: 2019-08-14
forum: Installation &amp; Upgrades
---

### Post by jkerwin2 on 2019-08-14
Hi,

I attempted to upgrade from Ubuntu 14.04.6 LTS to 16.04.6 LTS, I received the following error during installation:

The required dependency 'apt (>= 1.0.10.2ubuntu2)' is not installed during upgrade

Now when I log on to my server via a terminal it says that I'm on 16.04.6 LTS, but not everything is working.

I was able to get Apache running after it refused to start, but my Perl-based website hasn't returned. I needed to install some Perl modules used by the website software (Unicode::String) and got:

```
x86_64-linux-gnu-gcc: error: unrecognized command line option &#8216;-fstack-protector-strong&#8217;
make: *** [blib/arch/auto/Unicode/String/String.so] Error 1
  GAAS/GAAS/Unicode-String-2.10.tar.gz
  /usr/bin/make -- NOT OK
Failed during this command:
 GAAS/GAAS/Unicode-String-2.10.tar.gz         : make NO

```

This was related to the version of GCC I had installed. I have version 4.8.4.

For &#8216;-fstack-protector-strong&#8217; to work I need GCC 4.9. When trying to upgrade it (which didn't work) I eventually had to use: sudo apt-get update

Which threw up a load of errors:

```
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin'
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package php-psr-http-message-implementation
W: Ignoring Provides line with DepCompareOp for package php-psr-log-implementation
W: Ignoring Provides line with DepCompareOp for package php-seclib
W: Ignoring Provides line with DepCompareOp for package php-sabre-http
W: Ignoring Provides line with DepCompareOp for package php-math-biginteger
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Ignoring Provides line with DepCompareOp for package xserver-xorg
W: Ignoring Provides line with DepCompareOp for package php-math-biginteger
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Ignoring Provides line with DepCompareOp for package xserver-xorg
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: You may want to run apt-get update to correct these problems
```

Doing other things brings up other errors and I'm having a really bad time with it at the moment. Can anybody help? I'm very capable/willing to follow instruction.

Thanks,
James

---

### Post by dino99 on 2019-08-14
you might want to upgrade to the last LTS instead

Have you made some system cleaning recently to purge old versions and settings left behind ?
(clean/autoclean/autoremove/gtkorphan/bleachbit)

---

### Post by rsteinmetz70112 on 2019-08-14
I assume you upgraded using do-releae-upgrade. If not how did you do it?

It looks like the upgrade didn't complete properly and you still have a lor of 14.04 LTS packages.

What does 
```
sudo dpkg --configure -a
```
show?

Also where are you installing these packages from? It looks like the standard version of gcc for 16.04 LTS is gcc version 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.11).

If your original installation contained non-standard versions of packages any upgrade is likely to be problematic.

This error ```
The required dependency 'apt (>= 1.0.10.2ubuntu2)' is not installed during upgrade

``` indicates that the version of apt isn't correct. 
The version for 16.04 is```
 apt (1.2.32)
```

---

### Post by Impavidus on 2019-08-14
Sometimes a couple of```
sudo apt install -f
```and```
sudo dpkg --configure -a
```can fix a release upgrade gone wrong. Usually it's faster to do a fresh install (jump directly to 18.04 LTS) and restore your documents from your backups.

---

### Post by jkerwin2 on 2019-08-15
Hi,

Thank you for the suggestions and advice. Fortunately I remembered I had a suitable back-up from a few days ago that I was able to revert to. I've taken that route.

I really do appreciate the help offered. I think I'm going to go away and read exactly how to tackle upgrades in future and so be slightly less of an idiot.

As for this server; I inherited responsibility for it and don't fully know how it's set up and what alterations have been made. I don't know if the mismatch between apt, gcc and the OS were due to my partial upgrade or if that was existing pre-failed-upgrade. That's going to be part of the autopsy I carry out this afternoon.

Thanks,
James

---

### Post by rsteinmetz70112 on 2019-08-15
I'd strongly recommend you upgrade as soon as you can to 18.04 LTS since 14.04 LTS ended standard support 25 April 2019, although repositories are available somewhere and extended security maintenance is available if you have UBUNTU support. 

16.04 LTS end of standard support will come fairly soon. Waiting will only make it harder. 

If the Hardware is old you may run into some issues since 32 bit support is being depreciated.

---

