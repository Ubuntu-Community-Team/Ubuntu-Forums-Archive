---
title: "Can't find python-hulahop in 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by R3N3G4D3 on 2010-05-01
I upgraded to 10.04 and noticed that python-hulahop package is nowhere to be found. This package used to be available in previous versions, and according to google it was supposed to be available in 10.04 too until recently:
[http://packages.ubuntu.com/lucid/i386/python-hulahop](http://packages.ubuntu.com/lucid/i386/python-hulahop) (this is the actual page that claims the link is erroneous)
[http://webcache.googleusercontent.com/search?q=cache:tdcWKNIDCxMJ:packages.ubuntu.com/lucid/i386/python-hulahop+lucid+hulahop&cd=1&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:tdcWKNIDCxMJ:packages.ubuntu.com/lucid/i386/python-hulahop+lucid+hulahop&cd=1&hl=en&ct=clnk&gl=us) (this is google cache for the same link that shows the package for lucid)

I'm trying to run Pyjamas Desktop, which requests the hulahop module (in 9.10, the precompiled python-hulahop did not work, but self-compiled version did. Now in 10.04 I can't find the source to compile the package myself either). Did it get replaced? Did it get included into another package?

Thanks

---

### Post by zarthon on 2010-08-29
bump

---

### Post by gregghb on 2011-06-25
I'm using Kubuntu 10.04 and this is how I installed python-hulahop to get pyjamas-desktop running.

System Settings -> Add and Remove Software -> Settings -> Edit Software Sources
Unchecked all boxes under the tabs Kubuntu Software and Other Software
(Remember what they were so that you can reactivate them afterwards)
Under Other Software click Add
Enter: deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main
Click OK
Click Close
Click Reload
Now you should be able to install python-hulahop either through Software Management or sudo apt-get install python-hulahop
After it's installed be sure to reset your Software Sources

---

