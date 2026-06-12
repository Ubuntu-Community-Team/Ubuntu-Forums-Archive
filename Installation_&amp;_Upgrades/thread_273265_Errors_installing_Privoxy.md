---
title: "Errors installing Privoxy"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by montgoej on 2006-10-07
I've been trying to install privoxy, and every time I try to install it out of the repos or even when I download the package and try to install it manually, I get

Setting up privoxy (3.0.3-5) ...
chown: cannot access `/etc/privoxy/*.action': No such file or directory
chown: cannot access `/etc/privoxy/trust': No such file or directory
dpkg: error processing privoxy (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 privoxy

I had privoxy installed before, but now that I've re-installed Ubuntu, it doesn't work. Can anyone help me solve this?
~Jordan Montgomery

---

### Post by ifun on 2006-11-13
I have the same problem.

I upgrade my u6.06 to u6.10.

It seem to be file's ownership or groupship chaos.

I use "apt-get remove privoxy" and "apt-get install privoxy" to refresh it. 

I download the newest binary package and install it. It fails too.

Hope developers help us to sovles it.

Thanks.

ifun

---

### Post by OmahaVike on 2007-12-03
exact problem remains.

even "apt-get remove privoxy", "apt-get clean", "apt-get install privoxy" doesn't take care of it.  

At first, it appears to be a permissions thing, so I set global write privs on the directories, and still no remedy.

WIERD.

---

### Post by OmahaVike on 2007-12-03
[SOLVED]

Thanks to the package maintainer who helped me with this solution.  I found a less-than-elegant solution by digging into the .deb package and manually extracting out the /etc/privoxy files so the chown would work.  At first, I thought it was a package error, but the maintainer helped me understand how dpkg works in conjunction to uninstalling packages.

Here's what we need to do (the first line is expected to error out):

sudo apt-get install privoxy
sudo apt-get --purge remove privoxy
sudo apt-get install privoxy

Just confirmed it on my end (dapper).  Best of luck to you all.

---

