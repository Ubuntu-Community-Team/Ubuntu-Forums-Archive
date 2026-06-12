---
title: "Trouble after downloading nagios!!! Help!!!!!!"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by ofadl on 2013-05-31
Hello all, and thanks for taking the time to read

I recently just finished downloading nagios on ubuntu server 12.04 and was using this [guide ]("http://www.tjdit.com/install-nagios-on-ubuntu-server-12-04/")as help. I thought i did everything fine, so i went to my web brower to fire it up, and got the "504 Internal Server Error". After some research, i think i figured out what im missing. I went to [FONT=Arial][COLOR=#000000]/etc/httpd/conf.d/nagios.conf, and it was completely blank and i cant figure out why. Can someone lend a helping hand on what to do now? Im a newbie sorry haha[/COLOR][/FONT]

---

### Post by linuxtechguy on 2013-05-31
I would just use opsview instead.

---

### Post by scottwilkerson on 2013-06-05
Depending on you system on Ubuntu 12 I believe the file you are looking for is /etc/apache2/conf.d/nagios.conf

The official guide from Nagios on Ubuntu is located [here]("http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html") but you would need to adjust to the latest version when you reach the wget section to get the latest

```
wget http://prdownloads.sourceforge.net/sourceforge/nagios/nagios-3.5.0.tar.gz
```


@linuxtechguy - Guiding someone to a different product isn't helpful

---

