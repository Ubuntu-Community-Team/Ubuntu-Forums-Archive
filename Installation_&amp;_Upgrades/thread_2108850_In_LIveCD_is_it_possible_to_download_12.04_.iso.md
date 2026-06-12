---
title: "In LIveCD is it possible to download 12.04 .iso?"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2013-01-25
I am in LiveCD mode. Is it possilbe to download the 12.04 alternative install .iso directly to a thumb-drive?

I tried to install UNetBootin, but apt-get through a error message with 'aisleriot' as causing a problem.

---

### Post by Bucky Ball on 2013-01-25
There is nowhere to install apps to when running from the install media (Boot Repair is the exception). 

No reason why you can't download the ISO though. Transmission (I think) is the default torrent client. Try downloading the torrent to wherever you like then burning to a CD/DVD. There should be a 'Startup Disk Creator' in the apps menu by default, though I'm using Xubuntu so not positive about that.

Hmm, second thoughts; will be impossible to make a CD if you are running from the CD already in the optical drive ...

---

### Post by darkod on 2013-01-25
You don't have any working computer/OS?

You can download the ISO on any computer or OS as long as you have a usb hdd/stick to save it there afterwards. Then in live mode connect both this usb hdd and the usb stick you plan to use as live usb and create it with the Start Up Disk Creator.

---

### Post by mc4man on 2013-01-25
> **Mark_in_Hollywood said:**
> I am in LiveCD mode. Is it possilbe to download the 12.04 alternative install .iso directly to a thumb-drive?

I tried to install UNetBootin, but apt-get through a error message with 'aisleriot' as causing a problem.
You can download to wherever you pick (right click > save link as
(if you only have 1 usb thumb & it's running the live cd then you would have needed to create storage space on it when created.
When installing apps on live session best to open software sources, disable the 'cd' & make sure all the Ubuntu sources are enabled, then update sources

> **Bucky Ball said:**
> There is nowhere to install apps to when running from the install media (Boot Repair is the exception). .
You can install apps in live session to the extent of free ram available

---

### Post by Bucky Ball on 2013-01-25
> **mc4man said:**
> 


You can install apps in live session to the extent of free ram available

Thanks. You live and learn.

---

### Post by mc4man on 2013-01-25
> **Bucky Ball said:**
> Thanks. You live and learn.

It's been a while since I fooled around that much with live sessions but iirc after login one would have around 50% of the systems total ram left to use here on a laptop w/ 3GB (likely less with onboard graphics.

So sometimes it can get a bit touchy if installing a number of apps with alot of deps.
One way to free up after an app install is to run sudo apt-get clean which will remove all the dl'ed .deb's in /var/cache/apt/archives

(one can also remove some default apps to create additional space - libreoffice* is a prime example

---

### Post by Mark_in_Hollywood on 2013-01-26
Something must have "hung" or not been loaded or not fully loaded because when I next re-booted the problems were gone. Go Figure!

---

