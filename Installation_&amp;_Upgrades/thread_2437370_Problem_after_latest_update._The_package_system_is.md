---
title: "Problem after latest update. The package system is broken."
date: 2020-02-22
forum: Installation &amp; Upgrades
---

### Post by Mrhihat on 2020-02-22
So I ran some updates and now there is some problems.

[I]**The package system is broken**
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

libqtermwidget5-0: Depends: libc6 (>= 2.15) but 2.30-0ubuntu3 is installed
                   Depends: libqt5core5a (>= 5.12.2) but 5.12.5+dfsg-8 is installed
                   Depends: libqt5gui5-gles (>= 5.7.0) but it is not installed
                   Depends: libqt5widgets5 (>= 5.0.2) but 5.12.5+dfsg-8 is installed
                   Depends: libstdc++6 (>= 5.2) but 10-20200211-1ubuntu1 is installed
                   Depends: libutf8proc2 (>= 1.3) but 2.4.0-2build2 is installed
                   Depends: qtermwidget5-data (= 0.14.1-2) but 0.14.1-0ubuntu3 is installed[/I]


Anyone can give me helping hand?

I have tried the sudo apt update, -f install and all that jazz to no avail.

[B]edit.
It might be of interest that I am running Lubuntu alongside with Ubuntu.

[/B]

---

### Post by deadflowr on 2020-02-22
*> Check if you are using third party repositories. I*
Are you using any 3rd party repositories?
What release is this?

---

### Post by Mrhihat on 2020-02-23
I was, but not any longer.
Release? the Latest, 20.04
seems like the problem is with 

 /var/cache/apt/archives/qtermwidget5-data_0.14.1-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kubuntold on 2020-02-24
Hi,

similar problem here. Updating Lubuntu daily says for qtermwidget-data:
  
/var/cache/apt/archives/qtermwidget5-data_0.14.1-2_all.deb

 trying to overwrite '/usr/share/qtermwidget5/translations/qtermwidget_ca.qm', which is also in package qtermwidget-l10n 0.14.1-0ubuntu3

and visual quality on the desktop is impaired, i,e., some kind of tearing on active elements.

---

### Post by pablosquared on 2020-02-24
I had a similar issue last week (Ubuntu 19.10). The issue arose because I had the "Proposed" repository enabled. I disabled it (via Synaptic / Settings / Repositories / Developer Options), reloaded the update check and the problem went away.

---

### Post by kubuntold on 2020-02-25
> **pablosquared said:**
> I had a similar issue last week (Ubuntu 19.10). The issue arose because I had the "Proposed" repository enabled. I disabled it (via Synaptic / Settings / Repositories / Developer Options), reloaded the update check and the problem went away.  Thanks for sharing, but I do not have proposed updates turned on.  Also I just noted that printing in libreoffice seems to be broken for me... may be related not sure though. Provides either empty exported .pdf files or garbage to the printer (which works fine printing pdfs).   

 Edit: This may be relevant to the problem: [https://answers.launchpad.net/ubuntu/+question/688946](https://answers.launchpad.net/ubuntu/+question/688946)  Will try fix from there now!  


Edit 2: Fix works and resolves dependency problem, see also: [https://bugs.launchpad.net/ubuntu/+source/qtermwidget/+bug/1864170](https://bugs.launchpad.net/ubuntu/+source/qtermwidget/+bug/1864170)

Edit3: Graphics and Printing still broken, though... some different (unknown) issue.

---

### Post by Impavidus on 2020-02-25
> **Mrhihat said:**
> 
I have tried the sudo apt update, -f install and all that jazz to no avail.
In that case the full output of sudo apt install -f might help.

> **Mrhihat said:**
> 
Release? the Latest, 20.04

I'm not sure 20.04 can be considered the latest release. It hasn't been released yet. In other words, inconsistencies are to be expected.

---

### Post by Mrhihat on 2020-03-06
Here is the output 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-5.3.0-29-generic linux-modules-5.3.0-29-generic
  linux-modules-extra-5.3.0-29-generic python3.7 python3.7-minimal
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  qtermwidget5-data
The following packages will be upgraded:
  qtermwidget5-data
1 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
8 not fully installed or removed.
Need to get 0 B/19,8 kB of archives.
After this operation, 54,3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 342364 files and directories currently installed.)
Preparing to unpack .../qtermwidget5-data_0.14.1-2_all.deb ...
Unpacking qtermwidget5-data (0.14.1-2) over (0.14.1-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/qtermwidget5-data_0.14.1-2_all.deb (--unpack):
 trying to overwrite '/usr/share/qtermwidget5/translations/qtermwidget_ca.qm', which is also in package qtermwidget-l10n 0.14.1-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/qtermwidget5-data_0.14.1-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

