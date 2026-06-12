---
title: "HELP!!! Botched upgrade from 10.04 LTS to 12.04LTS"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by Olugbenga77 on 2012-12-17
Hi.
I'm not exactly new to Ubuntu, but i've been advancing with use.
here's the problem:
I attempted an inline upgrade to 12.04LTS, and i guess internet issues (plus erratic power supply in this part of the world) caused a botched upgrade.
I've gone through volumes of how to attyempt a partial upgrade until i encountered the dreaded 'network-manger-kde is marked for upgrade but is in the ...'. (cant remember the exact term now)
Eventually , 'sudo apt-get -f install' doesnt give any error but on attempting '```
sudo apt-get dist-upgrade
```' i get the following error:

```
gbenga@Gbenga-Ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
  libkdecore5: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkdesu5: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkdeui5: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkdewebkit5: Breaks: kdelibs5 (< 4:4.4.80) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkdnssd4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkfile4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkhtml5: Recommends: kdelibs5-plugins (= 4:4.8.4a-0ubuntu0.2) but it is not going to be installed
             Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkio5: Recommends: kdelibs5-plugins (= 4:4.8.4a-0ubuntu0.2) but it is not going to be installed
           Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkjsapi4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkmediaplayer4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libknewstuff3-4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libknotifyconfig4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkparts4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libkpty4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libktexteditor4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libnepomuk4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libnepomukquery4a: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
  libsolid4: Breaks: kdelibs5 (< 4:4.4.60) but 4:4.4.5-0ubuntu1.2 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```Prior to receiving this error, i was so stuck that i couldn't remove any packages at all until i stumbled on some error that pointed to ppp, so i ran:

```
'sudo apt-get remove ppp libpango1.0-0'
```The above command gave me some progress because for HOURS on end 'sudo apt-get -f install' donated multiple errors.
Pls i need help urgently, and actuaslly use my Ubuntu partition much more often than Windows.
thanks

---

### Post by dino99 on 2012-12-17
i does not know why you have removed these 2 packages as you might need them .

Before upgrading, its a good idea to clean the system and deactivate all the non genuine sources like ppas and else, and downgrade to genuine packages.

Try, then, to update and run:

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

sudo apt-get install kubuntu-desktop

if you still have issue, then boot into recovery mode, activate network, and fix/repair the system (from the recovery mode menu)

---

