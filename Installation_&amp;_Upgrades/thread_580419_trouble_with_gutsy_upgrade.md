---
title: "trouble with gutsy upgrade"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by BoneSaw on 2007-10-18
so im sure there are alot of posts out there about problems with upgrading but here goes anyway.

i was using update manager and got a bunch of errors, update manager said it was gonna abort and kept going. eventually said to dpkg --configure -a which gave a bunch of errors

```
bonesaw@butcher:~$ sudo dpkg --configure -a
Setting up jackd (0.103.0-6ubuntu1) ...
Installing new version of config file /etc/bash_completion.d/jackd ...
Setting up gij-4.2 (4.2.1-5ubuntu5) ...

Setting up tmispell-voikko (0.6.2-1ubuntu1) ...

Setting up mjpegtools (1:1.8.0-0.2ubuntu5) ...

Setting up libswt3.2-gtk-gcj (3.2.2-3ubuntu3) ...

Setting up powermanagement-interface (0.3.17) ...

Setting up mono-gac (1.2.4-6ubuntu6) ...
* Installing 1 assembly from libgmime2.2-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono

Setting up apport-gtk (0.98) ...

Setting up libjack-dev (0.103.0-6ubuntu1) ...

Setting up libjack0.100.0-dev (0.103.0-6ubuntu1) ...
Setting up gnome-app-install (0.4.13-0ubuntu1) ...
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...

Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Setting up wesnoth (1.2.6-1ubuntu2) ...

Setting up wesnoth-tsg (1.2.6-1ubuntu2) ...
Setting up bogofilter (1.1.5-2ubuntu2) ...
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-tr-base:
 language-pack-tr-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-tr-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-zh-base:
 language-pack-zh-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-zh-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-he-base:
 language-pack-gnome-he-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-he-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-de-base:
 language-pack-gnome-de-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-de-base (--configure):
 dependency problems - leaving unconfigured
Setting up wesnoth-ttb (1.2.6-1ubuntu2) ...
Setting up wesnoth-utbs (1.2.6-1ubuntu2) ...
dpkg: dependency problems prevent configuration of language-pack-pt-base:
 language-pack-pt-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-pt-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-no-base:
 language-pack-no-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-no-base (--configure):
 dependency problems - leaving unconfigured
Setting up gstreamer0.10-plugins-bad (0.10.5-4ubuntu1) ...
Setting up eclipse-platform (3.2.2-3ubuntu3) ...
dpkg: dependency problems prevent configuration of language-pack-sv-base:
 language-pack-sv-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-sv-base (--configure):
 dependency problems - leaving unconfigured
Setting up wesnoth-trow (1.2.6-1ubuntu2) ...
Setting up bind9-host (1:9.4.1-P1-3) ...
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
Setting up wesnoth-httt (1.2.6-1ubuntu2) ...
Setting up libndesk-dbus-glib1.0-cil (0.3-2) ...
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono

dpkg: dependency problems prevent configuration of language-pack-gnome-sv-base:
 language-pack-gnome-sv-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-sv-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-es-base:
 language-pack-gnome-es-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-es-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-ko-base:
 language-pack-gnome-ko-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-ko-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-cs-base:
 language-pack-gnome-cs-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-cs-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-sv:
 language-pack-gnome-sv depends on language-pack-gnome-sv-base; however:
  Package language-pack-gnome-sv-base is not configured yet.
dpkg: error processing language-pack-gnome-sv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-hu-base:
 language-pack-hu-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-hu-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-ru-base:
 language-pack-ru-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-ru-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-nb-base:
 language-pack-gnome-nb-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-nb-base (--configure):
 dependency problems - leaving unconfigured
Setting up java-gcj-compat (1.0.76-4ubuntu1) ...

Setting up libcairo-java-gcj (1.0.8-6ubuntu1) ...

dpkg: dependency problems prevent configuration of language-pack-nl-base:
 language-pack-nl-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-nl-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-fr-base:
 language-pack-gnome-fr-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-fr-base (--configure):
 dependency problems - leaving unconfigured
Setting up wesnoth-ei (1.2.6-1ubuntu2) ...
Setting up jack-rack (1.4.4-3ubuntu1) ...

dpkg: dependency problems prevent configuration of language-pack-gnome-hu-base:
 language-pack-gnome-hu-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-hu-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-pl-base:
 language-pack-gnome-pl-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-pl-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-sv:
 language-pack-sv depends on language-pack-sv-base; however:
  Package language-pack-sv-base is not configured yet.
dpkg: error processing language-pack-sv (--configure):
 dependency problems - leaving unconfigured
Setting up libmono-cairo1.0-cil (1.2.4-6ubuntu6) ...
Setting up eclipse-source (3.2.2-3ubuntu3) ...
Setting up gij (4:4.2.1-4ubuntu2) ...
Setting up libmono-system1.0-cil (1.2.4-6ubuntu6) ...
dpkg: dependency problems prevent configuration of language-pack-gnome-da-base:
 language-pack-gnome-da-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-da-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-es-base:
 language-pack-es-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-es-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oem-config:
 oem-config depends on locales (>= 2.3.7-1); however:
  Package locales is not configured yet.
dpkg: error processing oem-config (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-es:
 language-pack-gnome-es depends on language-pack-gnome-es-base; however:
  Package language-pack-gnome-es-base is not configured yet.
dpkg: error processing language-pack-gnome-es (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-ar-base:
 language-pack-ar-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-ar-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-zh-base:
 language-pack-gnome-zh-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-zh-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-pt:
 language-pack-pt depends on language-pack-pt-base; however:
  Package language-pack-pt-base is not configured yet.
dpkg: error processing language-pack-pt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-da-base:
 language-pack-da-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-da-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-ko-base:
 language-pack-ko-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-ko-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-de-base:
 language-pack-de-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-de-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-tr-base:
 language-pack-gnome-tr-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-tr-base (--configure):
 dependency problems - leaving unconfigured
Setting up libglib2.0-cil (2.10.2-1ubuntu2) ...
dpkg: dependency problems prevent configuration of language-pack-gnome-hu:
 language-pack-gnome-hu depends on language-pack-gnome-hu-base; however:
  Package language-pack-gnome-hu-base is not configured yet.
dpkg: error processing language-pack-gnome-hu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-he:
 language-pack-gnome-he depends on language-pack-gnome-he-base; however:
  Package language-pack-gnome-he-base is not configured yet.
dpkg: error processing language-pack-gnome-he (--configure):
 dependency problems - leaving unconfigured
Setting up libgtk-java-gcj (2.10.2-4ubuntu1) ...

dpkg: dependency problems prevent configuration of language-pack-gnome-ar-base:
 language-pack-gnome-ar-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-ar-base (--configure):
 dependency problems - leaving unconfigured
Setting up libmono-security1.0-cil (1.2.4-6ubuntu6) ...
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-nl-base:
 language-pack-gnome-nl-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-nl-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-nn-base:
 language-pack-gnome-nn-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-nn-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-ar:
 language-pack-ar depends on language-pack-ar-base; however:
  Package language-pack-ar-base is not configured yet.
dpkg: error processing language-pack-ar (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-cs-base:
 language-pack-cs-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-cs-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-ja-base:
 language-pack-ja-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-ja-base (--configure):
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
dpkg: dependency problems prevent configuration of language-pack-gnome-ar:
 language-pack-gnome-ar depends on language-pack-gnome-ar-base; however:
  Package language-pack-gnome-ar-base is not configured yet.
dpkg: error processing language-pack-gnome-ar (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-ko:
 language-pack-gnome-ko depends on language-pack-gnome-ko-base; however:
  Package language-pack-gnome-ko-base is not configured yet.
dpkg: error processing language-pack-gnome-ko (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-no:
 language-pack-no depends on language-pack-no-base; however:
  Package language-pack-no-base is not configured yet.
dpkg: error processing language-pack-no (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-nl:
 language-[pack-nl depends on language-pack-nl-base; however:
  Package language-pack-nl-base is not configured yet.
dpkg: error processing language-pack-nl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-nn-base:
 language-pack-nn-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-nn-base (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

```

so i went to the first error(tzdata) and tried dpkg --configure -a:

```
bonesaw@butcher:~$ sudo dpkg --configure tzdata
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata

```

i also got an error setting up libpam at one point that said i wouldnt be able to start any new x sessions, so im scared of restarting.

any help?

---

### Post by Pumalite on 2007-10-18
Try:

sudo  apt-get -f install

---

### Post by BoneSaw on 2007-10-18
i get the same list of errors. it all starts with that tzdata error.

---

### Post by steveneddy on 2007-10-18
Wait until late tonight, the morning, or tomorrow night. The servers are jam packed.

---

### Post by BoneSaw on 2007-10-18
ive gotten everything downloaded, but it wont configure for some reason.

---

### Post by BoneSaw on 2007-10-18
i cant use synaptic or apt because i keep getting "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

---

### Post by Pumalite on 2007-10-18
It's:

sudo dpkg --configure -a

---

### Post by steveneddy on 2007-10-18
Make me a sandwich!

No!

sudo make me a sandwich!

OK!

---

### Post by BoneSaw on 2007-10-18
> **Pumalite said:**
> It's:

sudo dpkg --configure -a

yeah i figured that out the first time i tried it.

i installed the deb listed in the comments [here]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/125349") and its seems to be working

---

### Post by Pumalite on 2007-10-18
Lol

---

### Post by Hoppiesbox on 2007-10-20
> **steveneddy said:**
> Make me a sandwich!

No!

sudo make me a sandwich!

OK!

HAHAHA

---

