---
title: "how to install gerix"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by valleron2009 on 2013-01-31
i downloaded a zip from tiger security with gerix.extracted it but dont know how to install it.help please im a noob here.the folder is on my desktop.

---

### Post by slickymaster on 2013-01-31
Here's a couple of links that might help you getting started:

[Gerix for Ubuntu]("http://top-hat-sec.com/forum/index.php?topic=599.0")
[Installing Gerix on Ubuntu/Mint from Backtrack’s repository]("http://lulzroflz.weebly.com/4/post/2012/04/installing-gerix-on-ubuntu-mint-from-backtracks-repository.html")
[Install Gerix Wifi Crackrer Ubuntu]("http://xtrabuntu.blogspot.pt/2011/01/install-gerix-wifi-crackrer-ubuntu.html")
[How to install gerix on ubuntu]("http://askubuntu.com/questions/130497/how-to-install-gerix-on-ubuntu-12-04-using-backtrack-repositories")

---

### Post by valleron2009 on 2013-01-31
> **slickymaster said:**
> Here's a couple of links that might help you getting started:

[Gerix for Ubuntu]("http://top-hat-sec.com/forum/index.php?topic=599.0")
[Installing Gerix on Ubuntu/Mint from Backtrack&#8217;s repository]("http://lulzroflz.weebly.com/4/post/2012/04/installing-gerix-on-ubuntu-mint-from-backtracks-repository.html")
[Install Gerix Wifi Crackrer Ubuntu]("http://xtrabuntu.blogspot.pt/2011/01/install-gerix-wifi-crackrer-ubuntu.html")
[How to install gerix on ubuntu]("http://askubuntu.com/questions/130497/how-to-install-gerix-on-ubuntu-12-04-using-backtrack-repositories")



i already checked that.im getting an error that system needs qt3-python installed.i downloaded the tar.gz python qt3 ,extracted but dont know how to install it.its on my desktop.

---

### Post by slickymaster on 2013-01-31
You must be aware that it's not advisable to download and install applications from internet files.
Most applications for Ubuntu are available through the Software Center or using a package manager like [aptitude]("http://packages.ubuntu.com/hardy/aptitude") or [synaptic]("http://packages.ubuntu.com/hardy/synaptic") to download and install packages. Installing from the Software Center is much more secure, much easier, and will allow the app to get updates from Ubuntu.

That said,  regarding what you ask the answer is that you cannot install a .**tar.gz** because these files are gzip-compressed tarballs.
What you can do is to open a terminal window and navigate to the folder where you have your **.tar.gz** file and extract it by running the following commands:
```
tar xvzf PACKAGENAME.tar.gz
```
Then:
```
./configure
make
make install
```

---

### Post by oldos2er on 2013-01-31
Thread closed. We do not support wifi cracking here: "Material that suggests illegal activity or contains illegal content is also forbidden."

---

