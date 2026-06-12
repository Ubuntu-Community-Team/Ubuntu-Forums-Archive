---
title: "Fixing upgrade from 9.04 to 9.10, openoffice and aptitude issue"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by Aereal on 2009-11-16
This is a _**temporal**_ fix for the upgrade failure from Jaunty (9.04) to Karmic (9.10).

If you were doing the upgrade and had to interrupt the installation of openoffice because it hanged out, you're in the right place.

Here is my output:

```
Could not install '/var/cache/apt/archives/openoffice.org-emailmerge_1%3a3.1.1-5ubuntu1_all.deb'

The upgrade will continue but the '/var/cache/apt/archives/openoffice.org-emailmerge_1%3a3.1.1-5ubuntu1_all.deb' package may not be in a working state. Please consider submitting a bug report about it.

Could not install '/var/cache/apt/archives/openoffice.org-writer2latex_0.5.0.2-4ubuntu1_all.deb'

The upgrade will continue but the '/var/cache/apt/archives/openoffice.org-writer2latex_0.5.0.2-4ubuntu1_all.deb' package may not be in a working state. Please consider submitting a bug report about it.

Could not install '/var/cache/apt/archives/ure_1.5.1+OOo3.1.1-5ubuntu1_amd64.deb'

The upgrade will continue but the '/var/cache/apt/archives/ure_1.5.1+OOo3.1.1-5ubuntu1_amd64.deb' package may not be in a working state. Please consider submitting a bug report about it.

Could not install 'ure'

The upgrade will continue but the 'ure' package may not be in a working state. Please consider submitting a bug report about it.

Could not install '/var/cache/apt/archives/openoffice.org-filter-binfilter_1%3a3.1.1-5ubuntu1_amd64.deb'

The upgrade will continue but the '/var/cache/apt/archives/openoffice.org-filter-binfilter_1%3a3.1.1-5ubuntu1_amd64.deb' package may not be in a working state. Please consider submitting a bug report about it.

Could not install 'openoffice.org-emailmerge'

The upgrade will continue but the 'openoffice.org-emailmerge' package may not be in a working state. Please consider submitting a bug report about it.


Could not install 'openoffice.org-writer2latex'

The upgrade will continue but the 'openoffice.org-writer2latex' package may not be in a working state. Please consider submitting a bug report about it.

Could not install 'openoffice.org-filter-binfilter'

The upgrade will continue but the 'openoffice.org-filter-binfilter' package may not be in a working state. Please consider submitting a bug report about it.
```Then it finished, so I booted, tried to enter with the new kernel but there it was that blinking console, so I went on irssi (you can just go back to the previous kernel), asked for the last nvidia driver, downloaded, installed it, configured the audio, and there I was, happy, until I tried to finish installing the missing updates!

So I did sudo aptitude safe-upgrade -f, and it hang out again removing openoffice.org-writer2latex. I tried ALMOST EVERYTHING, purges (dpkg -P), aptitude clean, fix install, etc, and the only way I could made "move on" the aptitude was commenting the entire code of this file: /usr/lib/openoffice/program/unopkg. After doing it, I ran an aptitude update and an aptitude safe-upgrade for a secommand time, but it got stuck again! and that was because unopkg was replaced, so I commented it again... runned the update+upgrade for a third time! Everything was fine until the set up of openoffice.org-filter-binfilter got stuck, and there I dunno wat to do.

Now if I try to download something using aptitude it tries to finish setting up openoffice.org-filter-binfilter, and It won't.

```
irakirashia@mfsec:~$ sudo apt-get install fakeroot (Example)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fakeroot is already the newest version.
fakeroot set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up openoffice.org-filter-binfilter (1:3.1.1-5ubuntu1) ...
^Cdpkg: error processing openoffice.org-filter-binfilter (--configure):
 subprocess installed post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 openoffice.org-filter-binfilter
E: Sub-process /usr/bin/dpkg returned an error code (1) (I interrupted)
```So, my idea was to set it up manually right? why not? I did some google search looking for a .deb file of openoffice.org-filter-binfilter but I just found .rpms, also tried to use alien to convert them into .debs but something new appeared

```
irakirashia@mfsec:~$ fakeroot alien -i Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm 
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
error: incorrect format: unknown tag
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
Unpacking of 'Downloads/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 155.
```Here's the rpm I downloaded
```
http://mandriva.c3sl.ufpr.br/devel/2010.0/x86_64/media/main/release/openoffice.org-filter-binfilter-3.1.1-2mdv2010.0.x86_64.rpm

```Info
```
irakirashia@mfsec:~/Downloads$ uname -a
Linux mfsec 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```By the way, apologise my english, i'm from Argentina and spent so many hours trying to fix this, hope to see any response soon, I'm actually a guy who does not want to give up (format to reinstall, that for WindowZ users :P, that's why we are here, right?).

Edit: I keep finding people with same issues
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1837551.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1837551.html)
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/478044](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/478044)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1865913.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1865913.html)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1865913.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1865913.html)
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/441005](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/441005)

Found my old thread about this issue [http://ubuntuforums.org/showthread.php?p=8324724](http://ubuntuforums.org/showthread.php?p=8324724)

Google for more [http://www.google.com.ar/search?hl=es&safe=off&client=firefox-a&channel=s&rls=org.mozilla%3Aes-AR%3Aofficial&hs=m5K&q=%22openoffice.org%22+9.10+upgrade&btnG=Buscar&meta=&aq=f&oq=](http://www.google.com.ar/search?hl=es&safe=off&client=firefox-a&channel=s&rls=org.mozilla%3Aes-AR%3Aofficial&hs=m5K&q=%22openoffice.org%22+9.10+upgrade&btnG=Buscar&meta=&aq=f&oq=)

---

### Post by Aereal on 2009-11-16
Ok, just downloaded the .deb [http://packages.ubuntu.com/karmic/misc/openoffice.org-filter-binfilter](http://packages.ubuntu.com/karmic/misc/openoffice.org-filter-binfilter)

I installed it and didn't work, so... there's no fix for this? Shame.

Found some people at the forum with same issue I think:

[http://ubuntuforums.org/showthread.php?p=8334497](http://ubuntuforums.org/showthread.php?p=8334497)

[http://ubuntuforums.org/showthread.php?p=8334488](http://ubuntuforums.org/showthread.php?p=8334488)

Edit: Aptitude is working fine doing all this, just that package is annoying me, but I'm trying to figure it out with jrib help on irc.

---

