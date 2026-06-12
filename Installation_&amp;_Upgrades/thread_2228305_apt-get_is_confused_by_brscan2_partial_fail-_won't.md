---
title: "apt-get is confused by brscan2 partial fail- won't install anything"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by linbu2 on 2014-06-06
Background:  Running kubuntu 14.04, using kdm.  I have a Brother  MFC7280N, and installed the brscan2 package.  Nevertheless I have never  been able to scan, since the device is never found.  I removed (I  thought) brscan2 in hopes of reinstalling. 


  I had installed Kompozer, and had to remove it when it started to  display funky video.  I have tried to reinstall it but without success.   I haven't edited any config files, except to add a repository for  Kompozer (failed), or done anything other than run apt-get and the  software center.  That is, I haven't tried any strange (to me) commands  to install, remove, or modify the installed software. 

 I did try to  install Kompozer from a .deb file and also from two tarballs.  Because I really, really need Kompozer and couldn't get it to work right on this machine.


  Now I can't install or remove any software using apt-get or the Ubuntu Software Center.  Here's an example: 
<<

bill@LEX:/home/bill# sudo apt-get purge kompozer:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  brscan2 kompozer:i386*
0 upgraded, 0 newly installed, 2 to remove and 338 not upgraded.
2 not fully installed or removed.
After this operation, 26.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 325451 files and directories currently installed.)
Removing brscan2 (0.2.5-1) ...
rmdir: failed to remove &#8216;/usr/local/Brother/sane/GrayCmData/ALL&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane/GrayCmData/AL&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane/GrayCmData&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane/models2&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother&#8217;: No such file or directory
dpkg: error processing package brscan2 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)

<<

It's as-if wheatever I am trying to install or remove, apt-get finds  that it had a problem with brscan2 and tries to remove it, giving up  when it fails because it had partially succeeded before.  Then it just  ignores anything else (like Kompozer, or anything I want to install or  remove, even when using the -f option).  This is so strange that I don't  have any notion of what to make of it.  So I need some expert guidance.   Many thanks!


[LIST]
[*]                          :confused: 
[/LIST]

---

### Post by Ubi_one_2014 on 2014-06-06
apt-get remove brscan2

what shows the output

---

### Post by linbu2 on 2014-06-07
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brscan2

---

### Post by Ubi_one_2014 on 2014-06-07
for your brother device

go to
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7820n_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7820n_all&os=128)

---

### Post by Ubi_one_2014 on 2014-06-07
your brother driver seems to be removed

pls install the drivers first, and make sure you can print and scan

after that i will guide you in to the process of installation of Kompozer

---

### Post by linbu2 on 2014-06-07
I can't install anything either (including brscan2).  I do appreciate your guidance.  It says brscan2 is already the latest version, but yet my scanner is never found.  I've tried xsane, simple scan, and gwenview for scanning.

# apt-get install brscan2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
brscan2 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kompozer:i386 : Depends: libatk1.0-0:i386 (>= 1.9.0) but it is not going to be installed
                 Depends: libcairo2:i386 (>= 1.0.2-2) but it is not going to be installed
                 Depends: libgtk2.0-0:i386 (>= 2.8.0) but it is not going to be installed
                 Depends: libidl0:i386 but it is not going to be installed
                 Depends: libpango1.0-0:i386 (>= 1.12.3) but it is not going to be installed
                 Depends: libxft2:i386 (> 2.1.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by linbu2 on 2014-06-07
BTW: I've tried 'apt-get -f install' with no packages

---

### Post by Ubi_one_2014 on 2014-06-08
dpkg -s brscan2

pls  post the output

---

### Post by linbu2 on 2014-06-08
Package: brscan2
Status: deinstall ok half-installed
Maintainer: Brother Industries, Ltd.
Architecture: amd64
Version: 0.2.5-1
Config-Version: 0.2.5-1
Provides: brscan
Description: Brother Scanner Driver
 Copyright: 2003 Brother Industries, Ltd. All Rights Reserved
 Brother sane backend Driver

---

### Post by kurt18947 on 2014-06-08
> **linbu2 said:**
> I can't install anything either (including brscan2).  I do appreciate your guidance.  It says brscan2 is already the latest version, but yet my scanner is never found.  I've tried xsane, simple scan, and gwenview for scanning.

If brscan2 is installed, have you done the 2 additional steps required for Brother scanners to be recognized by normal users?

One involves this edit: [INDENT]Copy the following files under /usr/lib64/ to /usr/lib/.

**For brscan2 Users:**
/usr/lib64/libbrscandec2.so.1.0.0
/usr/lib64/sane/libsane-brother2.so.1.0.7
/usr/lib64/sane/libsane-brother2.so.1
/usr/lib64/sane/libsane-brother2.so
/usr/lib64/libbrcolm2.so.1.0.1
/usr/lib64/libbrcolm2.so
/usr/lib64/libbrscandec2.so.1
/usr/lib64/libbrscandec2.so
/usr/lib64/libbrcolm2.so.1
[/INDENT]

reference:  [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)


The second issue involves a situation where the scanner works using SUDO but not as a non-privileged user:

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10 (versions later than 12.10 aren't mentioned but I've needed to do these steps with each new install)

**1**. Open "/lib/udev/rules.d/40-libsane.rules" file.[B]

2. [/B]Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".    
  
  The lines to be added---------------------------          
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

      **3.** Restart the OS.

reference:  [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#6](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#6)

I hope this will get your Brother working.

---

### Post by linbu2 on 2014-06-09
There's no /usr/lib64, and the /usr/lib/ doesn't contain any of the  files shown.  There are /lib /lib32 and /lib64 directories but none of  those contain the files mentioned.  In fact the files aren't anywhere on my system.

---

### Post by kurt18947 on 2014-06-09
If those files are not present, I'd wonder if the install worked as advertised.  Maybe try to uninstall and reinstall?  I  use the installer script and have an uninstall script in the same folder as the other Brother files.

---

### Post by linbu2 on 2014-06-09
/usr/lib64 doesn't exist, and so none of the files are there.  I don't actually think I have a brscan2 installed.  "Find Files/Folders" finds nothing with that name (and no extension).

---

### Post by linbu2 on 2014-06-09
> **kurt18947 said:**
> If those files are not present, I'd wonder if the install worked as advertised.  Maybe try to uninstall and reinstall?  I  use the installer script and have an uninstall script in the same folder as the other Brother files.

There's _no ability_ to uninstall, or install _**anything**_ on my system.  I get the same failure messages every time.

---

### Post by linbu2 on 2014-06-09
The uninstall might have partially worked, as I have found none of the Brother files on my system in any directory (and all are viewable and searchable).  But if it did, it left a mess that precludes any further installs or uninstalls until I get it fixed.

---

### Post by kurt18947 on 2014-06-09
> **linbu2 said:**
> There's _no ability_ to uninstall, or install _**anything**_ on my system.  I get the same failure messages every time.

Are you using an account with SUDO privileges?  It sounds like you've found your Brother problem - no or incomplete install.  Now to figure out why that is.

---

### Post by linbu2 on 2014-06-10
Yes, I have sudo privileges, which used to work just fine, until about two weeks ago.  I can also start a root shell and try apt-get with identical results.

---

### Post by linbu2 on 2014-06-13
This is related to another thread, asked a week ago, but never solved: [http://ubuntuforums.org/showthread.php?t=2228305&page=2&p=13045863#post13045863](http://ubuntuforums.org/showthread.php?t=2228305&page=2&p=13045863#post13045863)   I am going to have to trash my system if this can't be resolved, because I can't install security patches, let alone anything else.  I can't uninstall either.

When I attempt to do either I get this:

```

bill@LEX:/# sudo apt-get -f purge brscan2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kompozer:i386 : Depends: libatk1.0-0:i386 (>= 1.9.0) but it is not going to be installed
                 Depends: libcairo2:i386 (>= 1.0.2-2) but it is not going to be installed
                 Depends: libgtk2.0-0:i386 (>= 2.8.0) but it is not going to be installed
                 Depends: libidl0:i386 but it is not going to be installed
                 Depends: libpango1.0-0:i386 (>= 1.12.3) but it is not going to be installed
                 Depends: libxft2:i386 (> 2.1.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

bill@LEX:/# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gir1.2-gtk-2.0 libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgail-common libgail18 libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386
  libgtk2.0-0 libgtk2.0-0:i386 libgtk2.0-bin libgtk2.0-dev libharfbuzz0b:i386 libidl0:i386 libjasper1:i386 libpango-1.0-0:i386
  libpango1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386 libpixman-1-0:i386
  libthai0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxft2:i386
Suggested packages:
  librsvg2-common:i386 gvfs:i386 libgtk2.0-doc libjasper-runtime:i386 ttf-baekmuk:i386 ttf-arphic-gbsn00lp:i386
  ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386
The following packages will be REMOVED:
  brscan2
The following NEW packages will be installed:
  libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386 libgtk2.0-0:i386 libharfbuzz0b:i386
  libidl0:i386 libjasper1:i386 libpango-1.0-0:i386 libpango1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386
  libpangox-1.0-0:i386 libpangoxft-1.0-0:i386 libpixman-1-0:i386 libthai0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxft2:i386
The following packages will be upgraded:
  gir1.2-gtk-2.0 libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev
6 upgraded, 20 newly installed, 1 to remove and 354 not upgraded.
2 not fully installed or removed.
Need to get 0 B/7,985 kB of archives.
After this operation, 12.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 325451 files and directories currently installed.)
Removing brscan2 (0.2.5-1) ...
rmdir: failed to remove &#8216;/usr/local/Brother/sane/GrayCmData/ALL&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane/GrayCmData/AL&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane/GrayCmData&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane/models2&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother/sane&#8217;: No such file or directory
rmdir: failed to remove &#8216;/usr/local/Brother&#8217;: No such file or directory
dpkg: error processing package brscan2 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Doesn't matter if I try from a root terminal login.  Same failures and errors.  A little while ago I removed a repository that I had added before (related to Kompozer) I thought could be the problem- it wasn't.

I have never been able to scan.  brscan2 is not installed anymore, but evidently not fully uninstalled.

HELP!!!  I am really stuck.  Will reinstalling Ubuntu on top of my current installation do anything, or wreck everything?

---

### Post by mörgæs on 2014-06-13
Threads merged. Please don't double-post.

If you have been struggling with the problem for six days a reinstall is a good idea.

---

### Post by linbu2 on 2014-06-13
As you can see I've considered it, but I thought that surely someone must know more about apt-get, enough that I could at least learn something.  Sorry for "reposting"- I didn't see it that way- same problem, different approach.  Anyway, I was hoping to learn something from someone about apt-get.  Isn't that what this thing called a forum is for?

Might someone be able to suggest another forum where I can ask questions, possibly using different approaches to solve a problem?

And other than the mechanics of it, I haven't even learned what a reinstall involves.  I asked whether it will trash my system.  Will it install any software I have and destroy my data?  Is there some guide as to what I might backup (in /etc for example) so that I don't have to reconfigure from scratch (if it does trash my system)- can just just copy the backed up config files back?  I'd assume that if I backup and restore all of /etc after the reinstall, I might still have trouble with apt-get.  Then which files would I not want to replace, just the ones in /etc/apt?

---

### Post by mörgæs on 2014-06-13
You are free to post regarding different approaches but stick to one thread, please.

As your system is in a bad state I recommend saving as little as possible from it if you do a fresh install. You are of course also welcome to wait and see if a clever apt-get command comes up.

---

