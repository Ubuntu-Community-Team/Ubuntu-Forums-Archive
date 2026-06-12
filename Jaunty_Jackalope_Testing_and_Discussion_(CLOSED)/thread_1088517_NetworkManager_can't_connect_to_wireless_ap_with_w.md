---
title: "NetworkManager can't connect to wireless ap with wpa"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by feiy on 2009-03-06
NetworkManager can't connect to wireless ap with wpa!it's can connect to wireless ap with wep

NetworkManage info:
Architecture: amd64
Version: 0.7.1~rc3-0ubuntu1

feiy@feiy-toy:/etc/NetworkManager$ uname -a
Linux feiy-toy 2.6.28-8-generic #27-Ubuntu SMP Thu Mar 5 00:30:14 UTC 2009 x86_64 GNU/Linux

feiy@feiy-toy:~$ cat /etc/NetworkManager/nm-system-settings.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

thanks!

---

### Post by albandy on 2009-03-06
Is your wifi 802.11g or only 802.11b, if your wifi card is a 11mb/s card is 11b and is not wpa compatible.

---

### Post by feiy on 2009-03-06
Last week, it  can be connected on the wlan.

the wifi is worked ok! and other pc (windows xp system) can connect the ap!

---

### Post by albandy on 2009-03-06
check if the process wpa_supplicant is running

---

### Post by feiy on 2009-03-06
feiy@feiy-toy:~$ ps -ef|grep wpa
root      3726     1  0 18:05 ?        00:00:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
feiy      7072  4565  0 19:00 pts/0    00:00:00 grep wpa

the /var/log/wpa_supplicant.log info:
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS

---

### Post by albandy on 2009-03-06
check in your router the wpa password in ascii (not in text like mypasswordispepe), something like 44332211244332233221112223399944 copy it and paste it to the wifi password box.

---

