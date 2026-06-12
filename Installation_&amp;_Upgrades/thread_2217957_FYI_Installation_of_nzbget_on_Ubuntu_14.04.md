---
title: "FYI: Installation of nzbget on Ubuntu 14.04"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by sanderj on 2014-04-19
Ubuntu 14.04 has version 12.0 of nzbget (a light-weight NZB downloader with a beautifull webGUI built in) in it's repositories, and I find that good news.

Here's a short howto how to install nzbget 12.0:

Install
```
sudo apt-get install nzbget
```

Install basic configuration file
```
zcat /usr/share/doc/nzbget/examples/nzbget.conf.gz > ~/.nzbget
```

Run
```
nzbget -s
```

Then, in your webbrowser, go to [http://localhost:6789/nzbget:tegbzn6789/](http://localhost:6789/nzbget:tegbzn6789/) and you should get the NZBget web interface. Go to Settings -> NEWS-SERVERS to set up one or more newsservers.

About the nzbget config file: if you don't specify the location, nzbget will look here:

```
~/.nzbget
/etc/nzbget.conf
/usr/etc/nzbget.conf
/usr/local/etc/nzbget.conf
/opt/etc/nzbget.conf
```

HTH

---

### Post by Nathan_Deamer on 2014-06-03
Thanks.

For anyone that is running it on a separate machine (e.g. Ubuntu server like me). 
1. Move the config file to /etc/nzbget.conf. 
2. Edit the ControlIP in /etc/nzbget.conf to  ControlIP=0.0.0.0
3. sudo service nzbgetd start

---

### Post by smeerbartje on 2014-12-01
If I want to upgrade the version used in Ubuntu 14.04.1, what steps do I have to take? The latest version available is nzbget 12.something. It would be great is we can upgrade this to the latest version of nzbget, right?

---

