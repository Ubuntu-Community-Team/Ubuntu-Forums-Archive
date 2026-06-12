---
title: "VirtualBox OSE keeps failing"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by psycho5 on 2010-09-30
Guys, I try to install virtualbox through software center, but it just doesn't install.

```

installArchives() failed: Selecting previously deselected package virtualbox-ose.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 191262 files and directories currently installed.)
Unpacking virtualbox-ose (from .../virtualbox-ose_3.2.8-dfsg-2ubuntu1_i386.deb) ...
Unpacking virtualbox-ose-dkms (from .../virtualbox-ose-dkms_3.2.8-dfsg-2ubuntu1_all.deb) ...
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
Removing obsolete module vboxnetflt version  3.2.8
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/vboxnetflt/3.2.8/source/dkms.conf does not represent
a valid dkms.conf file.
dpkg: error processing /var/cache/apt/archives/virtualbox-ose-dkms_3.2.8-dfsg-2ubuntu1_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 5
No apport report written because MaxReports is reached already
Selecting previously deselected package virtualbox-ose-qt.
Unpacking virtualbox-ose-qt (from .../virtualbox-ose-qt_3.2.8-dfsg-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-ose-dkms_3.2.8-dfsg-2ubuntu1_all.deb
Setting up virtualbox-ose (3.2.8-dfsg-2ubuntu1) ...
 * Stopping VirtualBox kernel modules
   ...done.
 * Starting VirtualBox kernel modules
 * No suitable module for running kernel found
   ...fail!
invoke-rc.d: initscript virtualbox-ose, action "restart" failed.
Processing triggers for python-central ...
Setting up virtualbox-ose-qt (3.2.8-dfsg-2ubuntu1) ...

```

whats wrong? it seems like it can't find a suitable module for running kernel... shouldn't it auto install from the software center? this is a clean install... synaptic shows no virtualbox packages on my system.

---

### Post by lukeiamyourfather on 2010-09-30
What kernel and version of Ubuntu are you running?

```
uname -a
```

---

### Post by bachinchi on 2010-09-30
You can also try non-free version of VirtualBox. Instructions here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by psycho5 on 2010-10-01
Linux oj-desktop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

---

### Post by lukeiamyourfather on 2010-10-01
> **psycho5 said:**
> Linux oj-desktop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

The kernel on my up to date Lucid system is 2.6.32 series, not 2.6.35 series. Is that a kernel you compiled or a beta version of Ubuntu? VirtualBox compiles kernel modules that are required for it to run. If the kernel headers are not installed and/or that kernel isn't supported then it won't work.

---

### Post by SeijiSensei on 2010-10-01
He's running a Maverick beta.

OP, try this.  First there isn't yet a VB package for Maverick, so you'll need to to use the one for Lucid.

sudo nano /etc/apt/sources.list

Navigate to the bottom of the file and add the line:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free
Then Ctrl-X, "Y" to save and exit.

Now get the key for the VB repository and install it like this:

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

3)  sudo apt-get update 

4)  sudo apt-get install virtualbox-3.2

Worked for me just now.  I intended to install VB onto my Maverick build; you gave me the incentive to do so.  I just started my Win7 machine, and it all works as advertised.

Instructions come from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by psycho5 on 2010-10-02
> **SeijiSensei said:**
> He's running a Maverick beta.

OP, try this.  First there isn't yet a VB package for Maverick, so you'll need to to use the one for Lucid.

sudo nano /etc/apt/sources.list

Navigate to the bottom of the file and add the line:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free
Then Ctrl-X, "Y" to save and exit.

Now get the key for the VB repository and install it like this:

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

3)  sudo apt-get update 

4)  sudo apt-get install virtualbox-3.2

Worked for me just now.  I intended to install VB onto my Maverick build; you gave me the incentive to do so.  I just started my Win7 machine, and it all works as advertised.

Instructions come from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Thanks.

---

### Post by leperisland on 2010-11-08
Hi there this worked for me too so many thanks!

This all started when I was trying out kernel 2.6.35-23 to sort out a hibernation problem. I'm now a little wary of trying that kernel again - do you think I'll have any more problems?

Thanks,

Caroline

---

