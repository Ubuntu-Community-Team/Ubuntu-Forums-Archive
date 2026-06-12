---
title: "How do I save my old home dir from live cd?"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by phreon on 2008-11-07
My old 8.04 install broke. I have to reinstall 8.04 from my cd. I need to try to save my old install settings so I am trying to copy my old home directory to a usb drive. The live cd will not let me copy my old home directory, probably due to permissions problem. 

Is there a way to get a copy of my old home directory to usb?

I have the live cd and my old install will at least crashes to a login prompt.

thanks
P

---

### Post by ronz0o on 2008-11-07
you'll probably have to use the terminal + sudo to do it.

sudo mkdir /media/usbdrive/Home
sudo cp -r /media/otherdrive/user/name/home/* /media/usbdrive/Home

then you will have to set the permissions of it
sudo chmod 777 /media/usbdrive/Home
sudo chmod 777 /media/usbdrive/Home/*
sudo chmod 777 /media/usbdrive/Home/*/*

and etc. change the usbdrive and otherdrive as needed to the directory that they are in. hope this helps!  =)

---

