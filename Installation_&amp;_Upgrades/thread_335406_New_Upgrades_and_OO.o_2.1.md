---
title: "New Upgrades and OO.o 2.1"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by Abaddon on 2007-01-10
Hi All,

I got the little security update icon in my taskbar, so I clicked on it, and it told me that I wouldn't be able to upgrade fully unless I did a dist-upgrade.  Clicking on that gave me an error about not having ubuntu-desktop installed.

I had to uninstall ubuntu-desktop, because I've installed the Openoffice 2.1 upgrade, which conflicts with ubuntu-desktop, which in turn requires the OO 2.0 packages.

Any suggestions on a work around (without uninstalling OO 2.1 and reinstalling it after!)

Cheers,

---

### Post by bapoumba on 2007-01-10
I'm interested in the answer too ;)

From what I understand, ubuntu-desktop is a meta-package used by Ubuntu distributions to ensure all packages are tied up via dependencies,  and that all version numbers or release are compatible.

I read a lot on this forum that it is safe to remove ubuntu-desktop. I partially agree, as this will not break the system, and installing packages with higher version numbers than the ones you can get in a particular ubuntu release is quite easy. Now, ubuntu-desktop is essential to dist-upgrades, and this I why I think is it not that safe to recommend to remove it.
Am I wrong ?

For your OOo problem now, what is the complete output to **sudo apt-get dist-upgrade **or **sudo aptitude dist-upgrade** (aptitude may give you more infos). Cancel the dist-upgrade, do not answer "yes", just paste the error messages, along with **cat /etc/apt/sources.list**.

---

### Post by Hagar Delest on 2007-01-11
I think we cannot avoid the reinstall of the OOo packages bundled with the distro before upgrading. That's the problem with such meta-packages and distros that are designed to be used as it is with the standard softs.

---

### Post by Abaddon on 2007-01-13
Well, I decided to go and uninstall the OO.o 2.1 packages - coming across [another inconvenience]("http://www.ubuntuforums.org/showthread.php?p=2006638") along the way.

Got 2.1 uninstalled no worries, re-installed 2.04 and ubuntu-desktop, and then ran the dist-upgrade... too easy...

Until it came time to reinstall 2.1   Now 2.04 has a death-grip on my packages and doesn't seem to want to go anywhere.

```
 sudo aptitude purge openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.orgl10n-en-us openoffice.org-math openoffice.org-style-default openoffice.org-style-industrial openoffice.org-thesaurus-en-us openoffice.org-writer ubuntu-desktop

```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "openoffice.orgl10n-en-us"
The following packages are BROKEN:
  language-support-en openoffice.org-l10n-en-za python-uno 
The following packages will be REMOVED:
  openoffice.org{p} openoffice.org-base{p} openoffice.org-calc{p} openoffice.org-common{p} openoffice.org-core{p} openoffice.org-draw{p} 
  openoffice.org-evolution{p} openoffice.org-gnome{p} openoffice.org-gtk{p} openoffice.org-help-en-gb{p} openoffice.org-help-en-us{p} 
  openoffice.org-impress{p} openoffice.org-java-common{p} openoffice.org-l10n-common{p} openoffice.org-l10n-en-gb{p} openoffice.org-math{p} 
  openoffice.org-style-default{p} openoffice.org-style-industrial{p} openoffice.org-thesaurus-en-us{p} openoffice.org-writer{p} ubuntu-desktop{p} 
0 packages upgraded, 0 newly installed, 21 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 281MB will be freed.
The following packages have unmet dependencies:
  language-support-en: Depends: openoffice.org-help-en-us but it is not installable or
                                openoffice.org2-help-en-us which is a virtual package.
                       Depends: openoffice.org-l10n-en-gb but it is not installable or
                                openoffice.org2-l10n-en-gb which is a virtual package.
                       Depends: openoffice.org-thesaurus-en-us but it is not installable
  python-uno: Depends: openoffice.org-core (= 2.0.4-0ubuntu4) but it is not installable
  openoffice.org-l10n-en-za: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
openoffice.org-common [2.0.4-0ubuntu4 (edgy-updates, now)]
openoffice.org-core [2.0.4-0ubuntu4 (edgy-updates, now)]
openoffice.org-help-en-us [2.0.4-0ubuntu1 (edgy, now)]
openoffice.org-java-common [2.0.4-0ubuntu4 (edgy-updates, now)]
openoffice.org-l10n-common [2.0.4-0ubuntu1 (edgy, now)]
openoffice.org-l10n-en-gb [2.0.4-0ubuntu1 (edgy, now)]
openoffice.org-style-default [2.0.4-0ubuntu4 (edgy-updates, now)]
openoffice.org-style-industrial [2.0.4-0ubuntu4 (edgy-updates, now)]
openoffice.org-thesaurus-en-us [1:2.0.3-2ubuntu1 (edgy, now)]
openoffice.org-writer [2.0.4-0ubuntu4 (edgy-updates, now)]

Leave the following dependencies unresolved:
openclipart-openoffice.org recommends openoffice.org | openoffice.org2
Score is -640

Accept this solution? [Y/n/q/?] 

```

And many other solutions that involve downgrading instead of purging.

What to do?

---

### Post by Hagar Delest on 2007-01-13
I've had this kind of problem also the first time I uninstalled the Ubuntu OOo packages. I fixed it by removing the packages nearly one by one in Synaptic. I had to finish with the localization ones if I remember well.

---

### Post by be4truth on 2007-01-21
try this one for dapper.
[http://bodmas.org/blog/?p=523](http://bodmas.org/blog/?p=523)
works fine with me!

---

