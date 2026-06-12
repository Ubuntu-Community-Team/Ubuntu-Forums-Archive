---
title: "An error occured"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by rcarrasco on 2009-12-24
Hello,
I am not new to ubuntu; however, this doesn't mean I'm a whiz...yet!  hahaha. Anyways, I am having a problem.  Whenever I try to update my system it will download the updates and then "apply the changes", but it never finishes.  This always pops up:

The first window says:
________________________________________________________________________
An error occurred:

E: linux-image-2.6.31-16-generic: subprocess installed post-installation script returned error exit status 1
E: libdns53: subprocess installed post-installation script returned error exit status 2
E: libisccfg50: dependency problems - leaving unconfigured
E: libbind9-50: dependency problems - leaving unconfigured
E: bind9-host: dependency problems - leaving unconfigured
E: dnsutils: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
_______________________________________________________________________

After I close that another window is behind it that says:

________________________________________________________________________
Update is complete

Not all changes and updates succeeded.  For further details 
of the failure, please expand the 'Details' panel below:

>Details

Then there is a whole bunch of stuff that I can't copy and paste.....
It's a lot of information....
_________________________________________________________________________

I just want to be able to UPDATE my system again....please help me.

Thanks,

RC

---

### Post by adam814 on 2009-12-24
Try this:
> sudo dpkg --configure -a

This tries to configure all unpacked but not configured packages on your system and if you're getting failed updates I imagine you have a few of them.

---

### Post by rcarrasco on 2009-12-24
Hello,
Thanks for the advice I tried that and here is what happened:

___________________________________________________________________________

Setting up libdns53 (1:9.6.1.dfsg.P1-3ubuntu0.2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdns53 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libdns53 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libdns53 is not configured yet.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libdns53 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libdns53 is not configured yet.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libisccfg50:
 libisccfg50 depends on libdns53; however:
  Package libdns53 is not configured yet.
dpkg: error processing libisccfg50 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbind9-50:
 libbind9-50 depends on libdns53; however:
  Package libdns53 is not configured yet.
 libbind9-50 depends on libisccfg50; however:
  Package libisccfg50 is not configured yet.
dpkg: error processing libbind9-50 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-16-generic; however:
  Package linux-image-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.16.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdns53
 bind9-host
 linux-image-2.6.31-16-generic
 dnsutils
 libisccfg50
 libbind9-50
 linux-image-generic
 linux-generic

________________________________________________________________________

I have no idea what the problem is...but thank you, 

RC

---

### Post by rcarrasco on 2009-12-24
Hello,
Thanks for the advice I tried that and here is what happened:

__________________________________________________  _________________________

Setting up libdns53 (1:9.6.1.dfsg.P1-3ubuntu0.2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdns53 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libdns53 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libdns53 is not configured yet.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libdns53 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libdns53 is not configured yet.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libisccfg50:
 libisccfg50 depends on libdns53; however:
  Package libdns53 is not configured yet.
dpkg: error processing libisccfg50 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbind9-50:
 libbind9-50 depends on libdns53; however:
  Package libdns53 is not configured yet.
 libbind9-50 depends on libisccfg50; however:
  Package libisccfg50 is not configured yet.
dpkg: error processing libbind9-50 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-16-generic; however:
  Package linux-image-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.16.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdns53
 bind9-host
 linux-image-2.6.31-16-generic
 dnsutils
 libisccfg50
 libbind9-50
 linux-image-generic
 linux-generic

__________________________________________________  ______________________

I have no idea what the problem is...but thank you, 

RC

---

### Post by adam814 on 2009-12-24
Try:
> sudo aptitude purge libdns53 && sudo aptitude install libdns53
Then try again.  Sometimes the config files just get mixed up.

---

### Post by rcarrasco on 2009-12-24
Okay so I did that and then I went to update my system.  I still got an error; however, it was a different error.

The first window says:
_____________________________________________________________________________________

An Error Occured

The following details are provided:

E: linux-image-2.6.31-16-generic: subprocess installed post-installation script returned error exit status 1
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

___________________________________________________________________________________

The second window is also the same; however, there is a lot less stuff in the details.  I think I was able to upgrade most of it, but there is still a bug somewhere....but then again, I am still a pseudo-newb at this.

---

### Post by adam814 on 2009-12-24
You can get the output from the package manager by doing this in a terminal:
> sudo aptitude safe-upgrade 2>&1 | tee aptitude.log
If you can post the log file back here it should help see what the exact problem is.

---

