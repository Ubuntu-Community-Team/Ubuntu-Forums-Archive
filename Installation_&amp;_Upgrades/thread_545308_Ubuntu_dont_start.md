---
title: "Ubuntu dont start"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by berkayonen on 2007-09-07
I have a problem about my ubuntu. 
I requested ubuntu fesity fawn and my cds arrived.

But i have a problem. I installed succesfull and restarted my computer. But when is restart i see ubuntu logo after that my computer screen shows letters like dos screen.And writes lise this 


loading kernel modules           OK 
loading manual drivers           OK
activating swap...                 
checking root file system 
fsck 1.40-WIP (14-Nov-2006)
/dev/sda6 : superblock last mount time is in the future  fixed 
/dev/sda6 : superblock last write time is in the future  fixed 
dev/sda6 has gone 49710 days without being checked , check forced 
firmware_helper[4069]: main error loading /lib/firmware/bcm43xx_microcode5.fw for device  /class/firmware/0000:03:00.0 with driver unknown . 
[    49.324000]  bcm43xx : error microcode bcn43xx_microcode5.fw not avalaible or load failed. 
/dev/sda6 :  I===================================                  I 84.8% 




when 84.8 or another number ( different at every boot ) computer not responding and nothing happen.

I guess my problem about dev sda6 because bcm43xx is my wireless card and this can not block my computer.





I need your help.


SDA6 IS MY ARCHIVE PARTITON

---

### Post by berkayonen on 2007-09-07
Is there anybody help me ?

---

### Post by maybeway36 on 2007-09-07
It could be a hard drive problem.

---

### Post by markoloka on 2007-09-09
Same problem... I have sata2 hdd... i doubt i've been using it for 49710 days... that would be like: 136+ years!!!!!!!!!
Checked on pc check and manufacturers own hd... no problem. So it's ext3 problem.

---

### Post by ronaldv2li on 2008-03-03
Well for me my bcm43xx blocked startup. 
Try blacklisting bcm43xx

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

---

