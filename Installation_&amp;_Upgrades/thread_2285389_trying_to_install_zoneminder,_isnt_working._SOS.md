---
title: "trying to install zoneminder, isnt working. SOS"
date: 2015-07-05
forum: Installation &amp; Upgrades
---

### Post by thomas_margotta on 2015-07-05
i tried installing zoneminder via terminal, it didnt work. i tried apg-get purge, apt-get clean, apt get update, and then restarted the computer and tried from software center. didnt work there either. i have ubuntu 14.04, a old dell dimensions 8400. the 8.04 ubuntu zoneminder boot disc worked fine, but now im having issues installing it on 14.04. if this doesnt work ill see about either using a virtual machine or just sticking with ubuntu 8.04 but my hope is that it doesnt come to that, given its a 3 or so year outdated os. any help appreciated.

---

### Post by oldos2er on 2015-07-05
Please run ```
sudo apt-get install zoneminder
``` in a terminal and post the complete output here.

---

### Post by ubfan1 on 2015-07-05
Did you install/start apache2?  Here are some of my old notes (haven't done it recently either).

installed the ubuntu package 124.2
apache2 does not start automatically, and no startup checkoff.

To use apache2
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf-available/zoneminder.conf 
sudo a2enconf zoneminder

---

