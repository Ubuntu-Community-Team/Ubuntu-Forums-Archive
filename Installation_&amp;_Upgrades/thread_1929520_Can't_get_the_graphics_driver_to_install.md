---
title: "Can't get the graphics driver to install"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by HerFlower on 2012-02-22
Ok, I'm using Ubuntu 10.04 on a Toshiba Satellite M115-S1061. I've tried every way in the world to install the proprietary driver  with no luck. Does anyone know of a proper guide to install it? My video card is a ATI Radeon Xpress 200. 

Thanks!

---

### Post by aura7 on 2012-02-22
Download from the last link on this page
 
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.7&product=2.7.5.3.4.3.1&contentType=Tech+Download+Chipset+Motherboard&ostype=&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.7&product=2.7.5.3.4.3.1&contentType=Tech+Download+Chipset+Motherboard&ostype=&keywords=&items=20)

---

### Post by HerFlower on 2012-02-22
Awesome. Thank you. I guess my lack of sleep is getting to me and keeping me from searching properly, lol.

---

### Post by winh8r on 2012-02-22
You may have problems due to components of the fglrx package being left in the filesystem there is a guide here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch")

which shows how to purge the fglrx from the system and install the other driver.

Hope this is of some help.

---

### Post by HerFlower on 2012-02-22
Hmm... ran into a problem.


```
Generating package: Ubuntu/lucid
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Removing temporary directory: fglrx-install.9jZhMe

```

---

### Post by Mark Phelps on 2012-02-23
The reason you're getting that error is that there are NO proprietary drivers that will work with your video card and Ubuntu versions newer than 8.10.

Had the person who told you to install such drivers bothered to do a little research, they would have discovered this and NOT given you bad advice.

The ONLY drivers that will work with your card and recent Ubuntu versions are the default open-source Radeon drivers -- and those are installed by default during Ubuntu setup.

So, if you are seeing a graphical desktop, those drivers are installed -- and there are no other drivers you can use.

---

