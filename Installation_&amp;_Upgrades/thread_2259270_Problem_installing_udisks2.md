---
title: "Problem installing udisks2"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by ster2 on 2015-01-03
After an upgrade from Kubuntu 12.04 to 14.04, I have problems with several programs starting up or running really slow (like Dolphin, Kate,...) I start with a quick description, my question is at the bottom.Starting Dolphin or Kate in a Konsole results in the following output:

```

Object::connect: No such signal org::freedesktop::UPower::DeviceAdded(QDBusObjectPath)
Object::connect: No such signal org::freedesktop::UPower::DeviceRemoved(QDBusObjectPath)
Bus::open: Can not get ibus-daemon's address. IBusInputContext::createInputContext: no connection to ibus-daemon 
Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.NoReply"  "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." 
Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.NoReply"  "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

```

where the last 2 lines are repeated several times.  After sometimes multiple minutes, the application then pops up. After searching on several forums I found that I had to install udisks2. However installing udisks2 in apper or via apt-get fails each time when it needs to remove the package libclucene0ldbl.I isolated the removal of libclucene0ldbl by running sudo apt-get autoremove resulting in the following output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:  libclucene0ldbl0 
upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
513 not fully installed or removed.
After this operation, 1,249 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 199076 files and directories currently installed.)
Removing libclucene0ldbl (0.9.21b-2) ...

```

after a time out limit is passed I get the further output:
```

dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/libclucene0ldbl.postrm): Input/output error
dpkg: error processing package libclucene0ldbl (--remove): subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing: libclucene0ldblE: Sub-process /usr/bin/dpkg returned an error code (1)
The removal fails due to an Input/output error.  

```

I wonder whether this error is also due to the failure of enumerating Udisks2 objects. That would mean I am in a loop:  to solve the enumeration failure I have to install udisks2.  To install udisks2 I have to solve the enumeration failure.Any suggestions?Thanks in advance.

---

### Post by Dennis N on 2015-01-03
You should already have udisks2. It's in the default install. Check with:

```
apt-cache policy udisks2
```

---

### Post by ster2 on 2015-01-03
Running   apt-cache policy udisks2 results in:

```

udisks2:
  Installed: 2.1.3-1 
  Candidate: 2.1.3-1 
  Version table: 
 *** 2.1.3-1 0 
      500 http://be.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages 
      100 /var/lib/dpkg/status

```

However apper with the filter of only installed applications indicates only libudisks2-0 is installed and not udisks2. I it is installed what would then the solution be for the failure of enumerating the Udisks2 objects? And any suggestion for removing libclucene0ldbl? Thanks for your quick reply

---

### Post by ster2 on 2015-01-03
I did a package query:

```

dpkg-query -l udisks2

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/    Name                                                                  Version                                      Architecture                               Description
+++-=================================-=====================-=====================-========================================================================
iU     udisks2                                                                2.1.3-1                                      amd64                                      D-BUS service to access and manipulate storage devices


```

According to what I read this means that udisks2 is scheduled to be installed, but is not installed yet.  It is in the status of 'Unpacked'.

---

### Post by ster2 on 2015-01-03
Another update: I removed manually the file /var/lib/dpkg/info/libclucene0ldbl.postrm.  After that I succeeded in removing the libclucene package (dpkg --remove).  After that I retried the installation of udisks2:
 

 ```

sudo apt-get install udisks2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
udisks2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
512 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up docbook-xml (4.5-7.2) ...
dpkg: error processing package docbook-xml (--configure):
 cannot compute MD5 hash for file '/etc/sgml/docbook-xml/4.3/dbgenent.mod': failed to read (Input/output error)
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on docbook-xml; however:
  Package docbook-xml is not configured yet.

dpkg: error processing package kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on kdoctools (= 4:4.13.3-0ubuntu0.2); however:
  Package kdoctools is not configured yet.

dpkg: error processing package kdelibs5-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on kdelibs5-plugins (>= 4:4.13.3); however:
  Package kdelibs5-plugins is not configured yet.

dpkg: error processing package kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of polkit-kde-1:
 polkit-kde-1 depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error proceNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                           No apport report written because the error message indicates its a followup error from a previous failure.
                                                                       No apport report written because MaxReports is reached already
                                                                                                                                     No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                                                                                                   No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                                                                                                               No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
                                                                                             No apport report written because MaxReports is reached already
                                                                                                                                                           ssing package polkit-kde-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepimdbusinterfaces4:
 libkdepimdbusinterfaces4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing package libkdepimdbusinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcalendarsupport4:
 libcalendarsupport4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libcalendarsupport4 depends on libkdepimdbusinterfaces4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepimdbusinterfaces4 is not configured yNo apport report written because MaxReports is reached already
                                                                                                                    No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
                                                                                  No apport report written because MaxReports is reached already
                                                                                                                                                No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                                                                                                              No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                                                                                                          No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                                                                                                        et.

dpkg: error processing package libcalendarsupport4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpimcommon4:
 libpimcommon4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing package libpimcommon4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessagecore4:
 libmessagecore4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libmessagecore4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package libmessagecore4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libincidenceeditorsng4:
 libincidenceeditorsng4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libincidenceeditorsng4 depends on libcalendarsupport4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libcalendarsupport4 is not configured yet.
 libincidenceeditorsng4 depends on libkdepimdbusinterfaces4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepimdbusinterfaces4 is not configured yet.

dpkg: error processing package libincidenceeditorsng4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessageviewer4:
 libmessageviewer4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libmessageviewer4 depends on libmessagecore4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessagecore4 is not configured yet.
 libmessageviewer4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package libmessageviewer4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtemplateparser4:
 libtemplateparser4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libtemplateparser4 depends on libmessagecore4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessagecore4 is not configured yet.
 libtemplateparser4 depends on libmessageviewer4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessageviewer4 is not configured yet.
 libtemplateparser4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package libtemplateparser4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessagecomposer4:
 libmessagecomposer4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libmessagecomposer4 depends on libmessagecore4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessagecore4 is not configured yet.
 libmessagecomposer4 depends on libmessageviewer4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessageviewer4 is not configured yet.
 libmessagecomposer4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.
 libmessagecomposer4 depends on libtemplateparser4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libtemplateparser4 is not configured yet.

dpkg: error processing package libmessagecomposer4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmailcommon4:
 libmailcommon4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libmailcommon4 depends on libincidenceeditorsng4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libincidenceeditorsng4 is not configured yet.
 libmailcommon4 depends on libmessagecomposer4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessagecomposer4 is not configured yet.
 libmailcommon4 depends on libmessagecore4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessagecore4 is not configured yet.
 libmailcommon4 depends on libmessageviewer4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessageviewer4 is not configured yet.
 libmailcommon4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.
 libmailcommon4 depends on libtemplateparser4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libtemplateparser4 is not configured yet.

dpkg: error processing package libmailcommon4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepim4:
 libkdepim4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libkdepim4 depends on libmailcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmailcommon4 is not configured yet.
 libkdepim4 depends on libmessagecore4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessagecore4 is not configured yet.
 libkdepim4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package libkdepim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmailimporter4:
 libmailimporter4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libmailimporter4 depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.

dpkg: error processing package libmailimporter4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ktimetracker:
 ktimetracker depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package ktimetracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-kresources:
 kdepim-kresources depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 kdepim-kresources depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.

dpkg: error processing package kdepim-kresources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnoteshared4:
 libnoteshared4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libnoteshared4 depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.
 libnoteshared4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package libnoteshared4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knotes:
 knotes depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 knotes depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 knotes depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.
 knotes depends on libnoteshared4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libnoteshared4 is not configured yet.
 knotes depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package knotes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libksieveui4:
 libksieveui4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libksieveui4 depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.
 libksieveui4 depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package libksieveui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmessagelist4:
 libmessagelist4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libmessagelist4 depends on libmessagecore4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmessagecore4 is not configured yet.

dpkg: error processing package libmessagelist4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmail:
 kmail depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kmail depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 kmail depends on libcalendarsupport4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libcalendarsupport4 is not configured yet.
 kmail depends on libincidenceeditorsng4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libincidenceeditorsng4 is not configured yet.
 kmail depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.
 kmail depends on libksieveui4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libksieveui4 is not configured yet.
 kmail depends on libmailcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmailcommon4 is not configured yet.
 kmail depends on libmailimporter4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libmailimporter4 is not configured yet.
 kmail depends on libmessagecomposer4 (= 4:4.13.3-0ubuntu0.1); however:
 
dpkg: error processing package kmail (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of akregator:
 akregator depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 akregator depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.

dpkg: error processing package akregator (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kontact:
 kontact depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kontact depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.
 kontact depends on libkdepimdbusinterfaces4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepimdbusinterfaces4 is not configured yet.
 kontact depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing package kontact (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libeventviews4:
 libeventviews4 depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 libeventviews4 depends on libcalendarsupport4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libcalendarsupport4 is not configured yet.
 libeventviews4 depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.

dpkg: error processing package libeventviews4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of korganizer:
 korganizer depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 korganizer depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 korganizer depends on libcalendarsupport4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libcalendarsupport4 is not configured yet.
 korganizer depends on libeventviews4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libeventviews4 is not configured yet.
 korganizer depends on libincidenceeditorsng4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libincidenceeditorsng4 is not configured yet.
 korganizer depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.
 korganizer depends on libkdepimdbusinterfaces4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepimdbusinterfaces4 is not configured yet.
 korganizer depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package korganizer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kaddressbook:
 kaddressbook depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kaddressbook depends on kdepim-runtime (>= 4:4.10.2); however:
  Package kdepim-runtime is not configured yet.
 kaddressbook depends on libkdepim4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libkdepim4 is not configured yet.
 kaddressbook depends on libpimcommon4 (= 4:4.13.3-0ubuntu0.1); however:
  Package libpimcommon4 is not configured yet.

dpkg: error processing package kaddressbook (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plasma-dataengines-workspace:
 plasma-dataengines-workspace depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing package plasma-dataengines-workspace (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plasma-widgets-workspace:
 plasma-widgets-workspace depends on plasma-dataengines-workspace (= 4:4.11.11-0ubuntu0.2); however:
  Package plasma-dataengines-workspace is not configured yet.
 plasma-widgets-workspace depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing package plasma-widgets-workspace (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plasma-desktop:
 plasma-desktop depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 plasma-desktop depends on plasma-widgets-workspace (= 4:4.11.11-0ubuntu0.2); however:
  Package plasma-widgets-workspace is not configured yet.

dpkg: error processing package plasma-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kinfocenter:
 kinfocenter depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kinfocenter (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-style-oxygen:
 kde-style-oxygen depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kde-style-oxygen (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plasma-netbook:
 plasma-netbook depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 plasma-netbook depends on plasma-widgets-workspace (= 4:4.11.11-0ubuntu0.2); however:
  Package plasma-widgets-workspace is not configured yet.

dpkg: error processing package plasma-netbook (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-workspace-bin:
 kde-workspace-bin depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-workspace-bin depends on kde-style-oxygen (= 4:4.11.11-0ubuntu0.2); however:
  Package kde-style-oxygen is not configured yet.
 kde-workspace-bin depends on plasma-desktop (= 4:4.11.11-0ubuntu0.2) | plasma-netbook (= 4:4.11.11-0ubuntu0.2) | plasma-active; however:
  Package plasma-desktop is not configured yet.
  Package plasma-netbook is not configured yet.
  Package plasma-active is not installed.

dpkg: error processing package kde-workspace-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package k3b (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of k3b-i18n:
 k3b-i18n depends on k3b; however:
  Package k3b is not configured yet.

dpkg: error processing package k3b-i18n (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of language-pack-kde-en:
 language-pack-kde-en depends on k3b-i18n; however:
  Package k3b-i18n is not configured yet.

dpkg: error processing package language-pack-kde-en (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of amarok:
 amarok depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package amarok (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-pykde4:
 python3-pykde4 depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 python3-pykde4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing package python3-pykde4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qapt-batch:
 qapt-batch depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package qapt-batch (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python3-pykde4; however:
  Package python3-pykde4 is not configured yet.
 software-properties-kde depends on qapt-batch; however:
  Package qapt-batch is not configured yet.

dpkg: error processing package software-properties-kde (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apper:
 apper depends on software-properties-kde; however:
  Package software-properties-kde is not configured yet.
 apper depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package apper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package konsole (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apport-kde:
 apport-kde depends on python3-pykde4; however:
  Package python3-pykde4 is not configured yet.

dpkg: error processing package apport-kde (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdesudo:
 kdesudo depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kdesudo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apturl-kde:
 apturl-kde depends on python3-pykde4; however:
  Package python3-pykde4 is not configured yet.
 apturl-kde depends on kdesudo; however:
  Package kdesudo is not configured yet.
 apturl-kde depends on qapt-batch; however:
  Package qapt-batch is not configured yet.
 apturl-kde depends on software-properties-kde (>= 0.75.2); however:
  Package software-properties-kde is not configured yet.

dpkg: error processing package apturl-kde (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ark:
 ark depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package ark (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kio-audiocd:
 kio-audiocd depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kio-audiocd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of audiocd-kio:
 audiocd-kio depends on kio-audiocd; however:
  Package kio-audiocd is not configured yet.

dpkg: error processing package audiocd-kio (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 docbook-xml
 kdoctools
 kdelibs5-plugins
 kde-runtime
 polkit-kde-1
 kdepim-runtime
 libkdepimdbusinterfaces4
 libcalendarsupport4
 libpimcommon4
 libmessagecore4
 libincidenceeditorsng4
 libmessageviewer4
 libtemplateparser4
 libmessagecomposer4
 libmailcommon4
 libkdepim4
 libmailimporter4
 ktimetracker
 kdepim-kresources
 libnoteshared4
 knotes
 libksieveui4
 libmessagelist4
 kmail
 akregator
 kontact
 libeventviews4
 korganizer
 kaddressbook
 plasma-dataengines-workspace
 plasma-widgets-workspace
 plasma-desktop
 kinfocenter
 kde-style-oxygen
 plasma-netbook
 kde-workspace-bin
 k3b
 k3b-i18n
 language-pack-kde-en
 amarok
 python3-pykde4
 qapt-batch
 software-properties-kde
 apper
 konsole
 apport-kde
 kdesudo
 apturl-kde
 ark
 kio-audiocd
 audiocd-kio
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The first error is the failure to read /etc/sgml/docbook-xml/4.3/dbgenent.mod.  The file however exists.  Again I have the suspicion that the IO-problem is related to the fact that udisks2 is not installed.

---

