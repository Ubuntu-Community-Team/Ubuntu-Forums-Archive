---
title: "synce-trayicon and syncing Window mobil 6.1"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mike310z on 2009-02-07
I have been trying in vain to connect to my windows mobile phone under ubuntu 8.10, so with nothing to lose I loaded jaunty. 
I have had much more success alpha 4, seeing the pocket PC data appear and getting to the point of a messgae that appeard to need the tray icon to enter a password. Now it has all gone south.

I have been using the additional repositories suggested in the HOW to forums
 
```
deb http://ppa.launchpad.net/synce/ubuntu intrepid main
deb-src http://ppa.launchpad.net/synce/ubuntu intrepid main
```

But I now get the following error and I thought some one might be able to get me past why I get a seg fault.

```
mike@desktop:~$ dmesg
[  177.928145] usb 5-5.4: new full speed USB device using ehci_hcd and address 8
[  178.044540] usb 5-5.4: configuration #1 chosen from 1 choice
[  178.119426] rndis_host 5-5.4:1.0: RNDIS_MSG_QUERY(0x00010202) failed, -47
[  178.124229] eth2: register 'rndis_host' at usb-0000:00:1d.7-5.4, RNDIS device, 80:00:60:0f:e8:00
[  184.260975] synce-trayicon[4438]: segfault at c4 ip b7be3bc7 sp bfb62280 error 4 in librapi.so.2.0.0[b7bdf000+11000]
[  186.485863] synce-trayicon[4790]: segfault at c4 ip b7c25bc7 sp bfea25c0 error 4 in librapi.so.2.0.0[b7c21000+11000]
[  186.881376] synce-trayicon[4795]: segfault at c4 ip b7d05bc7 sp bf8830f0 error 4 in librapi.so.2.0.0[b7d01000+11000]
[  187.277446] synce-trayicon[4800]: segfault at c4 ip b7cd4bc7 sp bfc52b70 error 4 in librapi.so.2.0.0[b7cd0000+11000]
```

---

