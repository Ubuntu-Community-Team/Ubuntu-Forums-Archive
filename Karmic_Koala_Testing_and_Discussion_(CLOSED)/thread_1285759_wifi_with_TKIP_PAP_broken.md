---
title: "wifi with TKIP PAP broken"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yaywoop on 2009-10-08
I have a EEEPC 1000h running 8.10 UNR, I connect daily to my University network (RMIT) which requires WPA2 TKIP and PAP encryption.

I tried out the 9.10 UNR Beta (installed it from a flash drive to my HDD) and the above encryption appears to be broken. it never gets past the 'one green ball' in the task bar, and after a few seconds asks for the username/password again. I am using the same settings as in 8.10 to login.

I have tried running "apport-cli -f -p network-manager-gnome" to get some useful debug info to send in, but it doesn't appear to save a file in /tmp as its supposed to when offline.

This was also an issue in the final build of 9.04 UNR (which is the reason I haven't upgraded to that)


On a side note, I tried updating network-manager-gnome from 0.7.1 to 0.8 by installing the latest karmic repositories, then using synaptic to upgrade that package. After reboot I get a serious error message and no access to a command line. 
alt+F8 output: 
```
mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (764) terminated with status 127
rm: cannot remove '/forcefsck': Read-only file system
init: mountall post-stop process (765) terminated with status 1
```

---

### Post by kreggz on 2009-10-10
you could ask your it people to check their radius logs. this will give you an indication whether it is a client or a backend problem

---

### Post by yaywoop on 2009-10-10
What sort of backend problem could it be? the wireless works under windows and the earlier ubuntu as I mentioned. Something must have changed in how network manager or wpa supplicant handles it.
I did talk to the guys behind the computer help desk and of course they don't really know whats going on. he told me that the wireless hadn't worked on ubuntu for a while. which seems to indicate that I am not the only one having problems in later editions of ubuntu.

Maybe if i get time i will try compiling and installing the latest network manager.

---

### Post by kreggz on 2009-10-10
when you said PAP did you mean PEAP? If so they may require your machine be attached to the domain.

---

### Post by yaywoop on 2009-10-10
nope, i meant PAP.
here is my blog entry on the setup in 8.10
[http://woop.wordpress.com/2009/03/06/wifi-at-rmit-on-ubuntu/](http://woop.wordpress.com/2009/03/06/wifi-at-rmit-on-ubuntu/)

---

### Post by yaywoop on 2009-10-12
nvm. This issue seems to be fixed in a later Beta build. I downloaded yesterdays build and it connects fine.
(NetworkManager Applet 0.7.996)

Thanks for your suggestions anyway kreggz.

---

