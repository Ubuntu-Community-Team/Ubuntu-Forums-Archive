---
title: "Wireless in Intrepid"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mschraier on 2008-10-05
I just installed Intrepid Beta.  The install went well and is residing next to Hardy 8.04.1 and XP.  The Wifi light on my laptop is lit, if I click on the silver globe in the system tray it shows my secure connection.  However, I have am not able to connect to the net.  Any ideas????  I have no problem whatsoever in Hardy using the net.           :guitar:    :guitar:

---

### Post by pytheas22 on 2008-10-05
If you think you're connected to the wireless network but can't load pages, it could be a DNS problem.  Or you could not really be connected.  Please post the output of the following:
```

lspci -nn
lshw -C Network
ifconfig
sudo iwlist scan
host google.com
ping google.com
ping 64.233.187.99
cat /etc/resolv.conf
```

---

### Post by cariboo on 2008-10-05
It might be better if you asked your questions here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Jim

---

