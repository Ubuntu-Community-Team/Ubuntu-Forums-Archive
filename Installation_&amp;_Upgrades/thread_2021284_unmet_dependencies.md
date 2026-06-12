---
title: "unmet dependencies"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by eGelor on 2012-07-09
Hello ppl,
i add-apt-repository ppa:bumblebee/stable 
and try to install this app that is not compatible with ubuntu 12.04
the error is: 
> virtualgl-libs : Depends: libturbojpeg but it is not installed
when i give
> sudo apt-get -f install 
my system try to download 326Kb 
and gives me the error > dpkg: error processing /var/cache/apt/archives/libturbojpeg_1.1.90+svn733-0ubuntu4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libturbojpeg.so', which is also in package libjpeg-turbo62 1.1.90+svn702-0ubuntu1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libturbojpeg_1.1.90+svn733-0ubuntu4_amd64.deb

i delete this new repo from my list.
**Please help me fix it. thank you**

---

### Post by papibe on 2012-07-09
Hi eGelor.

Try this:
```
sudo apt-get autoclean

sudo apt-get autoremove

sudo apt-get clean

sudo apt-get update
```
Then try installing it again.

Regards.

---

### Post by eGelor on 2012-07-09
No nothing from the above worked. 
sudo apt-get autoremove gives me the same error
> The following packages have unmet dependencies:
 virtualgl-libs : Depends: libturbojpeg but it is not installed


and sudo apt-get -f autoremove 
> dpkg: error processing /var/cache/apt/archives/libturbojpeg_1.1.90+svn733-0ubuntu4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libturbojpeg.so', which is also in package libjpeg-turbo62 1.1.90+svn702-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libturbojpeg_1.1.90+svn733-0ubuntu4_amd64.deb


 All this are my fault cause i try to install an app that is not compatible on 12.04. Sot the libturbojpeg tries to overwrite the original lib. Please help. I only want to stop the installation of virtualgl.
 So i thing that i need to delete something, so the system will stop searching for libturbojpeg.
maybe in /var/cache/apt/archives

---

### Post by eGelor on 2012-07-10
ok > dpkg -r libjpeg-turbo62
fix my error and > apt-get -f remove
works ok.
Now updating my system.
thanks the live chat and **jokerdino**.

---

### Post by eGelor on 2012-07-10
For the history.
After that my nvidia crashed cause of virtualgl and bumblebee Optimus Nvidia support. remove it and reconfigure my nvidia 9200m fix the error. more than 2 hours now.

---

