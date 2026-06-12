---
title: "Errors with Ubuntu Software center"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by cblive25 on 2014-05-27
Hi everyone,

I am getting error with software center - unable to download any thing.


items cannot be installed or removed until the package catalog is repaired liber


Details mentioned below

```
installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libexttextcat0 (>= 2.2-8); however:
  Package libexttextcat0 is not installed.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-core (<< 1:4.2~) and is unpacked but not configured.
  Version of libreoffice-core to be configured is 1:3.5.7-0ubuntu5.
 ure (4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-core (<< 1:4.1.2~) and is installed.
  Version of libreoffice-core to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
No apport report written because MaxReports is reached already
 libreoffice-writer depends on libreoffice-base-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
 libreoffice-calc depends on libreoffice-base-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-emailmerge depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-emailmerge (<< 1:4.0.2~rc1) and is unpacked but not configured.
  Version of libreoffice-emailmerge to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:No apport report written because MaxReports is reached already


  Package libreoffice-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libreoffice-help-en-gb:
 libreoffice-help-en-gb depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-us:
No apport report written because MaxReports is reached already
 libreoffice-help-en-us depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mythes-en-us:
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libexttextcat0 (>= 2.2-8); however:
  Package libexttextcat0 is not installed.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-core (<< 1:4.2~) and is unpacked but not configured.
  Version of libreoffice-core to be configured is 1:3.5.7-0ubuntu5.
 ure (4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-core (<< 1:4.1.2~) and is installed.
  Version of libreoffice-core to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-human:
 libreoffice-style-human depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-style-human (<< 1:4.2~) and is unpacked but not configured.
  Version of libreoffice-style-human to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythes-en-us:
 mythes-en-us depends on libreoffice-core | openoffice.org-core (>= 1.9) | language-support-writing-en; however:
  Package libreoffice-core is not configured yet.
  Package openoffice.org-core is not installed.
  Package language-support-writing-en is not installed.
dpkg: error processing mythes-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-emailmerge depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-emailmerge (<< 1:4.0.2~rc1) and is unpacked but not configured.
  Version of libreoffice-emailmerge to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-common:
 libreoffice-common depends on libreoffice-style-default | libreoffice-style; however:
  Package libreoffice-style-default is not installed.
  Package libreoffice-style-human which provides libreoffice-style-default is not configured yet.
  Package libreoffice-style is not installed.
  Package libreoffice-style-human which provides libreoffice-style is not configured yet.
dpkg: error processing libreoffice-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-gb:
```


Also  i tried 


```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

but it gave me this response

```
addu@addu-Compaq-621:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-common : Breaks: libreoffice-core (< 1:4.2~) but 1:3.5.7-0ubuntu5 is installed
                      Breaks: libreoffice-emailmerge (< 1:4.0.2~rc1) but 1:3.5.7-0ubuntu5 is installed
                      Breaks: libreoffice-style-human (< 1:4.2~) but 1:3.5.7-0ubuntu5 is installed
 libreoffice-core : Depends: libexttextcat0 (>= 2.2-8) but it is not installed
 ure : Breaks: libreoffice-core (< 1:4.1.2~) but 1:3.5.7-0ubuntu5 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by cblive25 on 2014-05-27
after this i also tried 


```
addu@addu-Compaq-621:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-base-core libreoffice-calc libreoffice-core
  libreoffice-emailmerge libreoffice-math libreoffice-style-human
  libreoffice-writer python-uno
Suggested packages:
  libreoffice-base libopencl1 crystalcursors kde-icons-crystal libreoffice-gcj
  libreoffice-java-common default-jre gcj-jre openjdk-7-jre openjdk-6-jre
  sun-java5-jre sun-java6-jre java5-runtime jre
The following packages will be upgraded:
  libreoffice-base-core libreoffice-calc libreoffice-core
  libreoffice-emailmerge libreoffice-math libreoffice-style-human
  libreoffice-writer python-uno
8 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
14 not fully installed or removed.
Need to get 48.0 MB of archives.
After this operation, 34.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main libreoffice-writer i386 1:4.2.4~rc2-0ubuntu1~precise3 [9,761 kB]
Get:2 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main libreoffice-calc i386 1:4.2.4~rc2-0ubuntu1~precise3 [6,241 kB]
Get:3 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main libreoffice-base-core i386 1:4.2.4~rc2-0ubuntu1~precise3 [810 kB]
Get:4 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main libreoffice-math i386 1:4.2.4~rc2-0ubuntu1~precise3 [425 kB]
Get:5 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main libreoffice-core i386 1:4.2.4~rc2-0ubuntu1~precise3 [28.7 MB]
Get:6 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main libreoffice-emailmerge all 1:4.2.4~rc2-0ubuntu1~precise3 [70.1 kB]
Get:7 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main libreoffice-style-human all 1:4.2.4~rc2-0ubuntu1~precise3 [1,783 kB]
Get:8 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) precise/main python-uno i386 1:4.2.4~rc2-0ubuntu1~precise3 [288 kB]
Fetched 48.0 MB in 15min 35s (51.4 kB/s)                                       
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libexttextcat0 (>= 2.2-8); however:
  Package libexttextcat0 is not installed.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-core (<< 1:4.2~) and is unpacked but not configured.
  Version of libreoffice-core to be configured is 1:3.5.7-0ubuntu5.
 ure (4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-core (<< 1:4.1.2~) and is installed.
  Version of libreoffice-core to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                Package libreoffice-core is not configured yet.
 libreoffice-writer depends on libreoffice-base-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
 libreoffice-calc depends on libreoffice-base-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving uncoNo apport report written because the error message indicates its a followup error from a previous failure.
                                                             No apport report written because the error message indicates its a followup error from a previous failure.
       No apport report written because the error message indicates its a followup error from a previous failure.
                                 No apport report written because the error message indicates its a followup error from a previous failure.
                                                           No apport report written because the error message indicates its a followup error from a previous failure.
     No apport report written because the error message indicates its a followup error from a previous failure.
                               No apport report written because the error message indicates its a followup error from a previous failure.
                                                         No apport report written because the error message indicates its a followup error from a previous failure.
   nfigured
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-emailmerge depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-emailmerge (<< 1:4.0.2~rc1) and is unpacked but not configured.
  Version of libreoffice-emailmerge to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:3.5.7-0ubuntu5); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-gb:
 libreoffice-help-en-gb depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                    No apport report written because the error message indicates its a followup error from a previous failure.
                                              et.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-us:
 libreoffice-help-en-us depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythes-en-us:
 mythes-en-us depends on libreoffice-core | openoffice.org-core (>= 1.9) | language-support-writing-en; however:
  Package libreoffice-core is not configured yet.
  Package openoffice.org-core is not installed.
  Package language-support-writing-en is not installed.
dpkg: error processing mythes-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-human:
 libreoffice-style-human depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-common (1:4.2.4~rc2-0ubuntu1~precise3) breaks libreoffice-style-human (<< 1:4.2~) and is unpacked but not configured.
  Version of libreoffice-style-human to be configured is 1:3.5.7-0ubuntu5.
dpkg: error processing libreoffice-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-common:
 libreoffice-common depends on libreoffice-style-default | libreoffice-style; however:
  Package libreoffice-style-default is not installed.
  Package libreoffice-style-human which provides libreoffice-style-default is not configured yet.
  Package libreoffice-style is not installed.
  Package libreoffice-style-human which provides libreoffice-style is not configured yet.
dpkg: error processing libreoffice-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-l10n-en-gb:
 libreoffice-l10n-en-gb depends on libreoffice-common; however:
  Package libreoffice-common is not configured yet.
dpkg: error processing libreoffice-l10n-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-l10n-en-za:
 libreoffice-l10n-en-za depends on libreoffice-common; however:
  Package libreoffice-common is not configured yet.
dpkg: error processing libreoffice-l10n-en-za (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libreoffice-core
 libreoffice-base-core
 libreoffice-writer
 libreoffice-calc
 libreoffice-math
 libreoffice-emailmerge
 python-uno
 libreoffice-help-en-gb
 libreoffice-help-en-us
 mythes-en-us
 libreoffice-style-human
 libreoffice-common
 libreoffice-l10n-en-gb
 libreoffice-l10n-en-za
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ian-weisser on 2014-05-28
Well, it looks like you somehow hosed your locale settings.

Then you force-installed unsupported software (from a PPA)...software that needs your locale settings to function.

And there's a possibility that, since libexttextcat0 didn't even try to install, that you may have previously installed something that conflicts with it...or it may depend upon your locale settings.

1) I recommend against force-installing any software unless you really understand why it's necessary.

2) See [http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue](http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue) for how to fix your locale issue.

3) Try installing LibreOffice again once your locales are working.

Post all errors here.

---

