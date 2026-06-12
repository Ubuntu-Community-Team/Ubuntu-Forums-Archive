---
title: "Installing Lightscribe on 64bit Ubuntu 9.10 karmic"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by DLM955 on 2010-01-06
I have installed lightscribe on Ubuntu 9.10 64bit and this is info gathered from several place that has worked for me...I used newest deb packages from the lightscribe web site they are not 64bit but still work with ia32-libs installed

first in x-term console inter      sudo apt-get install fakeroot alien ia32-libs

next install lightscribe system software named something like lightscribe-1.18.9.1-linux-2.6-intel.deb with this command in x-term with this command

 sudo dpkg -i --force-architecture lightscribe-1.18.9.1-linux-2.6-intel.deb

then install lightscribeApplications

 sudo dpkg -i --force-architecture lightscribeApplications-1.18.6.1-linux-2.6-intel.deb

then to set your permissions to run lightscribe inter

 kdesudo SimpleLabeler

 if you dont have kdesudo it will give you command to install it just install and inter command again

 then you can place it in your menu it has its own icon if you look under opt file were it installed application

 hope this helps

---

