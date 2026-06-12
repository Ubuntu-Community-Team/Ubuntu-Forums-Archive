---
title: "No Wifi even with bcmwl-kernal-source"
date: 2017-05-23
forum: MINT
---

### Post by jake1232 on 2017-05-23
Ok so i have bcmwl-kernel-source and when i first installed it it worked but after a restart it still has the connection in network connections but it wont connect without a cable
and i know theres a lot of these but Ive tried and nothing has worked.
also i'm running Linux mint 18.1 cinnamon i know there not the same but there very similar kernel wise

---

### Post by ajgreeny on 2017-05-23
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by jeremy31 on 2017-05-23
See the wireless script link in my signature and post your results

---

### Post by jake1232 on 2017-05-24
[https://pastebin.com/dgJdX90N](https://pastebin.com/dgJdX90N)

---

### Post by jeremy31 on 2017-05-24
I would edit the /etc/modules file and remove the b43 entries as your wifi will only work with the module from bcmwl-kernel-source

---

### Post by jake1232 on 2017-05-24
cool
still no internet without a cable

---

### Post by wildmanne39 on 2017-05-24
Please do:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot

---

### Post by jake1232 on 2017-05-25
nope didn't work

---

### Post by wildmanne39 on 2017-05-25
Please run the script again so we can see what else is going on with your network.
Thanks

---

### Post by jake1232 on 2017-05-25
[https://pastebin.com/q2PbBZU9](https://pastebin.com/q2PbBZU9)

---

### Post by wildmanne39 on 2017-05-26
In network manager do you have wifi enabled? is it enabled in the bios if you have that option? it does not even show up in iwconfig, of course may be there is a difference in mint that I do not know about compared to ubuntu.

---

