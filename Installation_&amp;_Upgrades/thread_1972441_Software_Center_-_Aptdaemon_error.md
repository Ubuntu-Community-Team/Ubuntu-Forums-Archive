---
title: "Software Center - Aptdaemon error"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by Benni Tampubolon on 2012-05-03
Whenever I try to open software source this happening to me, before that i was change my repos

> 
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 202, in _process_transaction
    self.fix_incomplete_install(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 867, in fix_incomplete_install
    with self._frozen_status():
  File "/usr/lib/python2.7/contextlib.py", line 17, in __enter__
    return self.gen.next()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1013, in _frozen_status
    frozen_dir = tempfile.mkdtemp(prefix="aptdaemon-frozen-status")
  File "/usr/lib/python2.7/tempfile.py", line 317, in mkdtemp
    dir = gettempdir()
  File "/usr/lib/python2.7/tempfile.py", line 261, in gettempdir
    tempdir = _get_default_tempdir()
  File "/usr/lib/python2.7/tempfile.py", line 208, in _get_default_tempdir
    ("No usable temporary directory found in %s" % dirlist))
IOError: [Errno 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', '/']
im new with ubuntu, so i hope somebody can help me fix this problem.. thanks

---

### Post by Benni Tampubolon on 2012-05-04
so, already fix my aptdaemon after check my dpkg

after that i try update and when i try to upgrade i got this message:

> 
W: Duplicate sources.list entry [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-mozilla-daily_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-mozilla-daily_ppa_ubuntu_dists_precise_main_binary-i386_Packages)


anyone know how to fix this problem? thanks

---

### Post by plucky on 2012-05-04
> **Benni Tampubolon said:**
> so, already fix my aptdaemon after check my dpkg

after that i try update and when i try to upgrade i got this message:



anyone know how to fix this problem? thanks

Post output from a terminal for (CTRL + ALT + T)```
cat /etc/apt/sources.list
``` and ```
cat /etc/apt/sources.list.d/*.list
```

---

### Post by Benni Tampubolon on 2012-05-04
hi.. this is my sources.list:
> 
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise main restricted universe multiverse

###### Ubuntu Update Repos
deb [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise-security main restricted universe multiverse
deb [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse
deb [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise-security main restricted universe multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse 
deb-src [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

#### Gwibber (Daily) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) precise main

#### LibreOffice - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main

#### Medibuntu - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb [http://packages.medibuntu.org/precise](http://packages.medibuntu.org/precise) free non-free 

#### Mozilla Daily Build Team - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) precise main

#### Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) precise main

#### X Updates - [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main


####### 3rd Party Source Repos

#### Gwibber (Daily) (Source) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) precise main

#### LibreOffice (Source) - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main

#### Medibuntu (Source) - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src [http://packages.medibuntu.org/precise](http://packages.medibuntu.org/precise) free non-free 

#### Mozilla Daily Build Team (Source) - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) precise main

#### Ubuntu Tweak (Source) - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) precise main

#### X Updates (Source) - [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main


and my sources.list.d
> 
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/ryzom/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/ryzom/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free #Skype
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) precise main
deb [http://ppa.launchpad.net/wfg/0ad/ubuntu](http://ppa.launchpad.net/wfg/0ad/ubuntu) precise main
deb-src [http://ppa.launchpad.net/wfg/0ad/ubuntu](http://ppa.launchpad.net/wfg/0ad/ubuntu) precise main


i really hope u can help me, thank you so much...

---

### Post by plucky on 2012-05-04
> deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) precise main


These two in the sources.list.d folder are the same as the "#### Mozilla Daily Build Team" in your 3rd party Binary repostories and 3rd Party Source repositories.

Remove the ones in the sources.list.d folder.

Good Luck

---

### Post by Benni Tampubolon on 2012-05-04
thank you.. is it okay to remove the medibuntu in sources.list.d too?

---

### Post by plucky on 2012-05-04
Yes,as they are also duplicated.

---

