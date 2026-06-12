---
title: "Downloading Packages from a website"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by LonelyTraveler on 2008-01-14
Hi,

It's been a few months since I last used Linux, because of our limited internet connections here in South Africa. I installed Ubuntu on my old Laptop and that laptop is not online yet. I will set up a Wi-Fi link to my other laptop sometime so I can share that one's internet connection. I want to download packages from work (so I don't have to pay for it) and then install it at home off my flash drive. Is it possible to download packages (such as w32codecs) from a website and not via the sources.list?

Thanks...

---

### Post by dgray_from_dc on 2008-01-14
Yes.  You can download packages and install them at home.  Once you have the .deb file on your home machine, right click on it and use the appropriate package manager (kpackage or gdebi I think).  However, you have to be mindful of dependencies.   You'll need to download all of the dependencies for any application you want to install.

---

