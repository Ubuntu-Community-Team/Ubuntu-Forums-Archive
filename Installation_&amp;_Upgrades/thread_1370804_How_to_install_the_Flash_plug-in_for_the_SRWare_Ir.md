---
title: "How to install the Flash plug-in for the SRWare Iron browser (alternative version)"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by shiroyoshida on 2010-01-02
Today I downloaded the latest version of the SRWare Iron browser as it became available for 64bit Linux distributions (woooo-hoooo!). 

I was very pleased with it but there was no support for Flash-enabled content. I looked into it and found a thread on SRWare's forum [[http://www.srware.net/forum/viewtopic.php?f=18&t=561#p2119]](http://www.srware.net/forum/viewtopic.php?f=18&t=561#p2119]) which didn't solve my problem. So I thought of starting a thread here which will hopefully help others who are facing the same problem. :-) 

Please note that these instructions are for users who have just installed Iron on their systems. 

1) First of all, navigate to Iron's folder and create another folder called "plugins". 
2) Now, most forum posts I've read, suggest you create a symlink to libflashplayer.so by doing
```
ln -s /usr/lib/flashplugin-installer/libflashplayer.so
```
while in the "plugins" folder. In my case this didn't work due to permission problems. So I took an alternative route and copied the libflashplayer.so file as 
```
cp /usr/lib/flashplugin-installer/libflashplayer.so /path/to/Iron/plugins/folder
```
3) I then modified the launcher to include " --enable-plugins" but it still didn't seem to work... 
4) As a last ditch attempt, I've changed the permission of the libflashplayer.so file which I had copied into the "plugins" folder by right-clicking it and from the Permissions tab I checked the "Allow executing this file as program".
5) A visit to YouTube assured me that it finally worked! 

Good luck to anyone else who has the same problem and I hope this thread will be helpful to you. :-)

*Disclaimer: Flash support is a bit flaky in Iron on Linux. Don't expect any miracles. You may need to refresh the page a couple of times to get the Flash content to work. *

---

### Post by schmickey on 2010-09-19
Edit: Nov 1, 2010
Any update for this for Maverick?

Just wondering....

---

