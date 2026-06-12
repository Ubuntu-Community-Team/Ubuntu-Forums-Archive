---
title: "Bluetooth not detect dell Latitude E6400"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hyl4me on 2009-04-08
When I installed 9.04 Beta, I forgot to turn the switch (wireless + bluetooth) on, and now I couldn't get bluetooth.  Is there anyway to tell the computer to rescan (probe) for the bluetooth.  Thank you

By the way I am using GNOME and the laptop has Dell 370 bluetooth mini-card.

---

### Post by yelo3 on 2009-04-09
sudo hid2hci

---

### Post by hyl4me on 2009-04-09
> **yelo3 said:**
> sudo hid2hci

It still doesn't work.

```
root@my-laptop:/home/khoi# hid2hci
Switching device 413c:8158 to HCI mode was successful
root@my-laptop:/home/khoi# hcitool scan
Device is not available: No such device

root@my-laptop:/home/khoi# /etc/init.d/bluetooth restart
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
root@my-laptop:/home/khoi# hcitool scan
Device is not available: No such device

```

---

### Post by yelo3 on 2009-04-09
Also check that you have not disabled bluetooth in windows.

---

### Post by hyl4me on 2009-04-09
> **yelo3 said:**
> Also check that you have not disabled bluetooth in windows.

Funny that I just found out that too. You have to enable in Windows or else Ubuntu cannot enable it.  Wierd.

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/277211](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/277211)

Thank you Yelo3.  It works now.

---

