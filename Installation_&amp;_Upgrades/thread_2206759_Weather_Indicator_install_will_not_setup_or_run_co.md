---
title: "Weather Indicator install will not setup or run correctly"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by aquaman2 on 2014-02-20
For Ubuntu 12 OS users, I solved the Weather Indicator setup problem -- 
Gui install from Software center does not work, have to use a terminal window setup and and do sudo update. 
 
1.  Remove this software 
 
2. Open a terminal window and use the following: 
 
Terminal Commands: 
 
sudo add-apt-repository ppa:atareao/atareao 
sudo apt-get update 
sudo apt-get install my-weather-indicator 
 
Once installed find it in Accessories / My Weather Indicator, 
it will auto setup to the closest neighbor community near you, 
if you want to name a location use Setup 2 below it.

---

