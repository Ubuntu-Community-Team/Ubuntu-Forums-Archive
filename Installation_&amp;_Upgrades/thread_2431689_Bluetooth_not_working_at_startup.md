---
title: "Bluetooth not working at startup"
date: 2019-11-20
forum: Installation &amp; Upgrades
---

### Post by giaxdj98 on 2019-11-20
Hello everyone, after updating Ubuntu from 19.04 to 19.10 bluetooth seems to have stopped working, in fact if I try to switch on from settings the screen continues to be blank.
[IMG]https://imagizer.imageshack.com/v2/320x240q90/924/G8xJ7C.png[/IMG]

It only starts if I run from terminal:
```
[COLOR=#555555][FONT=Monaco]sudo /etc/init.d/bluetooth restart[/FONT][/COLOR]
```
But I should do it at every startup.
This is the result with status command:
```
sudo /etc/init.d/bluetooth status
```
```
&#9679; bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; disabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:bluetoothd(8)



```
Any solutions? Thanks you.

---

### Post by rsteinmetz70112 on 2019-11-20
Looks like the service is disabled.

---

### Post by giaxdj98 on 2019-11-20
Yes, I think so too. How can I enable it at startup?

---

### Post by rsteinmetz70112 on 2019-11-22
First:
```
sudo systemctl enable bluetooth
``` you can also 'start' 'stop' 'disable' and 'restart'

Also check the settings menu.

Have a look at /etc/bluetooth/main.conf - it may have this (uncommented) at the end - AutoEnable=true

---

### Post by giaxdj98 on 2019-11-25
Thank you, it seems to work

---

