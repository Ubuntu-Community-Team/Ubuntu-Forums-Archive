---
title: "package dependencies could not be resolved"
date: 2014-02-16
forum: Installation &amp; Upgrades
---

### Post by danielhughes77 on 2014-02-16
To my suprise I went to download inkscape and gimp and received this error message.  I have never had this problem on my other machines.

Error details:
The following packages have unmet dependencies:

inkscape: Depends: libaspell15 (>= 0.60.7~20110707) but 0.60.7~20110707-1 is to be installed
          Depends: libatkmm-1.6-1 (>= 2.22.1) but 2.22.6-1ubuntu1 is to be installed
          Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.5 is to be installed
          Depends: libcairo2 (>= 1.10.0) but 1.10.2-6.1ubuntu3 is to be installed
          Depends: libcairomm-1.0-1 (>= 1.6.4) but 1.10.0-1ubuntu1 is to be installed
          Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu9.1 is to be installed
          Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed
          Depends: libgc1c2 (>= 1:7.1) but 1:7.1-8ubuntu0.12.04.1 is to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
          Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is to be installed
          Depends: libglib2.0-0 (>= 2.24.0) but 2.32.4-0ubuntu1 is to be installed
          Depends: libglibmm-2.4-1c2a (>= 2.32.0) but 2.32.0-0ubuntu1 is to be installed
          Depends: libgnomevfs2-0 (>= 1:2.17.90) but 1:2.24.4-1ubuntu2.1 is to be installed
          Depends: libgomp1 (>= 4.2.1) but 4.6.3-1ubuntu5 is to be installed
          Depends: libgsl0ldbl (>= 1.9) but it is not going to be installed
          Depends: libgtk2.0-0 (>= 2.24.0) but 2.24.10-0ubuntu6 is to be installed
          Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not going to be installed
          Depends: libgtkspell0 (>= 2.0.10) but it is not going to be installed
          Depends: liblcms2-2 (>= 2.2+git20110628-2) but 2.2+git20110628-2ubuntu3.1 is to be installed
          Depends: libmagick++4 (>= 8:6.6.9.7) but 8:6.6.9.7-5ubuntu3.2 is to be installed
          Depends: libpango1.0-0 (>= 1.14.0) but 1.30.0-0ubuntu3.1 is to be installed
          Depends: libpangomm-1.4-1 (>= 2.27.1) but 2.28.4-1ubuntu1 is to be installed
          Depends: libpng12-0 (>= 1.2.13-4) but 1.2.46-3ubuntu4 is to be installed
          Depends: libpopt0 (>= 1.14) but 1.16-3ubuntu1 is to be installed
          Depends: libsigc++-2.0-0c2a (>= 2.0.2) but 2.2.10-0ubuntu2 is to be installed
          Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
          Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.6 is to be installed
          Depends: libxslt1.1 (>= 1.1.25) but 1.1.26-8ubuntu1.3 is to be installed
          Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed


Any ideas?

Regards

---

### Post by Ubi_one_2014 on 2014-02-17
pls post the output of:

cat /etc/apt/sources.list

---

### Post by danielhughes77 on 2014-02-17
could you quickly explain how to do this...sorry

---

### Post by Bucky Ball on 2014-02-17
Open a terminal and copy/paste:

```
cat /etc/apt/sources.list 
```

Hit 'enter' and post the output back here. ;)

Please always include the release and flavour you are using (Ubuntu 12.04, Xubuntu 13.10, whatever). Have you done a release upgrade lately?

Also, please run these commands, hitting enter between each:

 ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade 
```

Post back any and all errors. If none, try install Inkscape and Gimp again.

---

