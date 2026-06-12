---
title: "Fail to upgrade from 12.04 to 14.04"
date: 2014-08-24
forum: Installation &amp; Upgrades
---

### Post by Richiegs on 2014-08-24
I tried but failed to upgrade from Ubuntu 12.04 to 14.04 by using "Software Up to Date". It seemed an easy upgrade, but the computer said there might be errors. Thank you in advance for anyone who advises what to do.

---

### Post by Bashing-om on 2014-08-24
Richiegs; Sure !

Help is what we do.

For starters, see if you did make the transition:
```

cat /etc/issue
lsb_release -a
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
If all this looks "kosher", next is to look at the condition of installed packages.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Richiegs on 2014-08-27
I GOT THE FOLLOWING MESSAGE WHEN I TRIED TO UPGRADE FROM 12.04 TO 14.04 THROUGH SOFTWARE UP TO DATE:

"Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal."

WHAT SHOULD I DO NEXT? THANK YOU IN ADVANCE.

---

### Post by slickymaster on 2014-08-27
> **Richiegs said:**
> I GOT THE FOLLOWING MESSAGE WHEN I TRIED TO UPGRADE FROM 12.04 TO 14.04 THROUGH SOFTWARE UP TO DATE:

"Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal."

WHAT SHOULD I DO NEXT? THANK YOU IN ADVANCE.

The error message says it:
```
Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* **[COLOR=#ff0000]Unofficial software packages not provided by Ubuntu[/COLOR]**<---snip--->
```

Do you have any software from PPAs installed, or have you edited any of the default sources? If so, that's probably the problem. Disable any PPAs or other third-party repos and try again. If it still doesn't work you might need to actually uninstall some packages or replace them with versions from the official repos.
Look in **/var/log** for release-upgrader log files that will have more details.

---

### Post by Richiegs on 2014-08-27
I disabled all PPAs or third party repos, but it still gave me the same error message.

---

### Post by maclenin on 2014-08-27
**Richiegs!**

My advice:

1. Back-up your files (images / documents / config files etc) to an external (usb) hard drive....
2. Create a dvd or usb (stick) iso of the version of ubuntu you wish to install (e.g. 14.04.1)....
3. Take / keep note of those applications (configurations / ppas / sources) you have appended to the standard ubuntu install (so that you can re-install / re-apply them, later - if you choose to do so)....
3.a. When you are 100% sure you have backed-up everything / taken note of those applications you wish to re-install / configurations you wish to migrate...
4. ...insert the dvd or usb stick - re-start your machine - and do a complete blow-away-the-old re-install of ubuntu.

This is what I do every time I migrate to a latest (x)ubuntu - I never upgrade over top the current....

I also tend to migrate to a latest version "on the 4s" - or on the LTS (Long Term Support) versions (10.04, 12.04, 14.04) - so I only have to perform a full upgrade every ~4 years (though I still back-up regularly / and tend to upgrade more frequently)!

My experience has been clean and easy - and I don't worry about conflicts from earlier application versions - as a fresh install has the latest and (hopefully) greatest iterations of OS and applications - and I also force myself, in the process, to create a sound / simple / easily sustainable back-up / upgrade strategy!

Good luck!

---

### Post by slickymaster on 2014-08-27
Can you please run the following command and post back here in the thread its output, so we can see which package(s) might be preventing the upgrade.:```
grep Broken /var/log/dist-upgrade/apt.log
```

---

### Post by Richiegs on 2014-08-27
```
Broken python-aptdaemon.pkcompat:i386 Depends on python-aptdaemon [ i386 ] < 0.43+bzr805-0ubuntu9 -> 1.1.1-1ubuntu5 > ( python ) (= 0.43+bzr805-0ubuntu9)
Broken python3-aptdaemon.pkcompat:i386 Breaks on libpackagekit-glib2-14 [ i386 ] < 0.7.2-4ubuntu3 > ( libs )
Broken activity-log-manager:i386 Conflicts on activity-log-manager-common [ i386 ] < 0.9.4-0ubuntu3.2 > ( utils )
Broken libgdal1h:i386 Depends on libhdf5-7 [ i386 ] < none -> 1.8.11-5ubuntu7 > ( universe/libs )
Broken unity-gtk2-module:i386 Conflicts on appmenu-gtk [ i386 ] < 0.3.92-0ubuntu1.1 > ( libs )
Broken libperl5.14:i386 Depends on perl-base [ i386 ] < 5.14.2-6ubuntu2.4 -> 5.18.2-2ubuntu1 > ( perl ) (= 5.14.2-6ubuntu2.4)
Broken unity-gtk3-module:i386 Conflicts on appmenu-gtk3 [ i386 ] < 0.3.92-0ubuntu1.1 > ( libs )
Broken libnetcdfc7:i386 Depends on libhdf5-7 [ i386 ] < none -> 1.8.11-5ubuntu7 > ( universe/libs )
Broken friends-app:i386 Conflicts on gwibber-service [ i386 ] < 3.4.2-0ubuntu2.4 -> 3.7.0bzr13.04.05-0ubuntu1 > ( universe/misc )
Broken ubuntuone-client-data:i386 Breaks on ubuntuone-client [ i386 ] < 3.0.2-0ubuntu2.2 > ( net ) (< 4.1.90-0ubuntu3)
Broken gwibber:i386 Depends on friends-app [ i386 ] < none -> 0.92.0+14.04.20140306.1-0ubuntu2 > ( universe/gnome )
Broken python3-speechd:i386 Breaks on python-speechd [ i386 ] < 0.7.1-6ubuntu3 > ( python )
Broken librpmbuild2:i386 Depends on librpm2 [ i386 ] < 4.9.1.1-1ubuntu0.2 > ( libs ) (>= 4.9.0)
Broken ubuntuone-client-gnome:i386 Depends on libebook-1.2-12 [ i386 ] < 3.2.3-0ubuntu7.1 > ( libs ) (>= 3.2.3)
Broken libedataserverui-3.0-1:i386 Depends on libebook-1.2-12 [ i386 ] < 3.2.3-0ubuntu7.1 > ( libs ) (>= 3.2.3)
Broken libcogl-pango0:i386 Depends on libcogl9 [ i386 ] < 1.10.0-0ubuntu2 > ( libs ) (>= 1.9.6)
Broken libedata-book-1.2-11:i386 Depends on libebook-1.2-12 [ i386 ] < 3.2.3-0ubuntu7.1 > ( libs ) (>= 3.2.3)
Broken libunity-core-5.0-5:i386 Depends on unity-services [ i386 ] < 5.20.0-0ubuntu3 -> 7.2.2+14.04.20140714-0ubuntu1.1 > ( gnome ) (= 5.20.0-0ubuntu3)
Broken libexttextcat0:i386 Depends on libexttextcat-data [ i386 ] < 3.2.0-1ubuntu1 -> 3.4.3-1ubuntu1 > ( text ) (= 3.2.0-1ubuntu1)
Broken librpmsign0:i386 Depends on librpm2 [ i386 ] < 4.9.1.1-1ubuntu0.2 > ( libs ) (>= 4.9.0)
Broken libbamf3-0:i386 Depends on bamfdaemon [ i386 ] < 0.2.126-0ubuntu1 -> 0.5.1+14.04.20140409-0ubuntu1 > ( libs ) (= 0.2.126-0ubuntu1)
Broken libbamf0:i386 Depends on bamfdaemon [ i386 ] < 0.2.126-0ubuntu1 -> 0.5.1+14.04.20140409-0ubuntu1 > ( libs ) (= 0.2.126-0ubuntu1)
Broken ubuntu-sso-client-gtk:i386 Depends on python-ubuntu-sso-client [ i386 ] < 3.0.2-0ubuntu3 -> 13.10-0ubuntu6 > ( python ) (= 3.0.2-0ubuntu3)
Broken python-ubuntu-sso-client:i386 Breaks on python-ubuntuone-storageprotocol [ i386 ] < 3.0.2-0ubuntu1 > ( python ) (< 13.05)
Broken python-ubuntuone-client:i386 Depends on python-ubuntuone-storageprotocol [ i386 ] < 3.0.2-0ubuntu1 > ( python ) (>= 3.0.0-0ubuntu1.1)
Broken libopenscenegraph99:i386 Depends on libgdal1h [ i386 ] < none -> 1.10.1+dfsg-5ubuntu1 > ( universe/libs ) (>= 1.9.0)
Broken ubuntu-sso-client-qt:i386 Depends on ubuntuone-client-data [ i386 ] < none -> 13.05-0ubuntu1 > ( libs )
Broken ubuntu-desktop:i386 Depends on ubuntu-sso-client-qt [ i386 ] < 3.0.2-0ubuntu3 -> 13.10-0ubuntu6 > ( python )
Broken libsimgearscene3.0.0:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken python-ubuntu-sso-client:i386 Breaks on python-ubuntuone-storageprotocol [ i386 ] < 3.0.2-0ubuntu1 > ( python ) (< 13.05)
Broken python-ubuntuone-client:i386 Depends on python-ubuntuone-storageprotocol [ i386 ] < 3.0.2-0ubuntu1 > ( python ) (>= 3.0.0-0ubuntu1.1)
Broken ubuntuone-client:i386 Depends on python-ubuntuone-client [ i386 ] < 3.0.2-0ubuntu2.2 > ( python ) (= 3.0.2-0ubuntu2.2)
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken libsyncdaemon-1.0-1:i386 Depends on ubuntuone-client [ i386 ] < 3.0.2-0ubuntu2.2 > ( net ) (>= 3.0.2-0ubuntu2.2)
Broken python-ubuntuone-control-panel:i386 Depends on python-ubuntuone-client [ i386 ] < 3.0.2-0ubuntu2.2 > ( python ) (>= 2.99.92)
Broken libubuntuoneui-3.0-1:i386 Depends on libsyncdaemon-1.0-1 [ i386 ] < 3.0.2-0ubuntu2.2 > ( libs )
Broken gir1.2-ubuntuoneui-3.0:i386 Depends on libubuntuoneui-3.0-1 [ i386 ] < 3.0.1-0ubuntu1 > ( libs ) (>= 2.99.3)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken ubuntuone-control-panel:i386 Depends on python-ubuntuone-control-panel [ i386 ] < 3.0.1-0ubuntu1 > ( python ) (= 3.0.1-0ubuntu1)
Broken ubuntuone-couch:i386 Depends on python-ubuntuone-client [ i386 ] < 3.0.2-0ubuntu2.2 > ( python )
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
Broken flightgear-data-base:i386 Breaks on flightgear [ i386 ] < 2.4.0-1 -> 3.0.0-1 > ( universe/games ) (< 3.0.0~)
Broken flightgear:i386 Depends on libopenscenegraph99 [ i386 ] < none -> 3.2.0~rc1-4 > ( universe/libs )
```

---

### Post by slickymaster on 2014-08-27
[COLOR=#000000]I've edit you last post adding code tags to it. [/COLOR][COLOR=#000000]Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand and the [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

As to your issue I suspect that the [/COLOR]**[COLOR=#000000]flightgear[/COLOR]**[COLOR=#000000] package might be the culprit. [/COLOR][COLOR=#000000]How did you install it? From a PPA?

[/COLOR][COLOR=#000000]I would advise you to remove all the external PPAs you've added. From Software-Center > Edit > Software Sources > Other Software, do not only untick them,but delete them.[/COLOR]

---

### Post by macflav on 2014-08-30
I managed to solve the problem without removing any packages. On the settings for the update manager, I unchecked all of the Ubuntu Software options, leaving only the first box checked -- "Canonical-supported free and open-source software (main)".

[EDIT] I have FlightGear installed also. The "broken" packages were way too many to even consider removing them all. Hopefully the solution was as simple as I just reported.

---

