---
title: "unable to install firefox"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2007-10-12
I had removed firefox from my fiesty install, after installing swiftfox browser. Now as I intend to upgrade to Gutsy, the Ubuntu-desktop meta packages needed to be installed, and firefox needs to be installed too.

I got some errors saying firefox could not be installed.

Here is the error: 

vishnumrao@vishnumrao-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gtk2-engines-murrine
Use 'apt-get autoremove' to remove them.
Suggested packages:
  latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 0B/9263kB of archives.
After unpacking 29.4MB of additional disk space will be used.
(Reading database ... 179363 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.6+1-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.6+1-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/firefox/defaults', which is also in package limewire-basic
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.6+1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
vishnumrao@vishnumrao-desktop:~$ 



Then I tried removing limewire-basic as it was the one conflicting package. Here is what I encountered.

vishnumrao@vishnumrao-desktop:~$ sudo apt-get remove limewire-basic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-gnome-support: Depends: firefox (= 2.0.0.6+1-0ubuntu1) but it is not going to be installed
  yelp: Depends: firefox (>= 1.5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
vishnumrao@vishnumrao-desktop:~$ 


How can I fix this? 

Thanks in advance.

---

### Post by scapalexis888 on 2007-10-12
Download the tarball from [www.mozilla.com](www.mozilla.com), unzip, copy into /usr/local, put a link to firefox in /usr/bin, and you are all set.

Also, i think the package is mozilla-firefox

---

### Post by vishnumrao on 2007-10-12
I am not too familiar with installing from tarball tar.gz files. Could you help me with the installation.

---

### Post by forestpixie on 2007-10-12
doesn't installing ubuntu desktop install firefox ? as far as I know it should just put it back to standard

```
sudo aptitude install ubuntu-desktop
```

---

### Post by vishnumrao on 2007-10-12
> **forestpixie said:**
> doesn't installing ubuntu desktop install firefox ? as far as I know it should just put it back to standard

```
sudo aptitude install ubuntu-desktop
```

Forestpixie,

I tried installing the ubuntu-desktop. Thats when synaptic said firefox needed to be installed as a dependency. It went ahead with installing the other dependencies but then firefox failed.

I have tried it. Does not work.

---

### Post by forestpixie on 2007-10-12
sorry - you didn't say you'd tried to install the desktop :(

what errors did you get when you tried? do it again and post it here maybe

---

### Post by vishnumrao on 2007-10-12
Forestpixie,

Following your advice in the other thread, i tried to install ubuntu-desktop package. Synaptic installed many of the packages but failed at the firefox one.

Here is the result when I try to install ubuntu-desktop package through apt-get

vishnumrao@vishnumrao-desktop:~$ sudo apt-get install ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-gnome-support: Depends: firefox (= 2.0.0.6+1-0ubuntu1) but it is not going to be installed
  yelp: Depends: firefox (>= 1.5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
vishnumrao@vishnumrao-desktop:~$ 

It refuses to proceed until the broken package is fixed.

Thanks for your help.

---

