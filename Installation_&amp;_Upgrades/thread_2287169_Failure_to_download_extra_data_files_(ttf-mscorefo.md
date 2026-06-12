---
title: "Failure to download extra data files (ttf-mscorefonts-installer)"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by Ricial on 2015-07-17
[IMG]http://i.imgur.com/grjVWQQ.png[/IMG]

I keep on getting this error when installing [B]ttf-mscorefonts-installer

NOTE: 
 [/B]
[LIST]
[*]I have already tried the the solution suggested in here ([http://askubuntu.com/questions/525865/failure-to-download-extra-data-files-flashplugin-installer](http://askubuntu.com/questions/525865/failure-to-download-extra-data-files-flashplugin-installer)).
[*]This is a FRESH install and I have not added any PPA or whatsoever prior to this issue. 
[*]The package **(ttf-mscorefonts-installer)** is present on Synaptics and I already tried re-installation and still error pops-up. 
[*]I already tried changing the server download location to my Country to Main server. 
[*]I am not using any custom firewall setup, proxy server and VPN. 
[*]I have a stable Internet connection. (Tried both *wired* and *wireless* connection) 
[/LIST]

---

### Post by slickymaster on 2015-07-17
Please try the following in a terminal window, one command at a time```
sudo dpkg -P ttf-mscorefonts-installer  
sudo apt-get install ttf-mscorefonts-installer  
```
Use the Tab and Enter keys to accept the EULA in the Microsoft TrueType core fonts window that pops up.

---

### Post by Ricial on 2015-07-17
I just solved the problem by following the **Solution 2: **([http://askubuntu.com/questions/153928/failure-to-download-extra-data-files-after-installing-ttf-mscorefonts-installe](http://askubuntu.com/questions/153928/failure-to-download-extra-data-files-after-installing-ttf-mscorefonts-installe))

Thanks!

---

### Post by Ricial on 2015-07-17
Hmmm. Just wondering why all the downloaded fonts was gone after performing the ```
 sudo dpkg-reconfigure 
``` command?

---

