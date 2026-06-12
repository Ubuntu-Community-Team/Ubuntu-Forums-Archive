---
title: "Upgrade 14.10 -&gt; 15.04 failed - udev problem?"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by stefan-piaostefan on 2015-05-07
Hi,

I tried to upgrade Kubuntu 14.10 to 15.04 using the instructions on the home page.

After a couple of hours of downloading and setting up packages, I got an error message and the upgrade rolled back.
As I remember it, I think I saw something about openvpn, but I am not sure (it was late, to my excuse).

After this, I have tried to do 
  ```
sudo apt-get update
```
which works fine, and then 
  ```
sudo apt-get upgrade
```
which does not.

I look into the logs in /var/logs/apt/log and see problems like:

```
Ställer in udev (208-8ubuntu8.2) ...
udev stop/waiting
udev start/running, process 13355
update-initramfs: deferring update (trigger activated)
insserv: warning: script 'tptestd' missing LSB tags and overrides
insserv: There is a loop between service minidlna and tptestd if stopped
insserv:  loop involving service tptestd at depth 2
insserv:  loop involving service minidlna at depth 1
insserv: Stopping tptestd depends on minidlna and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: fel vid hantering av paketet udev (--configure):
 underprocessen installerade post-installation-skript gav felkod 1
dpkg: beroendeproblem förhindrar konfigurering av initramfs-tools:
 initramfs-tools är beroende av udev (>= 147~-5), men:
  Paketet udev har inte konfigurerats ännu.

```

(Yes, I know, How could I get the idea to setup the system to log in Swedish?)
And then there are multiple errors following that.

System info:
```
uname -a
Linux linus 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i686 GNU/Linux

```

Anybody know how to resolve this?

// Stefan

---

### Post by stefan-piaostefan on 2015-05-07
Hi,

I purged the tptestd package (a non-standard one) and things are starting to move.
I will report success not not here later.

// Stefan

---

### Post by stefan-piaostefan on 2015-05-07
Great news!

After purging the failing package tptestd, the upgrade worked just fine.
I am now running Kubuntu 15.04 and everything is fine.

// Stefan

---

