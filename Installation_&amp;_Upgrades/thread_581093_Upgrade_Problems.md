---
title: "Upgrade Problems"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by chiefbutz on 2007-10-19
When I upgraded is said not all things could be installed. I have tried using apt-get and dpkg to install that didn't install. But none of it will configure and such. Here is the output from running "dpkg --configure -a"

> Setting up tzdata (2007f-3ubuntu1) ...
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
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
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
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
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
 language-pack-en
 language-pack-gnome-en-base
 sun-java5-bin
 util-linux-locales
 sun-java5-plugin
 language-pack-gnome-en


Any help would be GREAT! I can't install any other programs now either.

---

### Post by freed0m on 2007-10-19
Check here [http://ubuntuforums.org/showthread.php?t=579679&highlight=tzdata]("http://ubuntuforums.org/showthread.php?t=579679&highlight=tzdata")

---

### Post by chiefbutz on 2007-10-19
Thanks

---

