---
title: "help with apt-get upgrade!!!"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by jacob4 on 2013-08-06
i recently got back from a long trip and found an unstable ubuntu. i have no ability to install or upgrade anything including the os. i've tried several solutions posted to this thread (and others) with no success. i can update but cannot run fsck....i'll post that error also. thanks for any help that you all can provide. i'm posting both errors here. BTW i'm not a complete novice to linux but it's been a while and lot's has changed. i'm a pre xwin user when i was in grad school and just got back into the open source world. thanks

jake

     I've used these 2 threads to no avail.

[http://ubuntuforums.org/showthread.php?t=1914216](http://ubuntuforums.org/showthread.php?t=1914216)
[http://ubuntuforums.org/showthread.php?t=352766](http://ubuntuforums.org/showthread.php?t=352766)
***Haven't tried this one*** [http://ubuntuforums.org/showthread.php?t=1625789](http://ubuntuforums.org/showthread.php?t=1625789)
```
[I][B]

ERROR FROM THE UPGRADE ATTEMPT[/B][/I]
[I]Package python3-apt is not configured yet. 

  language-selector-common depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  ERROR FROM THE UPGRADE ATTEMPT
 dpkg: error processing language-selector-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-gi: 
  python3-gi depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-gi (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of bluez: 
  bluez depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  
 dpkg: error processing bluez (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-menus: 
  gnome-menus depends on python3 (>= 3.1); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing gnome-menus (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-panel: 
  gnome-panel depends on gnome-menus (>= 3.1.4); however: 
   Package gnome-menus is not configured yet. 
  
 dpkg: error processing gnome-panel (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-session-fallback: 
  gnome-session-fallback depends on gnome-panel (>= 3.0); however: 
   Package gnome-panel is not configured yet. 
  
 dpkg: error processing gnome-session-fallback (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-bluetooth: 
  gnome-bluetooth depends on bluez (>= 4.36); however: 
   Package bluez is not configured yet. 
  
 dpkg: error processing gnome-bluetooth (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-shell: 
  gnome-shell depends on gnome-bluetooth (>= 3.0.0); however: 
   Package gnome-bluetooth is not configured yet. 
  
 dpkg: error processing gnome-shell (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-control-center: 
  gnome-control-center depends on gnome-menus (>= 2.12.0); however: 
   Package gnome-menus is not configured yet. 
  
 dpkg: error processing gnome-control-center (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of indicator-bluetooth: 
  indicator-bluetooth depends on gnome-bluetooth; however: 
   Package gnome-bluetooth is not configured yet. 
  
 dpkg: error processing indicator-bluetooth (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of kde-runtime: 
  kde-runtime depends on language-selector-common; however: 
   Package language-selector-common is not configured yet. 
  
 dpkg: error processing kde-runtime (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of k3b: 
  k3b depends on kde-runtime; however: 
   Package kde-runtime is not configured yet. 
  
 dpkg: error processing k3b (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of k3b-i18n: 
  k3b-i18n depends on k3b; however: 
   Package k3b is not configured yet. 
  
 dpkg: error processing k3b-i18n (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of language-pack-kde-en: 
  language-pack-kde-en depends on k3b-i18n; however: 
   Package k3b-i18n is not configured yet. 
  
 dpkg: error processing language-pack-kde-en (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-xkit: 
  python3-xkit depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-xkit (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ubuntu-drivers-common: 
  ubuntu-drivers-common depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  ubuntu-drivers-common depends on python3-apt; however: 
   Package python3-apt is not configured yet. 
  ubuntu-drivers-common depends on python3-xkit; however: 
   Package python3-xkit is not configured yet. 
  
 dpkg: error processing ubuntu-drivers-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-pkg-resources: 
  python3-pkg-resources depends on python3 (>= 3.2); however: 
   Package python3 is not configured yet. 
  python3-pkg-resources depends on python3 (<< 3.4); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-pkg-resources (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of python3-crypto: 
  python3-crypto depends on python3 (>= 3.3); however: 
   Package python3 is not configured yet. 
  python3-crypto depends on python3 (<< 3.4); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-crypto (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of python3-oauthlib: 
  python3-oauthlib depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-oauthlib depends on python3-crypto; however: 
   Package python3-crypto is not configured yet. 
  
 dpkg: error processing python3-oauthlib (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of friends-dispatcher: 
  friends-dispatcher depends on python3-pkg-resources; however: 
   Package python3-pkg-resources is not configured yet. 
  friends-dispatcher depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  friends-dispatcher depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  friends-dispatcher depends on python3-oauthlib; however: 
   Package python3-oauthlib is not configured yet. 
  friends-dispatcher depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing friends-dispatcher (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of libfriends0: 
  libfriends0 depends on friends-dispatcher; however: 
   Package friends-dispatcher is not configured yet. 
  
 dpkg: error processing libfriends0 (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of lsb-release: 
  lsb-release depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing lsb-release (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of ubuntu-minimal: 
  ubuntu-minimal depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  ubuntu-minimal depends on python3; however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing ubuntu-minimal (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of python3-gdbm:i386: 
  python3-gdbm:i386 depends on python3 (>= 3.3); however: 
   Package python3 is not configured yet. 
  python3-gdbm:i386 depends on python3 (<< 3.4); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-gdbm:i386 (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-commandnotfound: 
  python3-commandnotfound depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  python3-commandnotfound depends on python3-apt; however: 
   Package python3-apt is not configured yet. 
  python3-commandnotfound depends on python3-gdbm; however: 
   Package python3-gdbm:i386 is not configured yet. 
  python3-commandnotfound depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-commandnotfound (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of command-not-found: 
  command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however: 
   Package python3-commandnotfound is not configured yet. 
  
 dpkg: error processing command-not-found (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of python3-distupgrade: 
  python3-distupgrade depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-distupgrade depends on python3-apt (>= 0.8.5~); however: 
   Package python3-apt is not configured yet. 
  python3-distupgrade depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing python3-distupgrade (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-update-manager:No apport report written because MaxReports is reached already 
  
  python3-update-manager depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-update-manager depends on python3-apt (>= 0.8.5~); however: 
   Package python3-apt is not configured yet. 
  python3-update-manager depends on python3-distupgrade; however: 
   Package python3-distupgrade is not configured yet. 
  python3-update-manager depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing python3-update-manager (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:No apport report written because MaxReports is reached already 
  
  ubuntu-release-upgrader-core depends on python3 (>= 3.2); however: 
   Package python3 is not configured yet. 
  ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.192.12); however: 
   Package python3-distupgrade is not configured yet. 
  
 dpkg: error processing ubuntu-release-upgrader-core (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ubuntu-standard:No apport report written because MaxReports is reached already 
  
  ubuntu-standard depends on language-selector-common; however: 
   Package language-selector-common is not configured yet. 
  
 dpkg: error processing ubuntu-standard (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ufw:No apport report written because MaxReports is reached already 
  
  ufw depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing ufw (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of update-manager-core:No apport report written because MaxReports is reached already 
  
  update-manager-core depends on python3 (>= 3.2); however: 
   Package python3 is not configured yet. 
  update-manager-core depends on python3-update-manager (= 1:0.186.1); however: 
   Package python3-update-manager is not configured yet. 
  update-manager-core depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  update-manager-core depends on ubuntu-release-upgrader-core; however: 
   Package ubuntu-release-upgrader-core is not configured yet. 
  
 dpkg: error processing update-manager-core (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-problem-report:No apport report written because MaxReports is reached already 
  
  python3-problem-report depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-problem-report (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-apport:No apport report written because MaxReports is reached already 
  
  python3-apport depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-apport depends on python3-apt (>= 0.7.9); however: 
   Package python3-apt is not configured yet. 
  python3-apport depends on python3-problem-report (>= 0.94); however: 
   Package python3-problem-report is not configured yet. 
  python3-apport depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing python3-apport (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apport:No apport report written because MaxReports is reached already 
  
  apport depends on python3; however: 
   Package python3 is not configured yet. 
  apport depends on python3-apport (>= 2.9.2-0ubuntu8.3); however: 
   Package python3-apport is not configured yet. 
  apport depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  
 dpkg: error processing apport (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apport-gtk:No apport report written because MaxReports is reached already 
  
  apport-gtk depends on python3; however: 
   Package python3 is not configured yet. 
  apport-gtk depends on python3-apport (>= 2.9.2-0ubuntu8.3); however: 
   Package python3-apport is not configured yet. 
  apport-gtk depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  apport-gtk depends on apport (>= 0.41); however: 
   Package apport is not configured yet. 
  
 dpkg: error processing apport-gtk (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apturl-common:No apport report written because MaxReports is reached already 
  
  apturl-common depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  apturl-common depends on python3-apt; however: 
   Package python3-apt is not configured yet. 
  apturl-common depends on python3-update-manager; however: 
   Package python3-update-manager is not configured yet. 
  
 dpkg: error processing apturl-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of unattended-upgrades:No apport report written because MaxReports is reached already 
  
  unattended-upgrades depends on python3; however: 
   Package python3 is not configured yet. 
  unattended-upgrades depends on python3-apt (>= 0.7.90); however: 
   Package python3-apt is not configured yet. 
  unattended-upgrades depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing unattended-upgrades (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-software-properties:No apport report written because MaxReports is reached already 
  
  python3-software-properties depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-software-properties depends on python3-apt (>= 0.6.20ubuntu16); however: 
   Package python3-apt is not configured yet. 
  python3-software-properties depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  python3-software-properties depends on unattended-upgrades; however: 
   Package unattended-upgrades is not configured yet. 
  
 dpkg: error processing python3-software-properties (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of software-properties-common:No apport report written because MaxReports is reached already 
  
  software-properties-common depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  software-properties-common depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  software-properties-common depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  software-properties-common depends on python3-software-properties; however: 
   Package python3-software-properties is not configured yet. 
  
 dpkg: error processing software-properties-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-aptdaemon:No apport report written because MaxReports is reached already 
  
  python3-aptdaemon depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-aptdaemon depends on python3-apt (>= 0.8.5~ubuntu1); however: 
   Package python3-apt is not configured yet. 
  python3-aptdaemon depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  python3-aptdaemon depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  python3-aptdaemon depends on python3-pkg-resources; however: 
   Package python3-pkg-resources is not configured yet. 
  
 dpkg: error processing python3-aptdaemon (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:No apport report written because MaxReports is reached already 
  
  python3-aptdaemon.gtk3widgets depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-aptdaemon.gtk3widgets depends on python3-aptdaemon (= 1.0-0ubuntu9); however: 
   Package python3-aptdaemon is not configured yet. 
  python3-aptdaemon.gtk3widgets depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  
 dpkg: error processing python3-aptdaemon.gtk3widgets (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of software-properties-gtk:No apport report written because MaxReports is reached already 
  
  software-properties-gtk depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  software-properties-gtk depends on python3-software-properties; however: 
   Package python3-software-properties is not configured yet. 
  software-properties-gtk depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  software-properties-gtk depends on python3-aptdaemon.gtk3widgets; however: 
   Package python3-aptdaemon.gtk3widgets is not configured yet. 
  software-properties-gtk depends on software-properties-common; however: 
   Package software-properties-common is not configured yet. 
  software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however: 
   Package ubuntu-drivers-common is not configured yet. 
  
 dpkg: error processing software-properties-gtk (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apturl:No apport report written because MaxReports is reached already 
  
  apturl depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  apturl depends on apturl-common (= 0.5.2ubuntu1); however: 
   Package apturl-common is not configured yet. 
  apturl depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  apturl depends on software-properties-gtk; however: 
   Package software-properties-gtk is not configured yet. 
  apturl depends on python3-aptdaemon; however: 
   Package python3-aptdaemon is not configured yet. 
  apturl depends on python3-aptdaemon.gtk3widgets; however: 
   Package python3-aptdaemon.gtk3widgets is not configured yet. 
  
 dpkg: error processing apturl (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of bluez-alsa:i386:No apport report written because MaxReports is reached already 
  
  bluez-alsa:i386 depends on bluez; however: 
   Package bluez is not configured yet. 
  
 dpkg: error processing bluez-alsa:i386 (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: too many errors, stopping 
 Errors were encountered while processing: 
  python3.3-minimal 
  python3-minimal 
  python3.3 
  python3 
  python3-apt 
  python3-dbus 
  language-selector-common 
  python3-gi 
  bluez 
  gnome-menus 
  gnome-panel 
  gnome-session-fallback 
  gnome-bluetooth 
  gnome-shell 
  gnome-control-center 
  indicator-bluetooth 
  kde-runtime 
  k3b 
  k3b-i18n Sub-process /usr/bin/dpkg returned an error code (1)
  language-pack-kde-en 
  python3-xkit 
  ubuntu-drivers-common 
  python3-pkg-resources 
  python3-crypto 
  python3-oauthlib 
  friends-dispatcher 
  libfriends0 
  lsb-release 
  ubuntu-minimal 
  python3-gdbm:i386 
  python3-commandnotfound 
  command-not-found 
  python3-distupgrade 
  python3-update-manager 
  ubuntu-release-upgrader-core 
  ubuntu-standard 
  ufw 
  update-manager-core 
  python3-problem-report 
  python3-apport 
  apport 
  apport-gtk 
  apturl-common 
  unattended-upgrades 
  python3-software-properties 
  software-properties-common 
  python3-aptdaemon 
  python3-aptdaemon.gtk3widgets 
  software-properties-gtk 
  apturl 
  bluez-alsa:i386 
 Processing was halted because there werE: Sub-process /usr/bin/dpkg returned an error code (1) 


**ERROR FROM fsck**[/I]
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

[I]fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.


[/I]
```

---

### Post by Bashing-om on 2013-08-06
jacob4; Hi !

As the error from the file system check advises, sda1 is mounted. One can not check/repair the file system when in use ... That repair is best run from a liveDVD(USB) environment.
Boot up from the LiveDVD and enter the terminal codes:
```
 
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response 
sudo e2fsck -f -y -v /dev/sda1

```
see: man e2fsck
then:
```

sudo apt-get update
sudo apt-get upgrade

``` to see what state the system is now in.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2013-08-06
Please post the output of:

```
sudo apt-get update
```

And please use code tags or else your thread is going to be a mile long :)

```
***ERROR FROM THE UPGRADE ATTEMPT***
[I]Package python3-apt is not configured yet. 

  language-selector-common depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  ERROR FROM THE UPGRADE ATTEMPT
 dpkg: error processing language-selector-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-gi: 
  python3-gi depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-gi (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of bluez: 
  bluez depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  
 dpkg: error processing bluez (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-menus: 
  gnome-menus depends on python3 (>= 3.1); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing gnome-menus (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-panel: 
  gnome-panel depends on gnome-menus (>= 3.1.4); however: 
   Package gnome-menus is not configured yet. 
  
 dpkg: error processing gnome-panel (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-session-fallback: 
  gnome-session-fallback depends on gnome-panel (>= 3.0); however: 
   Package gnome-panel is not configured yet. 
  
 dpkg: error processing gnome-session-fallback (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-bluetooth: 
  gnome-bluetooth depends on bluez (>= 4.36); however: 
   Package bluez is not configured yet. 
  
 dpkg: error processing gnome-bluetooth (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-shell: 
  gnome-shell depends on gnome-bluetooth (>= 3.0.0); however: 
   Package gnome-bluetooth is not configured yet. 
  
 dpkg: error processing gnome-shell (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of gnome-control-center: 
  gnome-control-center depends on gnome-menus (>= 2.12.0); however: 
   Package gnome-menus is not configured yet. 
  
 dpkg: error processing gnome-control-center (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of indicator-bluetooth: 
  indicator-bluetooth depends on gnome-bluetooth; however: 
   Package gnome-bluetooth is not configured yet. 
  
 dpkg: error processing indicator-bluetooth (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of kde-runtime: 
  kde-runtime depends on language-selector-common; however: 
   Package language-selector-common is not configured yet. 
  
 dpkg: error processing kde-runtime (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of k3b: 
  k3b depends on kde-runtime; however: 
   Package kde-runtime is not configured yet. 
  
 dpkg: error processing k3b (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of k3b-i18n: 
  k3b-i18n depends on k3b; however: 
   Package k3b is not configured yet. 
  
 dpkg: error processing k3b-i18n (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of language-pack-kde-en: 
  language-pack-kde-en depends on k3b-i18n; however: 
   Package k3b-i18n is not configured yet. 
  
 dpkg: error processing language-pack-kde-en (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-xkit: 
  python3-xkit depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-xkit (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ubuntu-drivers-common: 
  ubuntu-drivers-common depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  ubuntu-drivers-common depends on python3-apt; however: 
   Package python3-apt is not configured yet. 
  ubuntu-drivers-common depends on python3-xkit; however: 
   Package python3-xkit is not configured yet. 
  
 dpkg: error processing ubuntu-drivers-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-pkg-resources: 
  python3-pkg-resources depends on python3 (>= 3.2); however: 
   Package python3 is not configured yet. 
  python3-pkg-resources depends on python3 (<< 3.4); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-pkg-resources (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg:  dependency problems prevent configuration of python3-crypto: 
  python3-crypto depends on python3 (>= 3.3); however: 
   Package python3 is not configured yet. 
  python3-crypto depends on python3 (<< 3.4); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-crypto (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg:  dependency problems prevent configuration of python3-oauthlib: 
  python3-oauthlib depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-oauthlib depends on python3-crypto; however: 
   Package python3-crypto is not configured yet. 
  
 dpkg: error processing python3-oauthlib (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg:  dependency problems prevent configuration of friends-dispatcher: 
  friends-dispatcher depends on python3-pkg-resources; however: 
   Package python3-pkg-resources is not configured yet. 
  friends-dispatcher depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  friends-dispatcher depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  friends-dispatcher depends on python3-oauthlib; however: 
   Package python3-oauthlib is not configured yet. 
  friends-dispatcher depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing friends-dispatcher (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of libfriends0: 
  libfriends0 depends on friends-dispatcher; however: 
   Package friends-dispatcher is not configured yet. 
  
 dpkg: error processing libfriends0 (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of lsb-release: 
  lsb-release depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing lsb-release (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg:  dependency problems prevent configuration of ubuntu-minimal: 
  ubuntu-minimal depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  ubuntu-minimal depends on python3; however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing ubuntu-minimal (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg:  dependency problems prevent configuration of python3-gdbm:i386: 
  python3-gdbm:i386 depends on python3 (>= 3.3); however: 
   Package python3 is not configured yet. 
  python3-gdbm:i386 depends on python3 (<< 3.4); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-gdbm:i386 (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-commandnotfound: 
  python3-commandnotfound depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  python3-commandnotfound depends on python3-apt; however: 
   Package python3-apt is not configured yet. 
  python3-commandnotfound depends on python3-gdbm; however: 
   Package python3-gdbm:i386 is not configured yet. 
  python3-commandnotfound depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-commandnotfound (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg:  dependency problems prevent configuration of command-not-found: 
  command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however: 
   Package python3-commandnotfound is not configured yet. 
  
 dpkg: error processing command-not-found (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg:  dependency problems prevent configuration of python3-distupgrade: 
  python3-distupgrade depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-distupgrade depends on python3-apt (>= 0.8.5~); however: 
   Package python3-apt is not configured yet. 
  python3-distupgrade depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing python3-distupgrade (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  python3-update-manager:No apport report written because MaxReports is  reached already 
  
  python3-update-manager depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-update-manager depends on python3-apt (>= 0.8.5~); however: 
   Package python3-apt is not configured yet. 
  python3-update-manager depends on python3-distupgrade; however: 
   Package python3-distupgrade is not configured yet. 
  python3-update-manager depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing python3-update-manager (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  ubuntu-release-upgrader-core:No apport report written because MaxReports  is reached already 
  
  ubuntu-release-upgrader-core depends on python3 (>= 3.2); however: 
   Package python3 is not configured yet. 
  ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.192.12); however: 
   Package python3-distupgrade is not configured yet. 
  
 dpkg: error processing ubuntu-release-upgrader-core (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ubuntu-standard:No  apport report written because MaxReports is reached already 
  
  ubuntu-standard depends on language-selector-common; however: 
   Package language-selector-common is not configured yet. 
  
 dpkg: error processing ubuntu-standard (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ufw:No apport report written because MaxReports is reached already 
  
  ufw depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing ufw (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  update-manager-core:No apport report written because MaxReports is  reached already 
  
  update-manager-core depends on python3 (>= 3.2); however: 
   Package python3 is not configured yet. 
  update-manager-core depends on python3-update-manager (= 1:0.186.1); however: 
   Package python3-update-manager is not configured yet. 
  update-manager-core depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  update-manager-core depends on ubuntu-release-upgrader-core; however: 
   Package ubuntu-release-upgrader-core is not configured yet. 
  
 dpkg: error processing update-manager-core (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  python3-problem-report:No apport report written because MaxReports is  reached already 
  
  python3-problem-report depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  
 dpkg: error processing python3-problem-report (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-apport:No  apport report written because MaxReports is reached already 
  
  python3-apport depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-apport depends on python3-apt (>= 0.7.9); however: 
   Package python3-apt is not configured yet. 
  python3-apport depends on python3-problem-report (>= 0.94); however: 
   Package python3-problem-report is not configured yet. 
  python3-apport depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing python3-apport (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apport:No apport report written because MaxReports is reached already 
  
  apport depends on python3; however: 
   Package python3 is not configured yet. 
  apport depends on python3-apport (>= 2.9.2-0ubuntu8.3); however: 
   Package python3-apport is not configured yet. 
  apport depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  
 dpkg: error processing apport (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apport-gtk:No apport report written because MaxReports is reached already 
  
  apport-gtk depends on python3; however: 
   Package python3 is not configured yet. 
  apport-gtk depends on python3-apport (>= 2.9.2-0ubuntu8.3); however: 
   Package python3-apport is not configured yet. 
  apport-gtk depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  apport-gtk depends on apport (>= 0.41); however: 
   Package apport is not configured yet. 
  
 dpkg: error processing apport-gtk (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apturl-common:No  apport report written because MaxReports is reached already 
  
  apturl-common depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  apturl-common depends on python3-apt; however: 
   Package python3-apt is not configured yet. 
  apturl-common depends on python3-update-manager; however: 
   Package python3-update-manager is not configured yet. 
  
 dpkg: error processing apturl-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  unattended-upgrades:No apport report written because MaxReports is  reached already 
  
  unattended-upgrades depends on python3; however: 
   Package python3 is not configured yet. 
  unattended-upgrades depends on python3-apt (>= 0.7.90); however: 
   Package python3-apt is not configured yet. 
  unattended-upgrades depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  
 dpkg: error processing unattended-upgrades (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  python3-software-properties:No apport report written because MaxReports  is reached already 
  
  python3-software-properties depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-software-properties depends on python3-apt (>= 0.6.20ubuntu16); however: 
   Package python3-apt is not configured yet. 
  python3-software-properties depends on lsb-release; however: 
   Package lsb-release is not configured yet. 
  python3-software-properties depends on unattended-upgrades; however: 
   Package unattended-upgrades is not configured yet. 
  
 dpkg: error processing python3-software-properties (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  software-properties-common:No apport report written because MaxReports  is reached already 
  
  software-properties-common depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  software-properties-common depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  software-properties-common depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  software-properties-common depends on python3-software-properties; however: 
   Package python3-software-properties is not configured yet. 
  
 dpkg: error processing software-properties-common (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of python3-aptdaemon:No  apport report written because MaxReports is reached already 
  
  python3-aptdaemon depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-aptdaemon depends on python3-apt (>= 0.8.5~ubuntu1); however: 
   Package python3-apt is not configured yet. 
  python3-aptdaemon depends on python3-dbus; however: 
   Package python3-dbus is not configured yet. 
  python3-aptdaemon depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  python3-aptdaemon depends on python3-pkg-resources; however: 
   Package python3-pkg-resources is not configured yet. 
  
 dpkg: error processing python3-aptdaemon (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  python3-aptdaemon.gtk3widgets:No apport report written because  MaxReports is reached already 
  
  python3-aptdaemon.gtk3widgets depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  python3-aptdaemon.gtk3widgets depends on python3-aptdaemon (= 1.0-0ubuntu9); however: 
   Package python3-aptdaemon is not configured yet. 
  python3-aptdaemon.gtk3widgets depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  
 dpkg: error processing python3-aptdaemon.gtk3widgets (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of  software-properties-gtk:No apport report written because MaxReports is  reached already 
  
  software-properties-gtk depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  software-properties-gtk depends on python3-software-properties; however: 
   Package python3-software-properties is not configured yet. 
  software-properties-gtk depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  software-properties-gtk depends on python3-aptdaemon.gtk3widgets; however: 
   Package python3-aptdaemon.gtk3widgets is not configured yet. 
  software-properties-gtk depends on software-properties-common; however: 
   Package software-properties-common is not configured yet. 
  software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however: 
   Package ubuntu-drivers-common is not configured yet. 
  
 dpkg: error processing software-properties-gtk (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of apturl:No apport report written because MaxReports is reached already 
  
  apturl depends on python3 (>= 3.2.3-3~); however: 
   Package python3 is not configured yet. 
  apturl depends on apturl-common (= 0.5.2ubuntu1); however: 
   Package apturl-common is not configured yet. 
  apturl depends on python3-gi; however: 
   Package python3-gi is not configured yet. 
  apturl depends on software-properties-gtk; however: 
   Package software-properties-gtk is not configured yet. 
  apturl depends on python3-aptdaemon; however: 
   Package python3-aptdaemon is not configured yet. 
  apturl depends on python3-aptdaemon.gtk3widgets; however: 
   Package python3-aptdaemon.gtk3widgets is not configured yet. 
  
 dpkg: error processing apturl (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of bluez-alsa:i386:No  apport report written because MaxReports is reached already 
  
  bluez-alsa:i386 depends on bluez; however: 
   Package bluez is not configured yet. 
  
 dpkg: error processing bluez-alsa:i386 (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: too many errors, stopping 
 Errors were encountered while processing: 
  python3.3-minimal 
  python3-minimal 
  python3.3 
  python3 
  python3-apt 
  python3-dbus 
  language-selector-common 
  python3-gi 
  bluez 
  gnome-menus 
  gnome-panel 
  gnome-session-fallback 
  gnome-bluetooth 
  gnome-shell 
  gnome-control-center 
  indicator-bluetooth 
  kde-runtime 
  k3b 
  k3b-i18n Sub-process /usr/bin/dpkg returned an error code (1)
  language-pack-kde-en 
  python3-xkit 
  ubuntu-drivers-common 
  python3-pkg-resources 
  python3-crypto 
  python3-oauthlib 
  friends-dispatcher 
  libfriends0 
  lsb-release 
  ubuntu-minimal 
  python3-gdbm:i386 
  python3-commandnotfound 
  command-not-found 
  python3-distupgrade 
  python3-update-manager 
  ubuntu-release-upgrader-core 
  ubuntu-standard 
  ufw 
  update-manager-core 
  python3-problem-report 
  python3-apport 
  apport 
  apport-gtk 
  apturl-common 
  unattended-upgrades 
  python3-software-properties 
  software-properties-common 
  python3-aptdaemon 
  python3-aptdaemon.gtk3widgets 
  software-properties-gtk 
  apturl 
  bluez-alsa:i386 
 Processing was halted because there werE: Sub-process /usr/bin/dpkg returned an error code (1) 


**ERROR FROM fsck**[/I]
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

[I]fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.[/I]
```

[ATTACH=CONFIG]245139[/ATTACH]

---

### Post by jacob4 on 2013-08-06
Here is the code from the update:

```
[I]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg [933 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed Release.gpg [933 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                                
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release [40.8 kB]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release                                      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed Release [40.8 kB]                           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources [14 B]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Sources                                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources [36.2 kB]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Sources                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Sources                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages                                     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources [1,825 B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages                              
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources [8,408 B]                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse i386 Packages                               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [94.3 kB]                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US                              
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en                             
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en        
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [32.2 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Sources [14 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,612 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources [57.4 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Sources [1,825 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en     
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Sources [67.9 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages [148 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages [133 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,612 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US                    
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/restricted i386 Packages [14 B]            
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/main i386 Packages [40.7 kB]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US                      
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/multiverse i386 Packages [14 B]            
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/universe i386 Packages [24.9 kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/main Translation-en                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/multiverse Translation-en                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/restricted Translation-en                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/universe Translation-en                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en_US                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/main Translation-en_US                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/multiverse Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/restricted Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed/universe Translation-en_US                    
Fetched 779 kB in 13s (56.7 kB/s)                                                              
Reading package lists... Done[/I]
```

---

### Post by QIII on 2013-08-06
jacob4:

Please enclose long strings of code between code tags.

You can do so by clicking the pound sign (#) above the text entry box, putting your cursor between the tags and pasting you text.

Alternately, paste your text, highlight it and click the #.

Thank you.

---

### Post by jacob4 on 2013-08-10
hello all....sorry just now back on. dad got sick and i've been preocuppied with that. anyway here goes. i took your advice **bashing-om** and ran fsck from live cd, followed your specific intructions carefully and still have the problem. nothing has changed. It seemd to get a bit further with the upgrade and then crashed again. When booting from live cd i chose the try ubuntu optin rather than install. open the terminal and run the code as sudo. is that correct? also i get a crash report....appears to be some problem with python. i've included the crash report here for you all to veiw. thanks again for all your help.

&#8203;&#8203;                                                                             #1173181                   [package  python3.3-minimal 3.3.1-1ubuntu5 failed to install/upgrade: subprocess  installed post-installation script returned error exit status 1]("https://bugs.launchpad.net/bugs/1173181")                                
                                                                        Confirmed                                                         (2                    comments)                   last updated                   2013-05-07                   [view this bug]("https://bugs.launchpad.net/bugs/1173181")                                
                                Different version info, x86 instead of 64
 ProblemType: Package
DistroRelease: Ubuntu 13.04
Package: python3.3-minimal 3.3.1-1ubuntu5
ProcVersionSignature: Ubuntu 3.8.0-19.29-generic 3.8.8
Uname: Linux 3.8.0-19-generic i686
ApportVersion: 2.9.2-0ubuntu8
Architecture: i386
Date: Fri Apr 26 08:03:58 2013
ErrorMessage: subprocess installed post-installation script returned error exit status 1
InstallationDate: Installed on 2012-12-31 (116 days ago)
InstallationMedia: Ubuntu 12.10 "Quantal Quetza...

---

### Post by ibjsb4 on 2013-08-10
This happen on a upgrade from 12.10 to 13.04?

Looks like you tried most all the standard fixes, if this is a upgrade bug you may just have to reinstall.  Even though you have tried standard fixes, give this a try:

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by jacob4 on 2013-08-12
is there a way to back everything up before a reinstall? i'm don't want to reinstall all my other programs and i also don't want to risk losing any data. thanks

jake

---

### Post by ibjsb4 on 2013-08-12
You can probably gain access to your files with a live cd/dvd.  Can you burn a copy of 12.04 (it will fit on a cd) or 13.04 (won't fit on a cd, has to be a dvd)?

You should be able to transfer your data to a usb stick or drive.

If you want a list of all your installed packages you can ..

[http://ubuntuforums.org/showthread.php?t=1139264&p=7157175&viewfull=1#post7157175](http://ubuntuforums.org/showthread.php?t=1139264&p=7157175&viewfull=1#post7157175)

That should work, depending on the shape of your current install.

---

### Post by jacob4 on 2013-08-12
well i've exhausted all the resources from the advice received here. i'll leave the thread open for a little longer see if anyone has any ideas. i'll most likely do attempt a fresh install next week. can anyone tell me how or why this might have happened? thanks again.

---

