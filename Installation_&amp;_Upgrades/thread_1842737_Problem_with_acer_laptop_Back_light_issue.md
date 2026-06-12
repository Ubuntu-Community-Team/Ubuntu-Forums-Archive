---
title: "Problem with acer laptop Back light issue"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by jibon_24 on 2011-09-12
After installation of ubuntu 11.04 in my acer laptop I faced problem with back light. After that I use cron job to solve it . The process is here :

First do this if you not able to see anything:

1. ctrl+alt+t && write this code :
[HTML]
 sudo setpci -s 00:02.0 F4.B=0
[/HTML]
&& type your password & hit enter.

2. Now write again:
[HTML]
sudo gedit /etc/rc.local
[/HTML]

&& add this line before exit 0
[HTML]
setpci -s 00:02.0 F4.B=0
[/HTML]


Now create cron job .This will run the script for every 1 second.

1. Go to home folder & create a script at any name. For example : "display"
&& write this code:
[PHP]
 #!/bin/bash
 while [ true ]; do
 sleep 1
 sudo setpci -s 00:02.0 F4.B=0
 done
 [/PHP]2. Go to terminal & write:

[HTML] sudo crontab -e[/HTML]& select 2 if you first time.

3. Now write this line at the end :

[HTML]
*/1 * * * *  sudo sh /home/YOUR NAME/display
[/HTML]4. Now ctrl+O && then ctrl+x

Enjoy :popcorn:

---

### Post by Toz on 2011-09-13
Interesting. You're resetting the backlight value every minute. Were you finding that the backlight was changing frequently on its own?

On a related note, when you press your brightness keys, do they show brightness changing via notification but no real brightness change taking place?

---

