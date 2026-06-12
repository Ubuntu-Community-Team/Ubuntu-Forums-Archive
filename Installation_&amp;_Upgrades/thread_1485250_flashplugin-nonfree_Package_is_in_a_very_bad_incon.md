---
title: "flashplugin-nonfree: Package is in a very bad inconsistent state"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Gergin on 2010-05-16
I'm having a few problems, but they seem to all revolve around flashplugin.

These are the error messages I get:
"You have 1 broken package on your system!
Use the "Broken" filter to locate it.'
and:
"E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal."

I can't seem to reinstall it though. I'm not so good at these sort of things, and I won't be surprised if I'm just being stupid. I'd appreciate any help anyone can give me. Thanks

Trying to install flashplugin from install manager just gives me those same messages.
I also tried to remove, in the hope of being able to reinstall without problems. But that attempt seems to run me back in circles. I noticed below it says "not installed, so not removed" But the fore-mentioned error suggests it is installed, but is in "a very bad inconsistent state"
???????????????????????????????????????????????????????
*@*-desktop:~$ sudo apt-get remove adobe-flashplugin
[sudo] password for *: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
*@*-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libfreebob0 libarts1c2a ispell ibritish libmono-posix1.0-cil
  kdelibs4c2a libartsc0 libmtp7 libmono-security1.0-cil lsb-languages
  libneon27 libavutil1d libdc1394-13 texlive-base libk3b2
  libmono-sharpzip0.84-cil texlive libicu38 texlive-fonts-recommended
  libgtk1.2 ubuntu-gdm-themes sqlite libwvstreams4.4-base mdetect
  libwxgtk2.6-0 libbeecrypt6 libmono-system-web1.0-cil libbeagle1 python-gdata
  kdelibs-data kdebase-data libopenexr2ldbl libmagick10 texlive-common
  libcamel1.2-11 libwvstreams4.4-extras openoffice.org-hyphenation-en-us
  openoffice.org-writer2latex libggzmod4 liblualib50 libqt4-core libpostproc1d
  libfftw3-3 libtotem-plparser10 libsgutils1 libx11-xcb1 libgtkhtml3.16-cil
  libsmbios1 libgpod3 luatex libdvbpsi4 libavformat1d binutils-static libcdio7
  policykit libxosd2 cryptsetup libmysqlclient15off libdirectfb-1.0-0 ruby1.8
  tetex-bin libgtkmm1.2-0c2a acl libffi4 libvlc0 nvidia-kernel-common ruby
  bluez-audio libkonq4 libavahi-qt3-1 libpolkit-gnome0 libflickrnet2.1.5-cil
  libwxbase2.6-0 libggz2 classpath-gtkpeer libmono1.0-cil libpolkit-dbus2
  libmono-data-tds1.0-cil openoffice.org-thesaurus-en-au libtunepimp5 libifp4
  libmono-system-data1.0-cil libdbus-qt-1-1c2 texlive-latex-recommended
  lsb-multimedia libiso9660-5 libdvdread3 libzip1 libgtk1.2-common
  firefox-3.0-gnome-support classpath-common texlive-latex-base cacao
  policykit-gnome python-4suite-xml libxklavier12 libavcodec1d libsigc++0c2
  libpq5 libggzcore9 texlive-luatex odt2txt classpath liblua50 libruby1.8
  sqlite3 iamerican libaudit0 texlive-doc-base libpolkit-grant2 libnjb5
  libofa0 libntfs-3g23 libpolkit2 hwtest
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 42 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

*@*-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libfreebob0 libarts1c2a ispell ibritish libmono-posix1.0-cil
  kdelibs4c2a libartsc0 libmtp7 libmono-security1.0-cil lsb-languages
  libneon27 libavutil1d libdc1394-13 texlive-base libk3b2
  libmono-sharpzip0.84-cil texlive libicu38 texlive-fonts-recommended
  libgtk1.2 ubuntu-gdm-themes sqlite libwvstreams4.4-base mdetect
  libwxgtk2.6-0 libbeecrypt6 libmono-system-web1.0-cil libbeagle1 python-gdata
  kdelibs-data kdebase-data libopenexr2ldbl libmagick10 texlive-common
  libcamel1.2-11 libwvstreams4.4-extras openoffice.org-hyphenation-en-us
  openoffice.org-writer2latex libggzmod4 liblualib50 libqt4-core libpostproc1d
  libfftw3-3 libtotem-plparser10 libsgutils1 libx11-xcb1 libgtkhtml3.16-cil
  libsmbios1 libgpod3 luatex libdvbpsi4 libavformat1d binutils-static libcdio7
  policykit libxosd2 cryptsetup libmysqlclient15off libdirectfb-1.0-0 ruby1.8
  tetex-bin libgtkmm1.2-0c2a acl libffi4 libvlc0 nvidia-kernel-common ruby
  bluez-audio libkonq4 libavahi-qt3-1 libpolkit-gnome0 libflickrnet2.1.5-cil
  libwxbase2.6-0 libggz2 classpath-gtkpeer libmono1.0-cil libpolkit-dbus2
  libmono-data-tds1.0-cil openoffice.org-thesaurus-en-au libtunepimp5 libifp4
  libmono-system-data1.0-cil libdbus-qt-1-1c2 texlive-latex-recommended
  lsb-multimedia libiso9660-5 libdvdread3 libzip1 libgtk1.2-common
  firefox-3.0-gnome-support classpath-common texlive-latex-base cacao
  policykit-gnome python-4suite-xml libxklavier12 libavcodec1d libsigc++0c2
  libpq5 libggzcore9 texlive-luatex odt2txt classpath liblua50 libruby1.8
  sqlite3 iamerican libaudit0 texlive-doc-base libpolkit-grant2 libnjb5
  libofa0 libntfs-3g23 libpolkit2 hwtest
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 42 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
*@*-desktop:~$

---

### Post by ajgreeny on 2010-05-16
If you are using gnome as your desktop, try using synaptic to fix the broken packages (Edit ->Fix Broken Packages).  It seems to work sometimes when apt-get doesn't, for some reason.

---

### Post by Gergin on 2010-05-16
ajgreeny - Thanks for the suggestion to try Synaptic. It had a lot of promise, but, for my issue it just runs me in circles. The solution won't apply. I get the same set of errors. It's like it's saying you can't fix without removing, and you can't remove without fixing, because it can't do either without installing, but it can't install without fixing, ect. ect... :confused:  I'm starting to wonder if I should jump to the drastic, pain in the butt, solution of reinstalling Ubuntu from scratch. I really appreciate the suggestion, though. Thank you very much for the input.

---

### Post by Flash 2933 on 2010-05-16
I am having the same problem. I have also tried to do [IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG][IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]robert@robert-desktop:~$ sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prem
[sudo] password for robert: 
rm: cannot remove `/var/lib/dpkg/info/flashplugin-nonfree.prem': No such file or directory
robert@robert-desktop:~$ sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 208370 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
robert@robert-desktop:~$ sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 208370 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

---

### Post by Gergin on 2010-05-17
@Flash 2933  Sorry to see your having same problem. But glad I'm not the only one. Thank you for posting your attempted solution. I, myself had not tried that. I'll give that solution a go, just to see, but I think the result will be the same. Be assured I will post any attempted solutions. -Thank you for your input -

-update- Attempted same solution - Terminal returned same response

---

### Post by kansasnoob on 2010-05-17
See if the first issue mentioned here applies:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

[B]Upgrade 8.04 -> 10.04 can break apt-get.
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;[/B]

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841")

> For those not wanting to read the bug report in detail, the fix is :

```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm

sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```

If so I'd finish up by installing "ubuntu-restricted-extras" once things are updated.

---

### Post by Gergin on 2010-05-17
@kansasnoob  U ROCK!!!  :guitar:    Can't say THANKS loud enough.
Solution worked great!!! Thank you... Thank you... Thank you...   :P

---

### Post by Flash 2933 on 2010-05-17
This is the fix I tried before however I am afraid that I missed 1 letter and it did not work. I thank you for posting this in a manner that made it easier for me to read. Thank You so much for the fix.

---

### Post by Flash 2933 on 2010-05-17
So Now How do you install the "ubuntu-restricted-extras". ?  Yes I know I am a newbie. at linux. I am certified in Windows  though I have my A+, Network+ and MCP Certifications.

---

### Post by kansasnoob on 2010-05-17
> **Flash 2933 said:**
> So Now How do you install the "ubuntu-restricted-extras". ?  Yes I know I am a newbie. at linux. I am certified in Windows  though I have my A+, Network+ and MCP Certifications.

Either just go to Synaptic or from terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Note: if you're using kubuntu or xubuntu be sure to change the command (add the x or k)

---

### Post by WoodworkerB on 2010-05-24
Kansasanoob - thanks.  This fixed the only problem I had with two upgrades from 8.04LTS to 10.04LTS.  I'm very impressed with the improvements.  WoodWorkerB

> **kansasnoob said:**
> See if the first issue mentioned here applies:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

[B]Upgrade 8.04 -> 10.04 can break apt-get.
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;[/B]

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841")



If so I'd finish up by installing "ubuntu-restricted-extras" once things are updated.

---

### Post by brazzmonkey on 2010-08-25
> **kansasnoob said:**
> See if the first issue mentioned here applies:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

[B]Upgrade 8.04 -> 10.04 can break apt-get.
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;[/B]

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841")



If so I'd finish up by installing "ubuntu-restricted-extras" once things are updated.
thanks a bunch. you saved  my day.

---

### Post by dionizos on 2010-11-02
> **kansasnoob said:**
> See if the first issue mentioned here applies:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

[B]Upgrade 8.04 -> 10.04 can break apt-get.
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;[/B]

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841")



If so I'd finish up by installing "ubuntu-restricted-extras" once things are updated.

Thanks that saved me a lot of work!

---

