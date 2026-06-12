---
title: "Refresh/Restore current installation without FULL reinstallation"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by padfootpak on 2011-04-07
Hi, I installed Ubuntu Lucid Lynx a while ago. but then upgraded it to 10.10 

I don't have the CD with me right now and i need to fix some mistakes of mine (being a n00b to ubuntu) urgently i.e. i can't wait for morning. Is there anyway i can rollback to the time when my ubuntu installation was in mint condition?


One more thing. Let me tell you my mistake. Almost a month ago i installed Apache2 on my Laptop (for LAMP). and now i have to install Apache Tomcat for JSP development. but the problem is that the files made by Apache2 and the PHP5 installation i made are not removed with

```
sudo apt-get remove apache2
```
```
sudo apt-get remove php5
```

so now the apache2 files are superseding the Apache Tomcat. hence i cannot distuinguish between apache2 or apache tomcat when i goto:

```
127.0.0.1
```

So if anyone has a way of ridding my laptop of this disease without complete overhaul, please post your replies here.

Until then, I will have to defect back to Windows :(

---

### Post by mörgæs on 2011-04-07
> **padfootpak said:**
> Is there anyway i can rollback to the time when my ubuntu installation was in mint condition?


No, unfortunately. In Synaptic you can see your history of packages being added and removed, but there is no record of what has been written to the configuration files.

---

