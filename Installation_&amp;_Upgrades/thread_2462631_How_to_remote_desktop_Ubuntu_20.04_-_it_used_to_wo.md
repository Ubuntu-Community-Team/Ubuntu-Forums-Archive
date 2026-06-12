---
title: "How to remote desktop Ubuntu 20.04 - it used to work in 16.04"
date: 2021-05-24
forum: Installation &amp; Upgrades
---

### Post by freeflyjohn on 2021-05-24
I have performed a fresh install of Ubuntu Server 20.04 desktop having previously been using 16.04.


The server is headless so I would normally use my Mac Book Pro to get remote access to the desktop of Ubuntu (on the internal network). 


This was easy to setup and worked well for 16.04, but the same setup does not seem to work with 20.04. 


How do I setup remote desktop on 20.04 so that I can access it using my Mac like I used to ?


Below is how I originally configured it on 16.04....


In Ubuntu:


1. Open Desktop Sharing and configure the settings as show...


[ATTACH=CONFIG]288538[/ATTACH]


2. Install dconf-tools...


```
sudo apt-get install dconf-tools
```


3. Open dconf-tools...


Expand ‘org’
Expand ‘gnome’
Expand ‘Desktop’
Select ‘Remote Access’
Uncheck ‘Require Encryption'(don’t click on Set to Default as it rechecks it)
Exit dconf-Editor


[ATTACH=CONFIG]288539[/ATTACH]




4. On the Mac, open Screen Sharing and enter the IP address to connect...




[ATTACH=CONFIG]288540[/ATTACH]




In 20.04, the screen sharing settings do not allow me to move the slider in the top left (it goes straight back to off) and it says 'No networks selected for sharing'.  It's also not possible to install dconf-tools like I did in 16.04


[ATTACH=CONFIG]288541[/ATTACH]

---

