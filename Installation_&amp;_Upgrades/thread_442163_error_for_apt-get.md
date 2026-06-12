---
title: "error for apt-get"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by mailbinoy on 2007-05-13
babu@xxxxxxx:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgsasl7 libmailutils1 setserial wacom-tools vdr
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqt4-ruby1.8
The following NEW packages will be installed:
  libqt4-ruby1.8
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/112kB of archives.
After unpacking 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 168984 files and directories currently installed.)
Unpacking libqt4-ruby1.8 (from .../libqt4-ruby1.8_1.4.6-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqt4-ruby1.8_1.4.6-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/ruby/1.8/Qt/qtruby.rb', which is also in package libqt0-ruby1.8-qt4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-ruby1.8_1.4.6-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cant install any packages now. HELP

---

### Post by kmslinux on 2007-05-13
Did you need to 'apt-get install -f'?
Also, I think the correct command is 'apt-get -f install'

---

### Post by mailbinoy on 2007-05-13
apt-get install -f and apt-get -f install are the same as far as i know. 
not sure what exactly i installed but it was related to qt-ruby. and it said that there was a error and i needed to run apt-get -f install

---

### Post by mailbinoy on 2007-05-13
nevermind fixed it . removed all libqt* packages from the synaptic


thanks

---

### Post by taurus on 2007-05-13
Try something like

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

