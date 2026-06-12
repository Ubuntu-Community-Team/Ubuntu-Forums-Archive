---
title: "USB stick not working"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Erikhh on 2006-06-05
I have never ever had any problems with my USB memory stick, nor in Wharty or Hoary or other distros, but it doesn't work in dapper. There simply doesn't happen anything, when I attaches it. What to do?

---

### Post by Vati-Khan on 2006-06-05
give us the output of 

tail -f /var/log/messages

when plugging in the stick,
and the device's partition table please

---

### Post by Erikhh on 2006-06-06
When I plugged the USB device in to retrieve the output, it worked! The problem must have been, that I have worked as root for awhile, because I have another problem with the xserver. This time I plugged it in as user. Sorry to have taken your time.

---

