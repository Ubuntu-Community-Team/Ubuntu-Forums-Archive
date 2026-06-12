---
title: "How do I upgrade &quot;Maverick&quot; to &quot;Natty&quot; from live cd if I'm dual booting??"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by anti-other on 2011-05-19
[SIZE=2]K, so I'm dual booting Windows 7 and Ubuntu. I wanna upgrade Ubuntu 10.10 to Ubuntu 11.04. I boot from the 11.04live cd, I select "install", but there's **NO** upgrade option.. **HELP!!**[/SIZE] [SIZE=2]How do I upgrade[SIZE=2]**??**[/SIZE][/SIZE]

---

### Post by wojox on 2011-05-19
If you want to upgrade you need the Alternate CD.

---

### Post by anti-other on 2011-05-20
[SIZE=2]K, so I download **ubuntu-11.04-alternate-i386.iso**, and then what?? Do I just boot from the CD and upgrade, or do I just stick it in and it'll autorun and prompt me to upgrade??[/SIZE]
[ ]("http://mirrors.melbourne.co.uk/ubuntu-releases//natty/ubuntu-11.04-alternate-i386.iso")

---

### Post by Zero2Nine on 2011-05-20
> **anti-other said:**
> [SIZE=2]K, so I download **ubuntu-11.04-alternate-i386.iso**, and then what?? Do I just boot from the CD and upgrade, or do I just stick it in and it'll autorun and prompt me to upgrade??[/SIZE]
[ ]("http://mirrors.melbourne.co.uk/ubuntu-releases//natty/ubuntu-11.04-alternate-i386.iso")

If you just want to upgrade you can do that with the update manager or via the terminal from within your already installed 10.10. Seems like the easiest option to me. That is if you have a working internet connection on that machine.

[https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)

---

### Post by Aardwolf96 on 2011-05-20
Even so, you can just format your Ubuntu partition.
There was a thread on that somewhere that I started.
Somewhere...

---

### Post by anti-other on 2011-05-20
[SIZE=2]K, I don't want to format, and I want to do, if possible, an offline upgrade. I just want to know what I should do once I've downloaded the **alternate iso**
[/SIZE]

---

### Post by linuxinstalledfromhdd on 2011-05-20
I don't know about an offline upgrade. Sorry.

In terminal you can run:

sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by kansasnoob on 2011-05-20
> **anti-other said:**
> [SIZE=2]K, so I'm dual booting Windows 7 and Ubuntu. I wanna upgrade Ubuntu 10.10 to Ubuntu 11.04. I boot from the 11.04live cd, I select "install", but there's **NO** upgrade option.. **HELP!!**[/SIZE] [SIZE=2]How do I upgrade[SIZE=2]**??**[/SIZE][/SIZE]

I'm curious what your current drive/partition layout is. Please post the output of this command:

```
sudo parted -l
```

BTW that's a lower case L.

---

### Post by kansasnoob on 2011-05-20
> **anti-other said:**
> [SIZE=2]K, I don't want to format, and I want to do, if possible, an offline upgrade. I just want to know [COLOR="Red"]what I should do once I've downloaded the **alternate iso**[/COLOR]
[/SIZE]

[https://help.ubuntu.com/community/NattyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/NattyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

