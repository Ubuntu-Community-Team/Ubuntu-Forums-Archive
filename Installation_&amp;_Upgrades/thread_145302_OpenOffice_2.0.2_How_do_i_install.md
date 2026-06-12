---
title: "OpenOffice 2.0.2 How do i install?"
date: 2006-03-16
forum: Installation &amp; Upgrades
---

### Post by risknothin on 2006-03-16
I new and i really want to figure out how to install it.

Thanks for any help.

---

### Post by ziplux on 2006-03-16
You probably want to do the following:

Go to System -> Administration -> Synaptic Package Manager


Search for openoffice in the package manager.  Double click the package, then click Apply to install it.

---

### Post by ziplux on 2006-03-16
Ah, on second thought, it looks like you want to upgrade your version of OO.org to 2.0.2.  Your best bet is probably to download it from the OO.org site, but I'm not too sure of that.

---

### Post by funkydan2 on 2006-03-16
Upgrade to the development version of Ubuntu - Dapper Drake.  However it is still under development and may break (i.e. not great for a new linux user).  Is there any really good reason why the version is Breezy (2.0 RC2) isn't working for you?

---

### Post by fparri on 2006-03-16
For me it would be this one ;)

[http://secunia.com/advisories/19261/]("http://secunia.com/advisories/19261/")

---

### Post by towsonu2003 on 2006-03-16
> **fparri]For me it would be this one  said:**
> http://secunia.com/advisories/19261/[/URL]
file a bug report in malone (ubuntu) so they patch the existing version. 

and 2.0.1 is available tru a custom repository. search the forum for "openoffice update doku" (I don't remember the repo off hand).

---

### Post by matthewv on 2006-03-18
I installed openoffice 2 on breezy by downloading the official package from the openoffice site. Then extract the file to a convenient location. From commandline, change into the rpm subdirectory of the folder you extracted openoffice to then
```

sudo apt-get install alien
sudo alien *.rpm

```
not sure if alien will install the .deb packages it created, if not run a ```
sudo dpkg -i *.deb
```

---

