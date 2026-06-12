---
title: "Locale"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by zar123 on 2011-02-21
[COLOR=Red]**Cannot update or install any package**[/COLOR]

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
i18n is not install or has been removes
cannot update or install anything (gets the same perl warning locale not set)
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
directory which should have i18n is empty

---

### Post by sikander3786 on 2011-02-21
Please run these commands in Terminal under Applications > Accessories sub-menu and post the complete outputs.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readibility purposes.

---

### Post by zar123 on 2011-02-23
> **sikander3786 said:**
> Please run these commands in Terminal under Applications > Accessories sub-menu and post the complete outputs.

```
sudo dpkg --configure -a
sudo apt-get install -f
```While posting, click the # icon in post menu and paste your text in between the generated ```
 tags for readibility purposes.
[CODE]
sudo dpkg --configure -a
Setting up postgresql-common (111) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
 * Starting PostgreSQL 8.4 database server                                       * perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
The PostgreSQL server failed to start. Please check the log output:
FATAL:  invalid value for parameter "lc_messages": "en_US.UTF-8"
                                                                         [fail]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-contrib-8.4:
 postgresql-contrib-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-contrib-8.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-8.4:
 postgresql-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-8.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-common
 postgresql-contrib-8.4
 postgresql-8.4
 postgresql


```

---

### Post by zar123 on 2011-02-23
> **sikander3786 said:**
> Please run these commands in Terminal under Applications > Accessories sub-menu and post the complete outputs.

```
sudo dpkg --configure -a
sudo apt-get install -f
```While posting, click the # icon in post menu and paste your text in between the generated ```
 tags for readibility purposes.
[CODE]
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up postgresql-common (111) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
 * Starting PostgreSQL 8.4 database server                                       * perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
The PostgreSQL server failed to start. Please check the log output:
FATAL:  invalid value for parameter "lc_messages": "en_US.UTF-8"
                                                                         [fail]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-8.4:
 postgresql-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-8.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-contrib-8.4:
 postgresql-contrib-8.4 depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
 postgresql-contrib-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-coNo apport report written because the error message indicates its a followup error from a previous failure.
                                                              No apport report written because the error message indicates its a followup error from a previous failure.
        No apport report written because MaxReports is reached already
                                                                      ntrib-8.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-common
 postgresql-8.4
 postgresql
 postgresql-contrib-8.4
localepurge: checking for existence of /var/cache/localepurge...
localepurge: checking for existence of /var/cache/localepurge/localelist...
localepurge: checking system for new locale ...
Some new locales have appeared on your system:

en@boldquot en@quot 

They will not be touched until you reconfigure localepurge
with the following command:

    dpkg-reconfigure localepurge

localepurge: processing locale files ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: processing man pages ...
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: processing Gnome files ...
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: processing Omf files ...
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: processing KDE files ...
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


```
```

dpkg -reconfigure localepurge

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure must be run as root


```

---

### Post by zar123 on 2011-02-23
> **zar123 said:**
> ```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up postgresql-common (111) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
 * Starting PostgreSQL 8.4 database server                                       * perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
The PostgreSQL server failed to start. Please check the log output:
FATAL:  invalid value for parameter "lc_messages": "en_US.UTF-8"
                                                                         [fail]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-8.4:
 postgresql-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-8.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-contrib-8.4:
 postgresql-contrib-8.4 depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
 postgresql-contrib-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-coNo apport report written because the error message indicates its a followup error from a previous failure.
                                                              No apport report written because the error message indicates its a followup error from a previous failure.
        No apport report written because MaxReports is reached already
                                                                      ntrib-8.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-common
 postgresql-8.4
 postgresql
 postgresql-contrib-8.4
localepurge: checking for existence of /var/cache/localepurge...
localepurge: checking for existence of /var/cache/localepurge/localelist...
localepurge: checking system for new locale ...
Some new locales have appeared on your system:

en@boldquot en@quot 

They will not be touched until you reconfigure localepurge
with the following command:

    dpkg-reconfigure localepurge

localepurge: processing locale files ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: processing man pages ...
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: processing Gnome files ...
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: processing Omf files ...
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: processing KDE files ...
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


``````

dpkg -reconfigure localepurge

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure must be run as root


```
```

my be this will be of little help
locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX


```

---

### Post by sikander3786 on 2011-02-23
Thanks for the outputs. Try removing/purging your offensive packages.

```
sudo apt-get remove --purge postgresql-common postgresql-contrib-8.4 postgresql-8.4 postgresql
```

Or if that doesn't work,

```
sudo apt-get install --reinstall postgresql-common postgresql-contrib-8.4 postgresql-8.4 postgresql
```

---

### Post by zar123 on 2011-02-23
> **sikander3786 said:**
> Thanks for the outputs. Try removing/purging your offensive packages.

```
sudo apt-get remove --purge postgresql-common postgresql-contrib-8.4 postgresql-8.4 postgresql
```Or if that doesn't work,

```
sudo apt-get install --reinstall postgresql-common postgresql-contrib-8.4 postgresql-8.4 postgresql
```

```

 sudo apt-get remove --purge postgresql-common postgresql -contrib-8.4 postgresql-8.4 postgresql
[sudo] password for far: 
E: Opening configuration file ontrib-8.4 - ifstream::ifstream (2: No such file or directory)
far@far-OptiPlex-GX270:~$ sudo apt-get remove --purge postgresql-common postgresql-contrib-8.4 postgresql-8.4 postgresql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  postgresql-client-8.4 libossp-uuid16 postgresql-client-common libpq5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  postgresql* postgresql-8.4* postgresql-common* postgresql-contrib-8.4*
0 upgraded, 0 newly installed, 4 to remove and 42 not upgraded.
4 not fully installed or removed.
After this operation, 12.2MB disk space will be freed.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 291170 files and directories currently installed.)
Removing postgresql ...
Removing postgresql-contrib-8.4 ...
Removing postgresql-8.4 ...
 * Stopping PostgreSQL 8.4 database server                               [ OK ] 
Purging configuration files for postgresql-8.4 ...
Dropping cluster main...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
dpkg: warning: while removing postgresql-8.4, directory '/usr/share/postgresql/8.4/tsearch_data' not empty so not removed.
Removing postgresql-common ...
Purging configuration files for postgresql-common ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct


```

```



```

---

### Post by sikander3786 on 2011-02-24
Seems like the packages were removed successfully. That outputs isn't complete I think.

Now try installing those packages.

```
sudo apt-get install postgresql-common postgresql-contrib-8.4 postgresql-8.4 postgresql
```

---

### Post by zar123 on 2011-02-25
> **sikander3786 said:**
> Seems like the packages were removed successfully. That outputs isn't complete I think.

Now try installing those packages.

```
sudo apt-get install postgresql-common postgresql-contrib-8.4 postgresql-8.4 postgresql
```
```
rib-8.4 postgresql-8.4 postgresql
[sudo] password for far: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-common is already the newest version.
postgresql is already the newest version.
postgresql-8.4 is already the newest version.
postgresql-contrib-8.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.

```

[COLOR=Red]directory which should have i18n is empty[/COLOR]
"en_US.UTF-8" does not exist on my computer
"en_CA.UTF-8" is there
"en_GB.UTF-8" is there
but "en_US.UTF-8" is not on my computer

---

