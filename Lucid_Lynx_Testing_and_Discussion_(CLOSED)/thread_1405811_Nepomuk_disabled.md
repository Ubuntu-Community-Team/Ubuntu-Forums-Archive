---
title: "Nepomuk disabled?"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cookiecruncher on 2010-02-13
Is it only me or are people here getting a popup message every now and then informing me that 'nepomuk' is disabled?  Message is as follows:

> Nepomuk Indexing Agents Have Been Disabled
The Nepomuk service is not available or fully operational and attempts to rectify this have failed. Therefore indexing of all data stored in the Akonadi PIM service has been disabled, which will severely limit the capabilities of any application using this data.

The following problems were detected:
 
[LIST]
[*]Calling the Nepomuk storage service failed: 'Message did not receive a reply (timeout by message bus)'.
[/LIST]
 


EDIT.
Found this:
[http://userbase.kde.org/Akonadi](http://userbase.kde.org/Akonadi)

---

### Post by Reiger on 2010-02-13
No not since virtuoso 5 hit the repositories, at least. (Currently we are on virtuoso 6.) But you might want to check:
(a) That you have the nepomuk & virtuoso (minimal) packages installed.
(b) That you have libiodbc and soprano packages installed.
(c) That you have strigi instaleld
(d) That you have System settings (Desktop Search) configured to enable Nepomuk (and strigi).

(c) Can probably be dropped if you do not enable strigi.

If you have all that you might want to log out of your current KDE session, and from a tty (Ctrl, Alt + F1 thru F9) issue:
```

# delete Nepomuk data
rm -r ~/.kde/share/apps/nepomuk
# restart the PC.
sudo reboot

```

---

### Post by cookiecruncher on 2010-02-13
> # delete Nepomuk data
rm -r ~/.kde/share/apps/nepomuk
# restart the PC.
sudo rebootI've searched for 'nepomuk' under '~/.kde/share/apps' and found it isn't there.

> # apt-get install strigi
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package strigi
> # apt-get install nepomuk
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nepomuk


---

### Post by Reiger on 2010-02-13
These are not &#8220;direct package names&#8221;. Use as search terms, 'cause there is a whole load of them, and decide what you need.

Here is my list:
```

sudo aptitude search soprano | grep ^i
i A libsmokesoprano3                - Soprano Smoke library
i   libsoprano4                     - libraries for the Soprano RDF framework
i   soprano-daemon                  - daemon for the Soprano RDF framework
sudo aptitude search nepomuk | grep ^i
i   virtuoso-nepomuk                - OpenLink Virtuoso Open-Source Edition (OSE
sudo aptitude search libiodbc | grep ^i
i   libiodbc2                       - iODBC Driver Manager
sudo aptitude search virtuoso | grep ^i
i   virtuoso-minimal                - Virtuoso minimal Server (metapackage for l
i   virtuoso-nepomuk                - OpenLink Virtuoso Open-Source Edition (OSE
i   virtuoso-opensource-6.0         - OpenLink Virtuoso Open-Source Edition - Se
i A virtuoso-opensource-6.0-bin     - OpenLink Virtuoso Open-Source Edition - Se
i A virtuoso-opensource-6.0-common  - OpenLink Virtuoso Open-Source Edition - Co
i   virtuoso-server                 - Virtuoso OSE Server (metapackage for lates
i A virtuosoconverter               - converts nepomuk database to Virtuoso 6.1.
sudo aptitude search strigi | grep ^i
i   kdegraphics-strigi-plugins      - graphics file format plugins for Strigi De
i   kdepim-strigi-plugins           - PIM file format plugins for Strigi Desktop
i A libstrigihtmlgui0               - library for writing html clients for Strig
i A libstrigiqtdbusclient0          - library for writing D-Bus clients for Stri
i   strigi-client                   - Qt4 client for Strigi Desktop Search
i   strigi-daemon                   - fast indexing and searching tool for your

```

---

### Post by lovinglinux on 2010-02-13
I was getting those warnings on KDE 4.4 installed over Karmic. Looks like they stopped since I have enabled both desktop search options (Nepomuk and Strigi)

---

### Post by lovinglinux on 2010-02-14
> **lovinglinux said:**
> I was getting those warnings on KDE 4.4 installed over Karmic. Looks like they stopped since I have enabled both desktop search options (Nepomuk and Strigi)

I had t turn them off again, since virtuoso was using 35% of my CPUs, even with the strigi indexer paused.

---

### Post by jbernardo on 2010-02-14
I turned off strigi and nepomuk since it was keeping my netbook fan running all the time, and exhausting my battery faster, as it runs in the background. Now I always get the akonadi warning on login - and it is kind of irrelevant, since I know that nepomuk isn't running...

---

### Post by Seren on 2010-02-14
Anyone got the Dolphin Nepomuk search working under Lucid ?

I have upgraded to virtuoso 6, converted my db.

The search from krunner is working properly, but the search through Dolphin search bar does not find anything.

(I have no warning either, like nepomuk not being running or not correctly installed).

---

