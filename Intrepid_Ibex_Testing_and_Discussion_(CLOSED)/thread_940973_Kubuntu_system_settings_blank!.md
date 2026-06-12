---
title: "Kubuntu system settings blank!"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by David Gerard on 2008-10-07
Laptop: HP Compaq 6710b. Ran Gutsy okay, ran Hardy fabulously well, installed KDE 4.1 from ppa-launchpad, did dist-upgrade to Intrepid.

I start System Settings and ... it's blank! I get a blank window. That's all.

Deleted .kde and .kde4 for a freshish start. Still happens.

1. Has anyone else seen this?
2. Is there a way to start each system settings module? I really don't like the default window dressings ...

---

### Post by Beatinu on 2008-10-26
Same here for me. The "old" system settings program from my kde4 test installation caused this. The solution is to simply install the current systemsettings package ("apt-get install systemsettings").

BTW shouldn't there be a dependency which installs the current systemsettings package even if the systemsettings-kde4 package is installed? This may cause problems for everyone who tried the kde4 packages in hardy.

---

### Post by David Gerard on 2008-10-26
> **Beatinu said:**
> Same here for me. The "old" system settings program from my kde4 test installation caused this. The solution is to simply install the current systemsettings package ("apt-get install systemsettings").

Yep! It removed systemsettings-kde4, which I had installed in Hardy, and replaced it with systemsettings.

AND IT WORKS!!

> **Beatinu said:**
> BTW shouldn't there be a dependency which installs the current systemsettings package even if the systemsettings-kde4 package is installed? This may cause problems for everyone who tried the kde4 packages in hardy.

Heck yes. Please report this as a bug ASAP before the final ISOs are gold mastered. Or I will. Or both of us can.

**Edit:** Reported as [bug 289611]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/289611").

**Edit 2:** The helpful souls at Launchpad closed it "WONTFIX" for being reported in the wrong package. Rereported as [bug 289630](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/289630).

---

### Post by claydoh on 2008-10-26
> **Beatinu said:**
> 
BTW shouldn't there be a dependency which installs the current systemsettings package even if the systemsettings-kde4 package is installed? This may cause problems for everyone who tried the kde4 packages in hardy.

The package kubuntu-desktop does just that. Do you have that installed?

---

### Post by David Gerard on 2008-10-26
> **claydoh said:**
> The package kubuntu-desktop does just that. Do you have that installed?

[FONT="Courier New"]fun@heidi:~$ sudo apt-get install kubuntu-desktop
[sudo] password for fun:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  adept kdm kmail konqueror-plugin-searchbar ktimetracker libkpgp4 libksieve4
  libmimelib4 libqca2-plugin-ossl mediamanager strigi-client
  update-manager-kde update-notifier-kde
Suggested packages:
  procmail clamav f-prot-installer
The following packages will be REMOVED
  adept-common karm kdm-kde4
The following NEW packages will be installed
  adept kdm kmail konqueror-plugin-searchbar ktimetracker kubuntu-desktop
  libkpgp4 libksieve4 libmimelib4 libqca2-plugin-ossl mediamanager
  strigi-client update-manager-kde update-notifier-kde
0 upgraded, 14 newly installed, 3 to remove and 12 not upgraded.
Need to get 5649kB of archives.
After this operation, 12.9MB of additional disk space will be used.
Do you want to continue [Y/n]?
[/FONT]

WHAT THE S**T. No, I did not.

Considering I did a dist-upgrade from hardy to intrepid, I darn well SHOULD have had it. What the?

---

### Post by xerosis on 2008-10-26
It wasn't closed as WONTFIX because it was the wrong package, but because that's what kubuntu-desktop is for. It's installed in Hardy and it's installed in Intrepid so you must have removed it at some point, perhaps as a by-product of using the PPAs (which aren't officially supported are they?).

---

### Post by claydoh on 2008-10-26
I agree  that somewhere in hardy kubuntu-desktop was removed when you uninstalled something that it depended on, such as kmail or something (which is normal actually)

I think it needs to be mentioned in the release notes or in any upgrade how-to, that (K)(X)Ubuntu-desktop is needed before any upgrade, to make sure all  the necessary packages are installed.

---

### Post by David Gerard on 2008-10-26
> **claydoh said:**
> I agree  that somewhere in hardy kubuntu-desktop was removed when you uninstalled something that it depended on, such as kmail or something (which is normal actually)

I think it needs to be mentioned in the release notes or in any upgrade how-to, that (K)(X)Ubuntu-desktop is needed before any upgrade, to make sure all  the necessary packages are installed.

Yeah. My originally-submitted bug has been reopened pointing this out as the actual problem.

---

