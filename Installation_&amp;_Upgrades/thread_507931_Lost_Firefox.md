---
title: "Lost Firefox"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by StewD on 2007-07-23
Hi

I ran one of Ubuntu's standard updates (that flash up from the white star in orange square icon near the date/time at the top right of the screen). It stopped half way through with an error, I think because FireFox was open on another desktop.

Since then I can not open Firefox. If I start Update Manager, I get told to run "sudo apt-get install -f" from a terminal, or "Synaptic". I can't get either of these to work. Following instructions from another posting I've tried to reinstall Firefox but get just about the same error messages. The reinstall followed these instructions:

```
cd /usr/lib
sudo rm -r mozilla-firefox
sudo apt-get update
sudo apt-get install mozilla-firefox

then you should have a fresh installation of firefox.

```

The error message I get from the terminal when running "sudo apt-get install -f" is:

```
stew@Fileserver1:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libktnef1 linux-headers-2.6.20-15-generic libflac++5c2 python-ctypes
  linux-headers-2.6.20-15 libgpgme11
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts firefox-libthai
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/9262kB of archives.
After unpacking 73.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 126941 files and directories currently installed.)
Preparing to replace firefox 2.0.0.4+1-0ubuntu1 (using .../firefox_2.0.0.5+1-0ubuntu1_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.5+1-0ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/share/firefox/chrome/classic/skin/classic/browser/feeds' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Please restart any running Firefoxes, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.5+1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas how I get Firefox back?

Thanks,

Stew

---

### Post by StewD on 2007-07-24
Any ideas anyone??!!

Please....I'm desperate!

---

### Post by davidjmayo on 2007-07-24
Some ides but not sure if this will help

> **StewD said:**
> Hi

I ran one of Ubuntu's standard updates (that flash up from the white star in orange square icon near the date/time at the top right of the screen). It stopped half way through with an error, I think because FireFox was open on another desktop.
[COLOR="Blue"]There was a security patch for firefox 2 or 3 days ago - sorry don't remember exactly. I installed with no problems but I didn't have firefox open. I do updates first then continue from there. Suggestion - look in synaptic for broken packages see bold below. (I use KDE so don't know synaptic). (I [/COLOR]
Since then I can not open Firefox. If I start Update Manager, I get told to run "sudo apt-get install -f" from a terminal, or "Synaptic". I can't get either of these to work. Following instructions from another posting I've tried to reinstall Firefox but get just about the same error messages. The reinstall followed these instructions:

```
cd /usr/lib
sudo rm -r mozilla-firefox
sudo apt-get update
sudo apt-get install mozilla-firefox

then you should have a fresh installation of firefox.

```

The error message I get from the terminal when running "sudo apt-get install -f" is:

```
stew@Fileserver1:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
[I]The following packages were automatically installed and are no longer required:
  libktnef1 linux-headers-2.6.20-15-generic libflac++5c2 python-ctypes
  linux-headers-2.6.20-15 libgpgme11[/I]
**Use 'apt-get autoremove' to remove them.**
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts firefox-libthai
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
**1 not fully installed or removed.**
Need to get 0B/9262kB of archives.
After unpacking 73.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 126941 files and directories currently installed.)
Preparing to replace firefox 2.0.0.4+1-0ubuntu1 (using .../firefox_2.0.0.5+1-0ubuntu1_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.5+1-0ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/share/firefox/chrome/classic/skin/classic/browser/feeds' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Please restart any running Firefoxes, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.5+1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas how I get Firefox back?

Thanks,

Stew

looks like the deb for ff 2.0.0.5 didn't download correctly (mine went from 2.0.0.4 to 2.0.0.5)

Hope this gives you some ides. This is not my strong point but post back if you need too and I'll try to help

---

### Post by StewD on 2007-07-24
Thanks for the advice.

I've had another go with Synaptic. When I enter I am told 

"You have one broken package on your system!
Use the "Broken" filter to locate it."

I then selected "Broken Dependencies" on the left hand side and "firefox-gnoe-support", version "2.0.0.5+1-0ubuntu1" appears.

I marked for re-installation, warned this would also affect Firefox, and then applied

Sadly I got the same error message:  

ie. unable to stat `./usr/share/firefox/chrome/classic/skin/classic/browser/feeds' 

I then tried going into Add/remove applications, and get told to try 'sudo apt-get update' and 'sudo apt-get install -f'. But continue to get the same error messages.

Aghhhhh....

---

