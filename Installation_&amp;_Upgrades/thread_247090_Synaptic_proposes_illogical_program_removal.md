---
title: "Synaptic: proposes illogical program removal"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by SteveHoffmanUK on 2006-08-30
I would like to install the desktop publishing package Scribus using the Synaptic Package Manager. However, when I mark it for installation, it says that two packages must be removed:
libqt3c102-mt
mailwasher

I'm not bothered by the first one (only because I don't know what it is), but I am by the second one. Why does it propose to remove my anti-spam program Mailwasher? I use it and need it, and I can't see how it is at all related to a desktop publishing package.

Is there any way I can install Scribus but still preserve Mailwasher? There doesn't seem to be any way in Synaptic to opt-out of a proposed removal. Or is there?

---

### Post by Anonii on 2006-08-30
> **SteveHoffmanUK said:**
> I would like to install the desktop publishing package Scribus using the Synaptic Package Manager. However, when I mark it for installation, it says that two packages must be removed:
libqt3c102-mt
mailwasher

I'm not bothered by the first one (only because I don't know what it is), but I am by the second one. Why does it propose to remove my anti-spam program Mailwasher? I use it and need it, and I can't see how it is at all related to a desktop publishing package.

Is there any way I can install Scribus but still preserve Mailwasher? There doesn't seem to be any way in Synaptic to opt-out of a proposed removal. Or is there?

First, try downloading the .deb from here: 
[http://packages.ubuntu.com/dapper/graphics/scribus](http://packages.ubuntu.com/dapper/graphics/scribus)
(down in the box by the title Download scribus, chose your architecture and then a mirror, and then you got the .deb)
and then installing it with:

*sudo dpkg -i scrib*.deb*

But. if that also asks you to remove these packages, you have to post here the output of this command on the terminal, for further help:

*sudo apt-get install scribus*

---

### Post by SteveHoffmanUK on 2006-08-30
Many thanks for your help. Fell at the first hurdle.

I downloaded the package to my desktop then ran the terminal command:
```
steve@steve-desktop:~$ sudo dpkg -i scrib*.deb
Password:
dpkg: error processing scrib*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 scrib*.deb
steve@steve-desktop:~$

```

---

### Post by Anonii on 2006-08-30
Well, you get this error when there is no scrib*.deb, 
I guess you didnt go to the directory where scribus was downloaded right?

Go to your Desktop, using the cd command.

"cd Desktop" and then run the "sudo dpkg -i scribus*.deb"



Also please try "sudo aptitude install scribus"
and post the output here.

Thanks.

---

### Post by SteveHoffmanUK on 2006-08-30
OK; you can tell I'm new at this. Got to the right directory and got this:
```
steve@steve-desktop:~/Desktop$ sudo dpkg -i scrib*.deb
Password:
Selecting previously deselected package scribus.
(Reading database ... 102796 files and directories currently installed.)
Unpacking scribus (from scribus_1.2.4.1.dfsg-1ubuntu4_i386.deb) ...
dpkg: dependency problems prevent configuration of scribus:
 scribus depends on libqt3-mt (>= 3:3.3.5); however:
  Package libqt3-mt is not installed.
dpkg: error processing scribus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scribus
steve@steve-desktop:~/Desktop$
```

So then I went to the same website and downloaded libqt3-mt and then tried to install it:

```
steve@steve-desktop:~/Desktop$ sudo dpkg -i libqt3-mt*.deb
Selecting previously deselected package libqt3-mt.
dpkg: considering removing libqt3c102-mt in favour of libqt3-mt ...
dpkg: no, cannot remove libqt3c102-mt (--auto-deconfigure will help):
 mailwasher depends on libqt3c102-mt (>= 3:3.3.3)
  libqt3c102-mt is to be removed.
dpkg: regarding libqt3-mt_3.3.6-1ubuntu3_i386.deb containing libqt3-mt:
 libqt3-mt conflicts with libqt3c102-mt
  libqt3c102-mt (version 3:3.3.4-3) is installed.
dpkg: error processing libqt3-mt_3.3.6-1ubuntu3_i386.deb (--install):
 conflicting packages - not installing libqt3-mt
Errors were encountered while processing:
 libqt3-mt_3.3.6-1ubuntu3_i386.deb
steve@steve-desktop:~/Desktop$

```

Well, I guess that explains why Synaptic wants to uninstall Mailwasher, doesn't it? 

Any further suggestions?

---

### Post by SteveHoffmanUK on 2006-08-30
Sorry, forgot you also asked me to use sudo aptitude; this is what I got:

```
steve@steve-desktop:~/Desktop$ sudo aptitude install scribus
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  mailwasher
The following NEW packages will be automatically installed:
  libqt3-mt
The following packages will be automatically REMOVED:
  libqt3c102-mt
The following NEW packages will be installed:
  libqt3-mt
The following packages will be REMOVED:
  libqt3c102-mt
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 3152kB of archives. After unpacking 1331kB will be used.
The following packages have unmet dependencies:
  mailwasher: Depends: libqt3c102-mt (>= 3:3.3.3) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
mailwasher

Score is -301

Accept this solution? [Y/n/q/?]

```

Seem consistent, doesn't it?

---

### Post by Anonii on 2006-08-30
> **SteveHoffmanUK said:**
> OK; you can tell I'm new at this. Got to the right directory and got this:
```
steve@steve-desktop:~/Desktop$ sudo dpkg -i scrib*.deb
Password:
Selecting previously deselected package scribus.
(Reading database ... 102796 files and directories currently installed.)
Unpacking scribus (from scribus_1.2.4.1.dfsg-1ubuntu4_i386.deb) ...
dpkg: dependency problems prevent configuration of scribus:
 scribus depends on libqt3-mt (>= 3:3.3.5); however:
  Package libqt3-mt is not installed.
dpkg: error processing scribus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scribus
steve@steve-desktop:~/Desktop$
```

So then I went to the same website and downloaded libqt3-mt and then tried to install it:

```
steve@steve-desktop:~/Desktop$ sudo dpkg -i libqt3-mt*.deb
Selecting previously deselected package libqt3-mt.
dpkg: considering removing libqt3c102-mt in favour of libqt3-mt ...
dpkg: no, cannot remove libqt3c102-mt (--auto-deconfigure will help):
 mailwasher depends on libqt3c102-mt (>= 3:3.3.3)
  libqt3c102-mt is to be removed.
dpkg: regarding libqt3-mt_3.3.6-1ubuntu3_i386.deb containing libqt3-mt:
 libqt3-mt conflicts with libqt3c102-mt
  libqt3c102-mt (version 3:3.3.4-3) is installed.
dpkg: error processing libqt3-mt_3.3.6-1ubuntu3_i386.deb (--install):
 conflicting packages - not installing libqt3-mt
Errors were encountered while processing:
 libqt3-mt_3.3.6-1ubuntu3_i386.deb
steve@steve-desktop:~/Desktop$

```

Well, I guess that explains why Synaptic wants to uninstall Mailwasher, doesn't it? 

Any further suggestions?
Yes, it explains why :/

And unfortunately, I cant help you further. You could try to install this application, and then try to install mailwasher after that...

But I dont know the possible results of that...

Good Luck :]

---

### Post by SteveHoffmanUK on 2006-08-30
Anonii

Thanks very much for trying to help me and for your quick responses. It's what makes the Ubuntu forums so valuable!:cool:

---

### Post by SteveHoffmanUK on 2006-08-31
Anonii

Thought you would like to know that I wrote to Firetrust, the owners of the Mailwasher package, and they came back with a beta version of the program that uses the new module. I downloaded and installed it without a problem, so now I have both Mailwasher and Scribus working.

Sweet.:D 

Thanks again for your help.

---

### Post by Anonii on 2006-08-31
Thats great news :)

Good Luck in the future SteveHoffmanUK.

---

