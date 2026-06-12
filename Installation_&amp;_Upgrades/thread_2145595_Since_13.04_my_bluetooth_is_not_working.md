---
title: "Since 13.04 my bluetooth is not working"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by piggyr on 2013-05-15
My computer is a System 76 Lemur Ultra, i'm using a 64-bit ubuntu. SInce i upgraded my computer to 13.04 my bluetooth is not able to send  a file to my phone ir either my other computer. This is the error: GDBus.Error:org.openobex.Error.Failed: Unable to request session. Thank you very much :D

---

### Post by slickymaster on 2013-05-27
Hi, piggyr. Be very welcome to the forums.

What are you using to send files via bluetooth?```
sudo rfkill list
```will show you if bluetooth is softblocked. If it says 'Yes' then try:```
sudo rfkil unblock bluetooth
```
Other than that, you can check an already reported bug: [Bug #1148033]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033"), particularly you might want to see post[ #23]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/1148033/comments/23") as it might provide a workaround for it.

---

### Post by Ramazan on 2013-11-15
thanks

---

