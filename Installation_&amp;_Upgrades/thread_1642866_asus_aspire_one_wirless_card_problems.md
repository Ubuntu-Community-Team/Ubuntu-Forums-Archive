---
title: "asus aspire one wirless card problems"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Justin Smith on 2010-12-10
Ok I have installed ubuntu 10.04 with upgrades on my wife's laptop. It works great but I cannot figure out how to get the built in wi-fi card to work. I have determined that the os can see and does recognise the card and that a driver is installed but it still does not show that I can activate the wireless. The laptop is a Asus aspire one. The wirless card is a Broadcom corporation product.

---

### Post by Justin Smith on 2010-12-16
When ever I try to activate or remove the Broadcom STA wireless driver I get an error message that says"SystemError:installArchives()failed. But it shows that that driver is active.

---

### Post by wacky_ninjas on 2010-12-16
The Ubuntu community has a set of help pages for the Aspire One series:
[https://help.ubuntu.com/community/AA1]("https://help.ubuntu.com/community/AA1")

Try the "Fixing Ubuntu" link there - it has specific instructions for wifi.

(This assumes that the laptop is an _Acer_ Aspire One, and not an Asus [EeeeePC]("https://help.ubuntu.com/community/EeePC").)

I have an older 9in Aspire One (AOA 110) myself. It's running [Madbox]("http://madbox.tuxfamily.org/") (an Ubuntu derivative, currently matching 10.10) and the wifi works with no tweaking at all.

---

### Post by Justin Smith on 2010-12-27
Well I can get the wireless to work on the b43 driver in fact I am on the computer right now. But I have the go into additional drivers and activate the driver and it will fail to install because it is already installed but then it will activate and find the 2wire network and is fully functional. It seems that the driver is not activating. Is there some way to start the driver on boot up?

---

### Post by Justin Smith on 2010-12-29
Alright well I reloaded the hybrid STA driver even though I think I could have done this with the b43 driver, but I couldn't find the modules for it! The driver was not loading on boot up so with the help of another thread in the forum I edited the boot module (I think that is what it is called)

sudo gedit /ect/module

#added "wl" to a new line,saved and rebooted.

---

