---
title: "Upgrading GIMP from 2.6 to 2.8"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by coloreporter on 2012-09-01
I've found a few sources that say to do the following to update GIMP to 2.8:


[INDENT]1.Delete Gimp
sudo apt-get autoremove gimp gimp-plugin-registry
2.Add the following PPA
sudo add-apt-repository ppa:otto-kesselgulasch/gimp sudo apt-get update
3.Install Gimp
sudo apt-get install gimp 

[/INDENT]This hasn't worked for me.  I don't seem to be getting an error, but when I open GIMP it's still version 2.6.  Does anyone know how I can get version 2.8?

Thanks.

---

### Post by zvacet on 2012-09-02
Read [this]("http://ubuntuforums.org/showpost.php?p=11912447&postcount=20") and see is it of any help to you.

---

### Post by coloreporter on 2012-09-03
> **zvacet said:**
> Read [this]("http://ubuntuforums.org/showpost.php?p=11912447&postcount=20") and see is it of any help to you.
That did it!  Thank you.

---

### Post by aquarius18 on 2012-09-14
> **zvacet said:**
> Read [this]("http://ubuntuforums.org/showpost.php?p=11912447&postcount=20") and see is it of any help to you.

Tried this in 11.10 Oneiric - to no avail (not ready for an upgrade to 12.04 Pangolin)

Any ideas please?

Thanks

---

### Post by aquarius18 on 2012-09-14
> **aquarius18 said:**
> Tried this in 11.10 Oneiric - to no avail (not ready for an upgrade to 12.04 Pangolin)

Any ideas please?

Thanks

Got around it by removing Gimp 2.6 and then installing 2.8 from **[Noobslab]("http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html")** (scroll down to the bottom half of the page)

---

### Post by aquarius18 on 2012-09-15
> **aquarius18 said:**
> Got around it by removing Gimp 2.6 and then installing 2.8 from **[Noobslab]("http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html")** (scroll down to the bottom half of the page)

Might add that Gimp is working A1, only hiccup was that xsane had been removed during the installation process. That was fixed easily by re-installing xsane.

---

