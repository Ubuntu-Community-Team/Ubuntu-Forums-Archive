---
title: "error while installing nagios plugin"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by nrmurali on 2012-11-26
i am installing nagios in Ubuntu 10.04 32 bit, package is installed correctly but when trying to install plugins i got the below error message and unable to install nagios plugin

**"E: Couldn't find package nagios-plugins-1.4.15"**

any body please suggest.

thanks,
murali

---

### Post by psyllex on 2012-12-31
try a search on your plugins to make sure you have the correct version number try:
```
sudo apt-cache search nagio-plugins-<version number>
```

you'll probably get a huge list just pick the one that looks the most proper and then try installing again.

---

### Post by ibjsb4 on 2013-01-01
How did you try to install it?  Im not finding the 1.4.15 package for Lucid, I am finding a 1.4.14 package.

The terminal command for installing it:

```
sudo apt-get install nagios-plugins
```If you want extras:

```
sudo apt-get install nagios-plugins-extra
```An excellent way to check for package versions is Synaptic Package Manager.

[ATTACH]229439[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en")

```
sudo apt-get install synaptic
```

For those who do not have it installed  :)

---

