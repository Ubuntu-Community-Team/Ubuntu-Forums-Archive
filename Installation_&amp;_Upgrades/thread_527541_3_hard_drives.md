---
title: "3 hard drives"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by robalcorn on 2007-08-16
What is the best way for me to install Ubuntu on my desktop? I have a 250gb sata drive and 2 eide drives 120gb and a 30gb. When i try to install i seem to only have the option for one drive only and I want to dedicate all 3 to this o/s. Thanks

---

### Post by wolfen69 on 2007-08-16
what do you mean dedicate all 3 drives?

---

### Post by dougfractal on 2007-08-16
How to use Logical Volume Manager (LVM2)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_Logical_Volume_Manager_.28LVM2.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_Logical_Volume_Manager_.28LVM2.29)

did you mean create 1 mega partition?
or somthing like
/  30GB
/home  120GB
/video   250gb

---

### Post by robalcorn on 2007-08-16
What i am trying to achieve is basically install the O/S on the 30gb drive. Use the 120gb as my home drive. And yes use the 250gb for my video..wow you read my mind. I am use to the windows concept of c:/ d:/ etc . When i tried to install i did use the 30gb as my / than tried the 120gb as the /home but cant seem to use the sata 250 as /video. Sorry I forgot the msg keep running from room to room but something like you cant start the end at the beginning.

---

### Post by dougfractal on 2007-08-17
> but cant seem to use the sata 250 can't detect?
just format it with gparted  during install or later.    /media/sda1
when installed create a link from home folder to /media/sda1and call the link video.

---

