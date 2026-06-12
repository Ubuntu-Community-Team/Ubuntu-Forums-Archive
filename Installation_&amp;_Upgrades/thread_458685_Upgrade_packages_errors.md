---
title: "Upgrade packages errors"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-05-29
Thanks to bung33 I can now paste the errors I am getting on an update:
...
linux-headers-generic 2.6.20.16.28.1 [24.5kB]
Fetched 9657kB in 47s (201kB/s)                                                
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
[COLOR="Red"]grave bugs of linux-libc-dev (2.6.20-15.27 - > 2.6.20-16.28 ) <done>
 #425595 - gcj-4.1: FTBFS: ../../../src/boehm-gc/os_dep.c:21:28: error: operator '<=' has no left operand (Fixed: linux-2.6/2.6.21-3)
   Merged with: 423462
grave bugs of nvidia-glx (1:1.0.9631+2.6.20.5-15.20 - > 1:1.0.9631+2.6.20.5-16.28 )  <pending>
 #420450 - fails to find OpenGL nvidia driver, does not start
   Merged with: 420177 420302 420417
serious bugs of python (2.5.1~rc1-0ubuntu3 -> 2.5.1-0ubuntu3)  <pending>
 #418462 - mailman: Fails to upgrade from Sarge to Etch
Summary:
 nvidia-glx(1 bug), linux-libc-dev(1 bug), python(1 bug)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]  n
****************************************************************************
****** Exit with an error by force in order to stop the installation. ******
****************************************************************************
E: Sub-process if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi returned an error code (10)
E: Failure running script if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi
 [/COLOR]

Errors occur with all the packages (except the upgrade to 2-6-20-16 - but which doesn't work on my or many other' machines judging by the posts.

Any hekp please why the packages above (not 2-6-20-16) all come up with errors and ask if I want to continue, even if I do them individually?

Many thanks,
David

---

