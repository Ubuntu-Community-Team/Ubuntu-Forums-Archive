---
title: "deskbar-applet unmet dependencies"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by thebinz on 2007-11-07
Deskbar-applet has been held back from upgrading for the past week. I finally took some time out to take a look at it.

The results i get from trying to upgrade deskbar-applet are: 
> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  deskbar-applet: Depends: libebook1.2-9 (>= 1.12.1) but 1.12.0-0ubuntu5 is to be installed
                  Depends: libedataserver1.2-9 (>= 1.12.1) but 1.12.0-0ubuntu5 is to be installed
E: Broken packages


I currently have libebook1.2-9 and libedataserver1.2-9 installed on the system. I am not sure if I understand what it means when it says "1.12.0-0ubuntu5 is to be installed"

I have tried reinstalling both packages but it does not fix the issue.

If i try to uninstall the packages then important packages will be uninstall. ie. nautilus, gnome-panel, etc.

Does anyone know what i can do to get the deskbar-applet install through synaptic?

---

### Post by zvacet on 2007-11-08
**synaptic>edit>fix broken packages**

---

### Post by thebinz on 2007-11-08
Nothing happens when i click **Fix Broken Packages**. 
Apparently i don't have broken packages on my system. 

I Uninstalled the Deskbar-applet. When i try to install deskbar-applet I still get the unmet dependencies error.
> The following packages have unmet dependencies:
  deskbar-applet: Depends: libebook1.2-9 (>= 1.12.1) but 1.12.0-0ubuntu5 is to be installed
                  Depends: libedataserver1.2-9 (>= 1.12.1) but 1.12.0-0ubuntu5 is to be installed
E: Broken packages


So i don't know what to do.

 Any other suggestions?

---

### Post by zvacet on 2007-11-09
Maybe you can try 

```
sudo apt-get autoclean
```

This command will delete all old packages from your var/cache/apt/archives.That way you will have only latest version of packages and maybe this is the way to solve your problem.

---

