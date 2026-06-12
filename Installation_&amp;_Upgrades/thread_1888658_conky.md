---
title: "conky"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by KrisDeniseRiley1 on 2011-11-29
I see some of the guys in class with really nice conky's installed on there desktops. I love the way they look. [http://desktopspotting.com/26/best-conky-configs-for-linux-desktop/](http://desktopspotting.com/26/best-conky-configs-for-linux-desktop/) is a link for an example. I really like the crunchbang conky example they showed. I want to install or get some step by step help for installing something close to it. I keep being told that it involves scripts, which I am not a pro at, but I could follow step by step instructions.[IMG]http://ubuntuforums.org/home/pictures/conky.jpg[/IMG]

---

### Post by Frogs Hair on 2011-11-29
First , install these items from the terminal .
```
sudo apt-get install conky-all
``````
sudo apt-get install lm-sensors
```Next , run the following command and answer yes to all questions and close the terminal .
```
sudo sensors-detect
```The Conky at the link is  similar one and all you have to do is extract the package , move the folder any place you want ,  read how it works ,  and click the install run icon . It comes in dark and light version and there some information about weather at the link . [http://gnome-look.org/content/show.php/Conky+Flavours?content=94467](http://gnome-look.org/content/show.php/Conky+Flavours?content=94467)
This will get you started and you can find tutorials with a search if you want to work with more advanced scripts . There is also a Conky thread in the community  cafe where help and custom configurations can be found . [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

