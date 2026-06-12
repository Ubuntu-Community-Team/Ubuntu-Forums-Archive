---
title: "Ubuntu Ultimate Edition 1.4 CD upgrade."
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by Geoformality on 2007-08-29
I burned and installed the Ubuntu Ultimate Edition 1.4, on CD because I don't have a DVD burner. It installed great, and I figured I could use the CD to get all the stuff that I would've gotten on the DVD after installation. Well, it became even easier with an Update script I could use. But it doesn't work. All I get is a page of errors all of which are 
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by jeremyphares on 2007-08-30
try trying sudo before the script your trying to run. it looks like you just need to run it with root privileges
if that doesnt work let make sure you dont have update manager, synaptic, apt-get, etc running when you run the script

---

