---
title: "canceling download in synamptic package manager caused problem"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by 24dhruv on 2008-11-12
i have serched ubuntustudio in synaptic and tired of my slow connection i cancelled the download but some of the packages are downloaded there properly so it tried to install them and then show errors.and after when i reboot i found another entry in my grub loader like this:

ubuntu 8.04. kernal 2.6.24-21-rt
ubuntu 8.04. kernal 2.6.24-21-rt(recovery mode)
ubuntu 8.04. kernal 2.6.24-21-generic
ubuntu 8.04. kernal 2.6.24-21-generic(recovery mode)
..........................
other os.........(vista)

like this it has double entry. when i go to the entry -rt once it shows 

b43-phy0 ERROR:firmware file "b43/4code13.fw" not found or load failed.

then i tried recovery mode found nothing and wen i again goes to the first entry (mind that second entry(generic) works properly leaving not using my nvidia graphics driver)it showed this error

Failed to start X Server(Your Graphical Interface)it is likely that it is not setup correctly.would like to view the x server output to diagnose the problem? next text i forget to write down

what can i do to remove this another entry?

---

