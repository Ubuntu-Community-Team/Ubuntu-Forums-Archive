---
title: "Fail upgrade from 9.04 to 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Aereal on 2009-11-15
Did an upgrade and it got stuck installing openoiffce packages, I thought it was going to go on after some minutes, so I went to the disco (irrelevant data), and came back 6 hours later to find out that the dpkg process was in 0% CPU USAGE. So I interrupted that instalation with control + c, and the others continued. It booted, and when using the new kernel it happened the thing of blinking console login.

So, I booted, logged in using another kernel and everything was "fine", except sound and don't know how many things more. I tried using aptitude upgrade -f and it got stuck again, here is a paste

```
irakirashia@mfsec:~$ sudo apt-get update

irakirashia@mfsec:~$ sudo aptitude upgrade -f
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  acl{u} autoconf{u} automake{u} automake1.9{u} autotools-dev{u} cdbs{u} 
  evolution-documentation-en{u} fdupes{u} firefox-3.0-branding{u} 
  g++-4.3{u} gnome-mount{u} intltool{u} ladcca2{u} 
  language-support-translations-en{u} libadns1{u} libass1{u} 
  libaudclient1{u} libaudid3tag1{u} libbeecrypt6{u} 
  libboost-date-time1.34.1{u} libboost-thread1.34.1{u} libcolamd-3.2.0{u} 
  libdirectfb-1.0-0{u} libffado0{u} libglib2.0-dev{u} libgmyth0{u} 
  libicu38{u} liblog4j1.2-java-gcj{u} liblrdf0{u} libltdl-dev{u} 
  libmysqlclient15off{u} libneon27{u} libpcap0.8-dev{u} libpulsecore9{u} 
  libsgutils1{u} libsmbios2{u} libsnacc-dev{u} libsnacc0c2{u} 
  libstdc++6-4.3-dev{u} libtool{u} libwxbase2.6-0{u} libwxgtk2.6-0{u} m4{u} 
  menu{u} omniidl4{u} openoffice.org-help-en-gb{u} 
  openoffice.org-help-en-us{u} openoffice.org-l10n-common{u} 
  openoffice.org-l10n-en-gb{u} openoffice.org-l10n-en-za{u} 
  openoffice.org-writer2latex{u} pkg-config{u} pulseaudio-module-hal{u} 
  python-chardet{u} sg3-utils{u} snacc{u} snacc-doc{u} 
  thunderbird-locale-en-gb{u} ttf-bengali-fonts{u} ttf-kannada-fonts{u} 
  ttf-oriya-fonts{u} ttf-telugu-fonts{u} 
The following packages will be upgraded:
  openoffice.org-emailmerge openoffice.org-filter-binfilter ure 
The following partially installed packages will be configured:
  language-support-en language-support-writing-en openoffice.org 
  openoffice.org-base openoffice.org-base-core openoffice.org-calc 
  openoffice.org-core openoffice.org-draw openoffice.org-hyphenation-en-us 
  openoffice.org-impress openoffice.org-math openoffice.org-officebean 
  openoffice.org-report-builder-bin openoffice.org-writer python-uno 
3 packages upgraded, 0 newly installed, 62 to remove and 0 not upgraded.
Need to get 0B/8,202kB of archives. After unpacking 174MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 191166 files and directories currently installed.)
Removing openoffice.org-writer2latex ...


```So, I know I can fix the sound and many more things, but without apt-get working ok I can't do anything, how do I fix it?

---

### Post by Aereal on 2009-11-15
irakirashia@mfsec:~$  sudo dpkg --force-depends --purge openoffice.org-writer2latex
(Reading database ... 191166 files and directories currently installed.)
Removing openoffice.org-writer2latex ...

And hangs out.

---

