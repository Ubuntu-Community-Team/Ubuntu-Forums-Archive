---
title: "Installing 11.04 server requests inserting CD"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by kladdert on 2011-05-31
Hi, I'm installing Ubuntu 11.04 Server adm64. ISO-file burnt to CD, boot from CD and began the installation. After configuring everything the installation (copying of files) was running to about 75%, then suddenly it asks for inserting a CD named something like "Natty Narwahl 11.04 amd64 2011-04-26". This is the CD that is already inserted, I thought and pushed the tray in and out, but it didn't work. The UI did not respond to me pushing enter, and the "go back" button did not send me back either.

So I rebooted my machine and Googled for a couple of minutes. I saw that sometimes the alternate CD is recommended, and since my machine is pretty old I downloaded the alternate CD and tried again. Same thing happens with alternate, so I don't know what to do.

Possible things that could be the error:
[LIST]
[*]No internet connection during installation
[*]Some hardware error in my hard drive. But it seems unlikely to cause this error
[*]The graphics card is built-in and sucks pretty bad
[/LIST]

Please, someone, help me out. I have no idea what to do, and I don't want to switch linux distribution just to cope with this silly problem. Thanks.

---

### Post by s0nspark on 2011-06-01
I too am seeing this on one of our servers... I tried the normal desktop cd and it installs fine. This is a fairly new Dell server and I've had Ubuntu 10.04.2 running just fine on it.

---

### Post by kladdert on 2011-06-01
I solved this issue by installing Ubuntu Server 10.04.2 instead. The issue did not occur then, and my server is running smooth.

However, it is too bad that there is no more information on the error being presented to the user.

---

### Post by s0nspark on 2011-06-02
Ultimately I got past this by using Startup Disk Creator to make a bootable flash drive from the server iso image... Installing from the flash drive worked without a hitch!

---

