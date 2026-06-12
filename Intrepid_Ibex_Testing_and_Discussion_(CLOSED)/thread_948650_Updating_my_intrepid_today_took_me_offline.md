---
title: "Updating my intrepid today took me offline"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by la5lia on 2008-10-15
Jus a few minutes ago I got the familiar message that there were upgrades available for my intrepid installation.
I did the update, rebooted, an my wlan card is no longer there !!??
My PC is a Lenovo 3000 N200.

/Steinar

---

### Post by overdrank on 2008-10-15
Moved to Intrepid Ibex Testing and Discussion :)

---

### Post by vgrisham on 2008-10-15
The wireless issue seems to have occurred at the same time as an [issue]("http://ubuntuforums.org/showthread.php?t=948700") that is preventing upgrade of linux-image-generic for lack of the dependency linux-firmware. Perhaps something is in the pipe that will fix both of these issues. 

Aren't betas fun?

---

### Post by zimt on 2008-10-15
Exactly the same happened to me, Ubuntu does not recognize the WLAN adapter anymore.
ACER TM5730, Intel Centrino2, Intel® Wireless WiFi Link 5000 Series (802.11a/g/Draft-N).
Even if I boot an older kernel (2.6.27-6-generic), the WLAN is gone.

---

### Post by arestivo on 2008-10-16
I have exactly the same problem with a linksys usb wireless adapter. Everything was working until the last update and now wireless links disappeared from the NetworkManager.

Dmesg reports an error requesting firmware for rt2x00lib. I don't know if this message was happening before.

Is there any info I can provide to help fix this problem?

Edit: Found solution in [another thread]("http://ubuntuforums.org/showthread.php?t=948665&page=2").

---

