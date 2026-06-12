---
title: "After upgrade,  /etc/rc.local is NOT executed at boot, Help please."
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by yingwuzhao on 2009-12-11
I did a fresh install of Ubuntu 9.10 on my thinkpad T400, and put the following two lines in my /etc/rc.local to adjust the trackpoint speed and sensitivity:
```

echo -n 120 > /sys/devices/platform/i8042/serio1/serio2/speed 
echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity 
   
exit 0

```
It worked perfectly, but after I see the update-notifier pop up and did the upgrade (including kenel from 2.6.31-14 to 2.6.31-16). After reboot, I find the /etc/rc.local is not executed. But manually issue the /etc/rc.local in terminal works flawlessly. 

I tried to debug it by putting a line like "mkidr /home/Mark/test" before exit 0, then after reboot the folder test is not made, but issue command in terminal will have the folder test made. 

I suspect that when at boot up, the system encounter problems when trying to echo the number into the devices, thus stopped. I don't know what to do, please  help.

Thanks, guys.

---

### Post by yingwuzhao on 2009-12-11
I find a temporary solution add "sleep 10" in the following way in /etc/init.d/rc.local before executing the command did the trick:
```
(sleep 10; /etc/rc.local)& 
```

somehow if the commands of echoing execute too early it will fail, don't know what make this happen though.

---

