---
title: "Apt is not working."
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by amolshinde on 2012-11-02
Hi, all. I Cannot install any package in the server, As I am  newbie in Server. In Morning I found that some, I am not able to  install any package from command line in the server,Now every package is now manually downloaded packages and then installed in the server. Can any one in the forum tell me what is the issue and how could I resolve this issue.
I have tried to fix this issue by upgrading & updating Server, But did not worked, Below are the details of my server :-

OS:- Ubuntu 10.04.4 LTS \n \l (64 Bit)
Ram:- 2Gb

Below are the unknown errors:- 

[HTML]administrator@backupserver:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pidgin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 102 not upgraded.
32 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 33, in <module>
    from ALChacks import *
  File "/usr/share/apt-listchanges/ALChacks.py", line 32, in <module>
    sys.stderr.write(_("Can't set locale; make sure $LC_* and $LANG are correct!\n"))
NameError: name '_' is not defined
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_CTYPE = "UTF-8",
	LANG = "en_IN"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up shared-mime-info (0.71-1ubuntu2) ...
/var/lib/dpkg/info/shared-mime-info.postinst: line 13: 21935 Segmentation fault      update-mime-database.real /usr/share/mime
dpkg: error processing shared-mime-info (--configure):
 subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-browser:
 chromium-browser depends on libgtk2.0-0 (>= 2.20.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing chromium-browser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-codecs-ffmpeg:
 chromium-codecs-ffmpeg depends on chromium-browser (>= 4.0.203.0~); however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-codecs-ffmpeg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-browser-l10n:
 chromium-browser-l10n depends on chromium-browser (= 18.0.1025.151~r130497-0ubuntu0.10.04.No apport report written because the error message indicates its a followup error from a previous failure.
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
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         1); however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-browser-l10n (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libevdocument2:
 libevdocument2 depends on libgtk2.0-0 (>= 2.14.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libevdocument2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libevview2:
 libevview2 depends on libevdocument2 (>= 2.29.5); however:
  Package libevdocument2 is not configured yet.
 libevview2 depends on libgtk2.0-0 (>= 2.20.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libevview2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevdocument2 (>= 2.29.5); however:
  Package libevdocument2 is not configured yet.
 evince depends on libevview2 (>= 2.29.No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       5); however:
  Package libevview2 is not configured yet.
 evince depends on libgtk2.0-0 (>= 2.16.0); however:
  Package libgtk2.0-0 is not configured yet.
 evince depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libgtk2.0-0 (>= 2.20.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcalctool:
 gcalctool depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gcalctool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdict-1.0-6:
 libgdict-1.0-6 depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgdict-1.0-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on libgdict-1.0-6 (>= 2.23.90); however:
  Package libgdict-1.0-6 is not configured yet.
 gnome-utils depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-pixbuf:
 gtk2-engines-pixbuf depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is not configured yet.
 gtk2-engines-pixbuf depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gtk2-engines-pixbuf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libgtk2.0-0 (>= 2.14.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail18:
 libgail18 depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgail18 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnotify-dev:
 libnotify-dev depends on libgtk2.0-dev (>= 2.10); however:
  Package libgtk2.0-dev is not configured yet.
dpkg: error processing libnotify-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on libgtk2.0-0 (>= 2.16.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on libgtk2.0-0 (>= 2.10); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.2.0-7ubuntu4.4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up update-manager (1:0.134.12.1) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 245
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgtk2.0-0 (>= 2.14.0); however:
  Package libgtk2.0-0 is not configured yet.
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xulrunner-1.9.2:
 xulrunner-1.9.2 depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing xulrunner-1.9.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.2-dev:
 xulrunner-1.9.2-dev depends on xulrunner-1.9.2 (= 1.9.2.28+build1+nobinonly-0ubuntu0.10.04.1); however:
  Package xulrunner-1.9.2 is not configured yet.
 xulrunner-1.9.2-dev depends on libnotify-dev; however:
  Package libnotify-dev is not configured yet.
dpkg: error processing xulrunner-1.9.2-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on xulrunner-1.9.2; however:
  Package xulrunner-1.9.2 is not configured yet.
 icedtea6-plugin depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up libgweather-common (2.30.0-0ubuntu1.1) ...
No apport report written because MaxReports is reached already
                                                              locale: Cannot set LC_CTYPE to default locale: No such file or directory
dpkg: error processing libgweather-common (--configure):
 subprocess installed post-installation script returned error exit status 245
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgtk2.0-0 (>= 2.11.0); however:
  Package libgtk2.0-0 is not configured yet.
 libgweather1 depends on libgweather-common (>= 2.24.0); however:
  Package libgweather-common is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-galaxy:
 openoffice.org-style-galaxy depends on openoffice.org-core (>= 1:3.2.0~beta); however:
  Package openoffice.org-core is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing openoffice.org-style-galaxy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-style-default | openoffice.org-style; however:
  Package openoffice.org-style-default is not installed.
  Package openoffice.org-style-galaxy which provides openoffice.org-style-default is not configured yet.
  Package openoffice.org-style is not installed.
  Package openoffice.org-style-galaxy which provides openoffice.org-style is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 shared-mime-info
 libgtk2.0-0
 chromium-browser
 chromium-codecs-ffmpeg
 chromium-browser-l10n
 libevdocument2
 libevview2
 evince
 firefox
 gcalctool
 libgdict-1.0-6
 gnome-utils
 gtk2-engines-pixbuf
 libedataserverui1.2-8
 libgail18
 libgtk2.0-bin
 libgtk2.0-dev
 libnotify-dev
 network-manager-gnome
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-impress
 pidgin
 update-manager
 update-notifier
 xulrunner-1.9.2
 xulrunner-1.9.2-dev
 icedtea6-plugin
 libgweather-common
 libgweather1
 openoffice.org-style-galaxy
 openoffice.org-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/HTML]

I would be grateful if you guys help me to resolve this issue.

Thanks.

---

### Post by Bucky Ball on 2012-11-02
You have run:

```
sudo apt-get update
sudo apt-get upgrade
```

... in that order? Not the other way around?

---

### Post by amolshinde on 2012-11-02
[HTML]sudo apt-get update
sudo apt-get upgrade[/HTML]

yes i have updated this commands but still error is same.

---

### Post by amolshinde on 2012-11-02
> **amolshinde said:**
> [HTML]sudo apt-get update
sudo apt-get upgrade[/HTML]

yes i have updated this commands but still error is same.

Below are the logs which are generated:-

[HTML]administrator@backupserver:/var/log/apt$ tail -f history.log

Start-Date: 2012-11-02  12:11:58
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2012-11-02  12:12:00[/HTML]

[HTML]administrator@backupserver:/var/log/apt$ sudo tail -f term.log
 update-manager
 update-notifier
 xulrunner-1.9.2
 xulrunner-1.9.2-dev
 icedtea6-plugin
 libgweather-common
 libgweather1
 openoffice.org-style-galaxy
 openoffice.org-common
Log ended: 2012-11-02  12:12:00[/HTML]

---

### Post by dino99 on 2012-11-02
watch /etc/apt/sources.list to be sure you only use lucid archives (deactivate ppa if you have a few ones)

then clean the cache:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

then update again:
sudo apt-get update
sudo apt-get install -f

note: as your log shows, there is a conflict with libgtk, which might be not a genuine package , but installed by an extra archive like ppa.
note2: you need to pay attention at your locale settings   [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

### Post by amolshinde on 2012-11-02
> **dino99 said:**
> watch /etc/apt/sources.list to be sure you only use lucid archives (deactivate ppa if you have a few ones)

then clean the cache:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

then update again:
sudo apt-get update
sudo apt-get install -f

note: as your log shows, there is a conflict with libgtk, which might be not a genuine package , but installed by an extra archive like ppa.
note2: you need to pay attention at your locale settings   [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)
Thanks for reply, Below is  my source.list file.

###### Ubuntu Main Repos
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted 
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted 

###### Ubuntu Update Repos
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted 
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted 
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted 
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted 

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted universe

###### Ubuntu Update Repos
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe

Is it okay?

---

### Post by Bucky Ball on 2012-11-02
I don't think so. These are all archives and there is a lot missing compared to my /etc/apt/sources.list.

---

### Post by amolshinde on 2012-11-02
> **Bucky Ball said:**
> I don't think so. These are all archives and there is a lot missing compared to my /etc/apt/sources.list.
sudo apt-get clean
sudo apt-get autoclean

Only above command worked, but other's did not.

---

### Post by amolshinde on 2012-11-02
> **Bucky Ball said:**
> I don't think so. These are all archives and there is a lot missing compared to my /etc/apt/sources.list.
Thanks for reply, Does upgrading OS with Command "sudo apt-get  upgrade" harm packages of Servers?

---

### Post by dino99 on 2012-11-02
you miss some archives: multiverse, partner, medibuntu

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main universe restricted multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

i does not need deb-scr here, so i've removed them. The missing on your side are about sound mainly, but also microcode etc.

---

### Post by Bucky Ball on 2012-11-02
> **amolshinde said:**
> Does upgrading OS with Command "sudo apt-get  upgrade" harm packages of Servers?

The intention is just the opposite. It upgrades your apps and software to the latest available for your release, it does NOT upgrade your system to the next release of Ubuntu Server.

I don't deploy servers in any professional environment but I imagine some folks need to be super safe and take the 'if it ain't broke, don't fix it' approach once the servers are up and only go for security updates until the next LTS release. This way  (theoretically) everything will stay as is, but there is no avoiding human intervention and from that point human error is always possible!

---

### Post by amolshinde on 2012-11-02
> **dino99 said:**
> you miss some archives: multiverse, partner, medibuntu

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main universe restricted multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

i does not need deb-scr here, so i've removed them. The missing on your side are about sound mainly, but also microcode etc.
Thanks for your reply, I have pasted above lines in the source.list file. But :( did not worked.
While running command i found that when i was using tab key for auto complete , apt-get word was not coming in the Bash terminal, as i  have checked in other Ubuntu OS it was autocompleting. That means i have to reinstall apt package in the server, hope i am right?

---

### Post by amolshinde on 2012-11-02
> **dino99 said:**
> you miss some archives: multiverse, partner, medibuntu

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main universe restricted multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

i does not need deb-scr here, so i've removed them. The missing on your side are about sound mainly, but also microcode etc.

Thanks for your reply.

I have pasted above lines in source.list file, But did not worked :( While running apt-get command i found that bash is not auto completing command, but in other same version of OS i have check it is working there. Does it means that apt Package is corrupted ?

---

### Post by dino99 on 2012-11-02
> **amolshinde said:**
> Thanks for your reply.

I have pasted above lines in source.list file, But did not worked :( While running apt-get command i found that bash is not auto completing command, but in other same version of OS i have check it is working there. Does it means that apt Package is corrupted ?

your best helpfull friend is still named log(s)

---

### Post by amolshinde on 2012-11-03
Thanks for you reply, But i think apt package is corrupted, while running command on terminal, command is not auto completing, that means that apt packaged is  corrupted.

---

### Post by amolshinde on 2012-11-05
Hi, 
Above lines did not worked, below are the logs of apt:-

[http://paste.ubuntu.com/1334193/](http://paste.ubuntu.com/1334193/)

How can fix it.

---

### Post by amolshinde on 2012-11-05
Below are the Logs of apt:-

Term logs:-
[http://paste.ubuntu.com/1334193/](http://paste.ubuntu.com/1334193/)

---

