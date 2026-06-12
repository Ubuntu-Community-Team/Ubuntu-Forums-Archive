---
title: "Broken Packages...?"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by Koba on 2005-08-24
ok, i tryed that sudo apt-get install kubuntu-desktop and this was what i got:
> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
kubuntu-desktop: Depends: amarok but it is not going to be installed
E: Broken packages
so any ideas one what to do...? i have tryed sudo apt-get clean, i have tryed sudo apt-get -f install (i realize thats only for packages with missing dependancies...)

---

### Post by mapman on 2005-08-26
I think it may have something to do with not having all the proper repositories in your sources.list.  Check that you use the sources.list that is specified in [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/).  That may fix your broken package after an apt-get update.  I'm guessing amarok isn't in the default sources.list.

---

### Post by Dustin Wyatt on 2005-08-26
[QUOTE=Koba]ok, i tryed that sudo apt-get install kubuntu-desktop and this was what i got:

so any ideas one what to do...? i have tryed sudo apt-get clean, i have tryed sudo apt-get -f install (i realize thats only for packages with missing dependancies...)[/QUOTE]
 I'm getting the same exact same message after issuing sudo apt-get install kubuntu-desktop

```

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: amarok but it is not going to be installed

```

I tried wiping my sources.list and replacing it with the one from ubuntuguide.

I'd sure like to try out KDE :(

---

### Post by pebo on 2005-08-26
I've got the same problem trying to install kubuntu-desktop.
I've updated my sources.list and added 'universe' to all the current repositories - still no good.
Are there any other repositories not listed in ubuntuguide I should have?

---

### Post by pebo on 2005-08-26
ok, fixed it. :wink:  Changed my sources.list:



[https://wiki.ubuntu.com/PackageManagementHowTo?highlight=%28sources.list%29](https://wiki.ubuntu.com/PackageManagementHowTo?highlight=%28sources.list%29)

---

### Post by Dustin Wyatt on 2005-08-27
[QUOTE=pebo]ok, fixed it. :wink:  Changed my sources.list:



[https://wiki.ubuntu.com/PackageManagementHowTo?highlight=%28sources.list%29](https://wiki.ubuntu.com/PackageManagementHowTo?highlight=%28sources.list%29)[/QUOTE]
 Ahh yes, this worked for me as well.  Seems odd that this is required and that no one other than us has experienced this issue (no results through a forum search).

---

### Post by Dustin Wyatt on 2005-08-27
Worked for me as well.  Thanks.

---

