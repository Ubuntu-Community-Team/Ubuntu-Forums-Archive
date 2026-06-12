---
title: "Mullvad VPN"
date: 2022-06-21
forum: Installation &amp; Upgrades
---

### Post by agemini68 on 2022-06-21
Mullvad released an update on their VPN service. When I try to install it, it is marked potentially unsafe by a third party and won't install. I've been using them for years, they are safe. How do I bypass the unsafe marking. There isn't anywhere to click to say I trust this source and it won't let me install it.

---

### Post by Holger_Gehrke on 2022-06-21
The fact that it shows '(null) (.deb)' as the source of the package and that searching for mullvad in the standard repositories gives me no results makes me think you installed this program by downloading the .deb file and installed it either through double-clicking it in the file manager (which should run the "Software" app and install the package) or from the command line (either with 'apt install path-and-filename' or with 'dpkg --install filename'). In that case there is no update, "Software" is only showing you what you've got installed. If there was an update, you'd have to find out about it yourself by visiting the website, download the new version and install it again. It is possible for the program to add a new repository to the software sources on your system (the tools for Linux provided by mega.co.nz do this ...) but in that case you would not see a "(null)" source ...

Holger

---

### Post by ActionParsnip on 2022-06-21
What is the full output of:
```

sudo apt update

```
Thanks

---

### Post by Frogs Hair on 2022-06-21
I just tested the.deb and run anyway dialog with a warning and a password prompt appeared. I did install and then remove the application.

[https://mullvad.net/en/download/linux/](https://mullvad.net/en/download/linux/)

---

### Post by agemini68 on 2022-11-16
I can't get it to install. on the old versions, I didn't have to jump through any hoops, it just installed. Now it gets hung up in loading application details.

---

### Post by agemini68 on 2022-11-17
I finally got it. I upgraded to latest ubuntu version then retried everything.

---

### Post by mullvadtester on 2023-09-22
Anyone else see Mullvad flagged as a Packet Sniffer by rootkit checkers? are all VPNS likely flagged as Packet sniffers? wg-mullvad was flagged multiple times but the latest time showed something a little different attached

---

