---
title: "Gutsy incomplete install"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by short4lif2 on 2007-10-19
I tried installing gutsy using the recommended method.  I clicked on the upgrade button in the update manager for 7.10.  Things seemed to go normally, but i got an army of error windows telling me that packages belonging to, for instance, sun-java.  after all of these messsages, the upgrade seemed to continue as normal, but then stopped with an error message completely, and told me that i could have a broken system, and that i should run dpkg --configure -a.  i decided to restart before trying anything to see if my system was, indeed broken, and it booted up fairly normally.  My about dialog tells me i have 7.10 even though i am missing all those packages.  I felt that doing an apt-get upgrade may finish up the upgrade process, but those packages still don't want to be installed.

```
danny@smallbox:~$ sudo apt-get upgrade
[sudo] password for danny:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ubuntustudio-look
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jdk:
 sun-java5-jdk depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-demo:
 sun-java5-demo depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
 sun-java5-demo depends on sun-java5-jdk (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jdk is not configured yet.
dpkg: error processing sun-java5-demo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
 ubuntu-minimal depends on util-linux-locales; however:
  Package util-linux-locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 sun-java5-jre
 sun-java5-bin
 sun-java5-jdk
 sun-java5-demo
 util-linux-locales
 ubuntu-minimal
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

After seeing these errors, i thought that i needed to do dpkg --confiure -a, and then try the upgrade again, but obviously that won't work.

```
danny@smallbox:~$ sudo dpkg --configure -a
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jdk:
 sun-java5-jdk depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-demo:
 sun-java5-demo depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
 sun-java5-demo depends on sun-java5-jdk (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jdk is not configured yet.
dpkg: error processing sun-java5-demo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 locales
 language-pack-en-base
 sun-java5-jre
 util-linux
 ubuntu-minimal
 sun-java5-jdk
 language-pack-en
 sun-java5-demo
 language-pack-gnome-en-base
 sun-java5-bin
 util-linux-locales
 language-pack-gnome-en

```

Can someone help me either redo the install, or complete the install?  Do i need to perform a full reinstall of my operating system?

---

### Post by daveysmith on 2007-10-19
Here is how I solved this problem:

As root: 

dpkg -r tzdata
apt-get install tzdata

It then re-installed tzdata and carried on with life :-)

---

### Post by short4lif2 on 2007-10-19
worked perfectly, thankyou.

---

