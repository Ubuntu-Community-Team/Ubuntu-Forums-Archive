---
title: "gstreamer0.8-lame installation problems - any help will be appreciated"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by saadat on 2005-07-16
Have this problem......any help will be appreciated

saadat@ubuntu:~$ sudo apt-get install gstreamer0.8-lame
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-lame: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

---

### Post by Vetto on 2005-07-17
First looks like you need to update the libc6 libray to 2.3.2.ds1-21 (actually ds1-22 is the latest I think)

Go to [HERE](http://packages.debian.org/testing/base/libc6) and get the latest and install it.  If Synaptec reports that you now have broken depedancies...go [HERE](http://ubuntuforums.org/showthread.php?t=47761) and see what I had to do.

After your libc6 is up to the needed version, try again and see what happens.

---

