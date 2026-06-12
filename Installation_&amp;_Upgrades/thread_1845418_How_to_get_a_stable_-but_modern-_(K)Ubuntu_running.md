---
title: "How to get a stable -but modern- (K)Ubuntu running?"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by mue.de on 2011-09-17
I want to rely on my kubuntu system but also need some newer functions of quite few applications (such as DigiKam, Amarok , Eclipse) which are a few years old in the repositories of (K)ubuntu Lucid Lynx.
Following some tips my system got sometimes completely unusable, so what is the right way ?

---

### Post by dino99 on 2011-09-17
you can upgrade to maverick, then natty :)

---

### Post by ld114 on 2011-09-17
I started with an installation of Lucid Lynx just a few months ago, but quickly found that I could upgrade to Natty on the same machine. That proved a better way to get more up to date versions of apps, than tyring to tweak them based on an earlier version of the OS. This might also work for you. (I am running Ubuntu, but with the KDE desktop installed so that I can have Ubuntu and Kubuntu options at login.)

---

### Post by mue.de on 2011-09-17
Thanks for reply,

but my primary choice is a stable system, secondary the newer applications.
My last dist-upgrade from Hardy heron to lucid lynx ended in a disaster, i almost had to set up a new system.
Now -after some experiments with 'backport' repos- i'm one year later quite at the same point again.
So how would you translate 'Ein gebranntes Kind scheut das Feuer' : my first aim is to keep all my running applications running.
I don't have enough harddisk space (just 250GB for Dual-Boot Windows and  Linux), to use a separate Test-Ubuntu on that Laptop, but i have Natty  Narwhal running at my daughter's Siemens Desktop.
I read a lot of trouble switching to natty narwhal; even my first  experience with that distro gave me a feeling of that 'kindly new  world': Two steps forward and **5** steps back?
I even couldn't boot a live dvd to the point of a running gui with natty  narwhal on the Toshiba Laptop where Lucid Lynx boots out of the box !
I just want to setup a clean system based on Lucid Lynx (LTS): what repos are (for kubuntu and german localisation) standard?
What kind of packet manager is reliable in emergency situation?
If i use KPackagekit it's only available in a gui, if use apt-get after  some trials i get the message to use a more powerful packetmanager as  synaptic or aptitude; aptitude helped me sometimes but has a cryptic  user interface; using a long time synaptic i was told, that it's no  longer recommended, i should use kpackagekit : the circle is complete.
Aptitude was my favorite -at the command line- to ignite the wonderful  system self heeling capabilities, but something didn't work right after  that; now it's the QDBUS (USB-auto-Mounting doesn't work anymore).

---

### Post by SeijiSensei on 2011-09-17
For my money, Maverick 10.10 remains the most stable version of Kubuntu available.  It does mean you'll be stuck with KDE 4.5 for a while.  The Kubuntu maintainers in their infinite wisdom removed the 4.6 binaries from the backports repository and offer no upgrade for Maverick at all. 

I'm waiting to see if 12.04 will be worth upgrading to.  My first couple of attempts with 11.10 alpha/beta haven't been too successful, but it will include KDE 4.7. That's why I figure 12.04 might be the best next choice, just as 10.10 fixed a lot of problems with Kubuntu 10.04.

For Maverick, digikam is at version 1.4.0.  I don't use amarok, preferring [Clementine]("http://www.clementine-player.org/downloads") instead. I don't use Eclipse at all, but it appears to be at version 5.6 in Maverick.

I still use synaptic from time to time, but KPackageKit has improved quite a bit.  Most of the time, though, I install packages from the command line with apt-get.

PS:  I don't know how the versions for Lucid can be "years" old when Lucid itself was released in April, 2010.

---

### Post by mue.de on 2011-09-18
Ok, I'll try Maverik in the next future; meanwhile my system is running quite fine again.
One disadvantage is, that Digikam got downgraded to V1.4.0 (i had compiled 2.1.0 before), Amarok is now V2.4.0, so the backports are working now.
The error 'Kein Kontact zu KDED' is still present and the behavior on plugging in usb-drives isn't ok;
 even after the 'clean-up' listed below:

I did the whole command sequence as mentioned in [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)
```

p, li { white-space: pre-wrap; } [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo fuser -vvv /var/lib/dpkg/lock[/FONT]
 [FONT=Sans Serif][sudo] password for muelux: [/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ cat /etc/lsb-release[/FONT]
 [FONT=Sans Serif]DISTRIB_ID=Ubuntu[/FONT]
 [FONT=Sans Serif]DISTRIB_RELEASE=10.04[/FONT]
 [FONT=Sans Serif]DISTRIB_CODENAME=lucid[/FONT]
 [FONT=Sans Serif]DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ uname -a[/FONT]
 [FONT=Sans Serif]Linux muelux-LT6cA 2.6.32-34-generic #76-Ubuntu SMP Tue Aug 30 16:19:34 UTC 2011 i686 GNU/Linux[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo rm /var/lib/apt/lists/lock[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo rm -rf /var/lib/dpkg/updates/*[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo rm -rf /var/lib/apt/lists[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo rm /var/cache/apt/*.bin[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo mkdir /var/lib/apt/lists[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo mkdir /var/lib/apt/lists/partial[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ LANG=C;sudo apt-get clean[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ LANG=C;sudo apt-get autoclean[/FONT]
 [FONT=Sans Serif]Reading package lists... Done[/FONT]
 [FONT=Sans Serif]Building dependency tree       [/FONT]
 [FONT=Sans Serif]Reading state information... Done[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ LANG=C;sudo apt-get --purge autoremove[/FONT]
 [FONT=Sans Serif]Reading package lists... Done[/FONT]
 [FONT=Sans Serif]Building dependency tree       [/FONT]
 [FONT=Sans Serif]Reading state information... Done[/FONT]
 [FONT=Sans Serif]The following packages will be REMOVED:[/FONT]
 [FONT=Sans Serif]  kde-minimal* kdebase*[/FONT]
 [FONT=Sans Serif]0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.[/FONT]
 [FONT=Sans Serif]After this operation, 73.7kB disk space will be freed.[/FONT]
 [FONT=Sans Serif]Do you want to continue [Y/n]? Y[/FONT]
 [FONT=Sans Serif](Reading database ... [/FONT]
 [FONT=Sans Serif]dpkg: warning: files list file for package `kde-minimal' missing, assuming package has no files currently installed.[/FONT]
 [FONT=Sans Serif][/FONT]
 [FONT=Sans Serif]dpkg: warning: files list file for package `kdebase' missing, assuming package has no files currently installed.[/FONT]
 [FONT=Sans Serif](Reading database ... 423780 files and directories currently installed.)[/FONT]
 [FONT=Sans Serif]Removing kdebase ...[/FONT]
 [FONT=Sans Serif]Removing kde-minimal ...[/FONT]
 p, li { white-space: pre-wrap; } [FONT=Sans Serif]muelux@muelux-LT6cA:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824[/FONT]
 [FONT=Sans Serif]Get:1 http://archive.ubuntu.com lucid Release.gpg [189B][/FONT]
 [FONT=Sans Serif]Get:2 http://archive.ubuntu.com lucid-updates Release.gpg [198B]                                    [/FONT]
 [FONT=Sans Serif]Get:3 http://archive.ubuntu.com lucid-security Release.gpg [198B]                [/FONT]
 [FONT=Sans Serif]Get:4 http://ppa.launchpad.net lucid Release.gpg [316B]                                             [/FONT]
 [FONT=Sans Serif]Get:5 http://ppa.launchpad.net lucid Release.gpg [316B]                                             [/FONT]
 [FONT=Sans Serif]Get:6 http://archive.ubuntu.com lucid-backports Release.gpg [198B]                                  [/FONT]
 [FONT=Sans Serif]Get:7 http://archive.ubuntu.com lucid Release [57.2kB]                                              [/FONT]
 [FONT=Sans Serif]Get:8 http://ppa.launchpad.net lucid Release [13.9kB]                                               [/FONT]
 [FONT=Sans Serif]Get:9 http://ppa.launchpad.net lucid Release [14.0kB]                                               [/FONT]
 [FONT=Sans Serif]Get:10 http://archive.ubuntu.com lucid-updates Release [44.7kB]                                     [/FONT]
 [FONT=Sans Serif]Get:11 http://download.virtualbox.org lucid Release.gpg [197B]              [/FONT]
 [FONT=Sans Serif]Get:12 http://ppa.launchpad.net lucid/main Packages [7552B]                 [/FONT]
 [FONT=Sans Serif]Get:13 http://ppa.launchpad.net lucid/main Sources [1138B]                                          [/FONT]
 [FONT=Sans Serif]Get:14 http://archive.ubuntu.com lucid-security Release [44.7kB]              [/FONT]
 [FONT=Sans Serif]Get:15 http://ppa.launchpad.net lucid/main Packages [106kB]                                         [/FONT]
 [FONT=Sans Serif]Get:16 http://archive.ubuntu.com lucid-backports Release [38.5kB]                    [/FONT]
 [FONT=Sans Serif]Get:17 http://archive.ubuntu.com lucid/main Packages [1386kB]                                       [/FONT]
 [FONT=Sans Serif]Get:18 http://download.virtualbox.org lucid Release [5447B]                                         [/FONT]
 [FONT=Sans Serif]Get:19 http://ppa.launchpad.net lucid/main Sources [33.2kB]                                         [/FONT]
 [FONT=Sans Serif]Get:20 http://download.virtualbox.org lucid/contrib Packages [1298B]                                [/FONT]
 [FONT=Sans Serif]Get:21 http://download.virtualbox.org lucid/non-free Packages [1320B][/FONT]
 [FONT=Sans Serif]Get:22 http://archive.ubuntu.com lucid/universe Packages [5448kB][/FONT]
 [FONT=Sans Serif]Get:23 http://archive.ubuntu.com lucid/restricted Packages [6208B]                                  [/FONT]
 [FONT=Sans Serif]Get:24 http://archive.ubuntu.com lucid/main Sources [659kB]                                         [/FONT]
 [FONT=Sans Serif]Get:25 http://archive.ubuntu.com lucid/universe Sources [3165kB]                                    [/FONT]
 [FONT=Sans Serif]Get:26 http://archive.ubuntu.com lucid-updates/main Packages [513kB]                                [/FONT]
 [FONT=Sans Serif]Get:27 http://archive.ubuntu.com lucid-updates/universe Packages [225kB]                            [/FONT]
 [FONT=Sans Serif]Get:28 http://archive.ubuntu.com lucid-updates/restricted Packages [3240B]                          [/FONT]
 [FONT=Sans Serif]Get:29 http://archive.ubuntu.com lucid-updates/main Sources [201kB]                                 [/FONT]
 [FONT=Sans Serif]Get:30 http://archive.ubuntu.com lucid-updates/universe Sources [80.4kB]                            [/FONT]
 [FONT=Sans Serif]Get:31 http://archive.ubuntu.com lucid-security/main Packages [205kB]                               [/FONT]
 [FONT=Sans Serif]Get:32 http://archive.ubuntu.com lucid-security/universe Packages [83.9kB]                          [/FONT]
 [FONT=Sans Serif]Get:33 http://archive.ubuntu.com lucid-security/restricted Packages [14B]                           [/FONT]
 [FONT=Sans Serif]Get:34 http://archive.ubuntu.com lucid-security/main Sources [62.9kB]                               [/FONT]
 [FONT=Sans Serif]Get:35 http://archive.ubuntu.com lucid-security/universe Sources [25.8kB]                           [/FONT]
 [FONT=Sans Serif]Get:36 http://archive.ubuntu.com lucid-backports/universe Packages [42.4kB]                         [/FONT]
 [FONT=Sans Serif]Get:37 http://archive.ubuntu.com lucid-backports/main Packages [15.6kB]                             [/FONT]
 [FONT=Sans Serif]Get:38 http://archive.ubuntu.com lucid-backports/restricted Packages [14B]                          [/FONT]
 [FONT=Sans Serif]Fetched 12.5MB in 12s (966kB/s)                                                                     [/FONT]
 [FONT=Sans Serif]Reading package lists... Done[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$[/FONT]
 p, li { white-space: pre-wrap; } [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo dpkg --clear-avail[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ sudo dpkg --configure -a[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ LANG=C;sudo apt-get -f install[/FONT]
 [FONT=Sans Serif]Reading package lists... Done[/FONT]
 [FONT=Sans Serif]Building dependency tree       [/FONT]
 [FONT=Sans Serif]Reading state information... Done[/FONT]
 [FONT=Sans Serif]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ LANG=C;sudo apt-get --fix-missing install[/FONT]
 [FONT=Sans Serif]Reading package lists... Done[/FONT]
 [FONT=Sans Serif]Building dependency tree       [/FONT]
 [FONT=Sans Serif]Reading state information... Done[/FONT]
 [FONT=Sans Serif]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$ [/FONT]
 p, li { white-space: pre-wrap; } [FONT=Sans Serif]muelux@muelux-LT6cA:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade[/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid Release.gpg[/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid Release.gpg                                                      [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid Release.gpg                                                     [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-updates Release.gpg                                             [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-security Release.gpg                                            [/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid Release                                       [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-backports Release.gpg                        [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid Release                                      [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-updates Release                                                 [/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid Release                                                          [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-security Release                                                [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-backports Release                                               [/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid/main Packages                                                    [/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid/main Sources                      [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid/main Packages                    [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid/universe Packages                [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid/restricted Packages              [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid/main Sources                     [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid/universe Sources[/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid/main Packages[/FONT]
 [FONT=Sans Serif]Hit http://ppa.launchpad.net lucid/main Sources                      [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-updates/main Packages            [/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-updates/universe Packages[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-updates/restricted Packages[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-updates/main Sources[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-updates/universe Sources[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-security/main Packages[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-security/universe Packages[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-security/restricted Packages[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-security/main Sources[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-security/universe Sources[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-backports/universe Packages[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-backports/main Packages[/FONT]
 [FONT=Sans Serif]Hit http://archive.ubuntu.com lucid-backports/restricted Packages[/FONT]
 [FONT=Sans Serif]Hit http://download.virtualbox.org lucid Release.gpg[/FONT]
 [FONT=Sans Serif]Hit http://download.virtualbox.org lucid Release[/FONT]
 [FONT=Sans Serif]Hit http://download.virtualbox.org lucid/contrib Packages[/FONT]
 [FONT=Sans Serif]Hit http://download.virtualbox.org lucid/non-free Packages[/FONT]
 [FONT=Sans Serif]Reading package lists... Done[/FONT]
 [FONT=Sans Serif]Reading package lists... Done[/FONT]
 [FONT=Sans Serif]Building dependency tree       [/FONT]
 [FONT=Sans Serif]Reading state information... Done[/FONT]
 [FONT=Sans Serif]Calculating upgrade... Done[/FONT]
 [FONT=Sans Serif]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
 [FONT=Sans Serif]muelux@muelux-LT6cA:~$[/FONT]



```

---

### Post by mue.de on 2011-09-27
Could someone please give me help for helping myself?

I'm still searching for the bug in my Lucid Lynx: The main problem is the error 'no contact to KDED' (KDE-daemon?); i can't use USB-Sticks under KDE, have to mount them by terminal, kmail forgets its certificates... (something wrong with DBUS?)

Where can i get on the trace of this bug?

P.S.:
Why are there still relicts from the old KDE3.5 on my system?
> [FONT=Sans Serif]muelux@muelux-LT6cA:/var/log$ [/FONT][FONT=Sans Serif]kded --version [/FONT]
 [FONT=Sans Serif]Qt: 3.3.8b[/FONT]
 [FONT=Sans Serif]KDE: 3.5.10[/FONT]
 [FONT=Sans Serif]KDE Daemon: $Id: kded.cpp 711061 2007-09-11 09:42:51Z tpatzig $[/FONT]
> 
  [FONT=Sans Serif]muelux@muelux-LT6cA:/$ [/FONT][FONT=Sans Serif]sudo qdbus[/FONT]
 [FONT=Sans Serif]:1.1[/FONT]
 [FONT=Sans Serif]org.freedesktop.DBus[/FONT]
How could i really clean up the system from old dependancies (the about 10 Kernel-Versions listed at GRUB2-Start) ?

Any help would by appreciated 

Just for the records:

Running the commands 

> 
sudo service apache2 stop
sudo service postfix stop

sudo apt-get update
sudo apt-get dist-upgrade 
 once more again (after stopping all Miniprogramms (systray) with apache2 and postfix) 
apt got a lot of updates, kernel-headers, firefox, firefox-branding, GRUB2-Updating it's list, generating a new initrd...

Now the qdbus has much more entries:

> muelux@muelux-LT6cA:/$ qdbus
:1.1
 org.kde.klauncher
:1.10
 org.kde.ActivityController-1693
:1.11
 org.freedesktop.Notifications
 org.kde.StatusNotifierHost-1719
 org.kde.plasma-desktop
:1.13
 org.kde.ActivityController-1719
:1.14
 org.kde.knotify
:1.16
 org.kde.JobViewServer
 org.kde.kuiserver
:1.18
 org.freedesktop.Akonadi.Control
 org.freedesktop.Akonadi.Control.lock
:1.19
 org.freedesktop.Akonadi
:1.20
:1.21
 org.freedesktop.Akonadi.Agent.akonadi_birthdays_resource_0
 org.freedesktop.Akonadi.Resource.akonadi_birthdays_resource_0
 org.kde.akonadi_birthdays_resource_0-1764
:1.22
 org.freedesktop.Akonadi.Agent.akonadi_kabc_resource_1
 org.freedesktop.Akonadi.Resource.akonadi_kabc_resource_1
 org.kde.KResourcesManager
 org.kde.akonadi_kabc_resource_1-1767
:1.23
 org.freedesktop.Akonadi.Agent.akonadi_ical_resource_0
 org.freedesktop.Akonadi.Resource.akonadi_ical_resource_0
 org.kde.akonadi_ical_resource_0-1766
:1.24
 org.freedesktop.Akonadi.Agent.akonadi_contacts_resource_2
 org.freedesktop.Akonadi.Resource.akonadi_contacts_resource_2
 org.kde.akonadi_contacts_resource_2-1765
:1.25
 org.freedesktop.Akonadi.Agent.akonadi_nepomuk_contact_feeder
 org.kde.akonadi_nepomuk_contact_feeder-1770
:1.26
 org.freedesktop.Akonadi.Agent.akonadi_nntp_resource_0
 org.freedesktop.Akonadi.Resource.akonadi_nntp_resource_0
 org.kde.akonadi_nntp_resource_0-1771
:1.27
 org.freedesktop.Akonadi.Agent.akonadi_vcard_resource_0
 org.freedesktop.Akonadi.Resource.akonadi_vcard_resource_0
 org.kde.akonadi_vcard_resource_0-1772
:1.28
 org.freedesktop.Akonadi.Agent.akonadi_maildir_resource_2
 org.freedesktop.Akonadi.Resource.akonadi_maildir_resource_2
 org.kde.akonadi_maildir_resource_2-1768
:1.29
 org.freedesktop.Akonadi.Agent.akonadi_maildispatcher_agent
 org.kde.akonadi_maildispatcher_agent-1769
:1.30
 org.kde.NepomukServer
:1.32
 org.kde.NepomukStorage
 org.kde.nepomuk.services.nepomukstorage
 org.kde.nepomukstorage-1795
:1.33
:1.34
 org.kde.kaccess
:1.40
 org.freedesktop.ScreenSaver
 org.kde.krunner
 org.kde.screensaver
:1.43
 org.kde.kmix
:1.45
 org.kde.policykit1-kde
:1.47
 org.kde.kbluetooth
:1.49
 org.kde.StatusNotifierItem-1830-1
:1.5
 org.kde.kglobalaccel
:1.50
 org.kde.kgpg
:1.52
:1.59
 org.kde.StatusNotifierItem-1835-1
:1.63
 org.kde.klipper
:1.65
 org.kde.korgac
:1.69
 org.kde.kwalletd
:1.71
 org.kde.knetworkmanager
 org.kde.networkmanagement
:1.73
 org.kde.StatusNotifierItem-1826-1
:1.74
 org.kde.StatusNotifierItem-1855-1
:1.75
 org.kde.StatusNotifierItem-1856-1
:1.76
 org.kde.StatusNotifierItem-1861-1
:1.77
 org.kde.printer-applet-1842
:1.78
 org.kde.StatusNotifierItem-1842-1
:1.79
 org.kde.nepomuk.services.nepomukqueryservice
 org.kde.nepomukqueryservice-1880
:1.8
 org.kde.ksmserver
 org.kde.ksmserver-1669
:1.80
 org.kde.nepomuk.services.nepomukontologyloader
 org.kde.nepomukontologyloader-1881
:1.81
 org.kde.nepomuk.services.nepomukfilewatch
 org.kde.nepomukfilewatch-1882
:1.82
 org.kde.digikamnepomukservice-1883
 org.kde.nepomuk.services.digikamnepomukservice
:1.83
 org.kde.nepomuk.services.nepomukremovablestorageservice
 org.kde.nepomukremovablestorageservice-1885
:1.84
 org.kde.nepomuk.services.nepomukactivitiesservice
 org.kde.nepomukactivitiesservice-1886
:1.85
 org.kde.kwalletmanager
:1.87
 org.kde.StatusNotifierItem-1888-1
:1.88
:1.89
 org.kde.dolphin
:1.9
 org.kde.kwin
 org.kde.kwin-1693
:1.91
:1.92
org.freedesktop.DBus


mue.de

---

