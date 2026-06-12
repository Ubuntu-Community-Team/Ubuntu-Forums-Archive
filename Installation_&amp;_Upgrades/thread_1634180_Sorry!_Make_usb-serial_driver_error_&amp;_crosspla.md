---
title: "Sorry! Make usb-serial driver error &amp; crossplatformui"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by raiyogendra on 2010-11-30
Every time I try to install new packge on Ubuntu 10.10 process ends with one such message...

Setting up crossplatformui (1.0.21) ...
Rather than invoking    init scripts through /etc/init.d, use the service(8)
utility, e.g. service    acpid restart

Since the script you are attempting to invoke has been    converted to an
Upstart job, you may also use the restart(8) utility, e.g.    restart acpid
acpid start/running, process 2606
Sorry! The usb-serial    driver does not support your Linux version.
Sorry! Make usb-serial driver    error.
But, it try to use the default driver module.
mv: cannot stat    `/usr/local/bin/ztemtApp/ztemt.ko': No such file or directory
dpkg: error    processing crossplatformui (--configure):
 subprocess installed    post-installation script returned error exit status 1
Errors were    encountered while processing:
 crossplatformui
E: Sub-process    /usr/bin/dpkg returned an error code (1)

Seeking Help urgently...

---

### Post by incognita on 2011-08-23
Guess you would have found the solution by now. If anyone else is still looking for it:

Well, all the terminal commands did not help me. In the process, I removed dpkg cempletely and compiled it from source. The problem remained. 

I figured, I had to remove the "set -e" line from the crossplatformui.postrm*file. Upon checking, the file was empty. So that did not help either. 

My solution:

Removed all the files relating to (go to root mode for that  - alt+f2 and then gksudo nautilus) crossplatformui, found in /user/bin/pdkg <OR> /var/lib/dpkg/info/

post that, just run 

sudo apt-get install -f

And you are good to go!

---

