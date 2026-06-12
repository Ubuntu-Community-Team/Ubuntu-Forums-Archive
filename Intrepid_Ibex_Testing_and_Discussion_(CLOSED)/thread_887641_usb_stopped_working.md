---
title: "usb stopped working"
date: 2008-08-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by matthewbpt on 2008-08-12
My usb on intrepid has suddenly stopped working and I have no idea why, a few days ago i had my ipod connected and it was working fine, but today I discovered it stopped working when I plugged in a usb wireless adaptor, it didn't work and I thought there was something wrong with the adaptor, but then I tried plugging in a usb memory stick, nothing, my ipod, nothing. Very worried I booted into a Ubuntu hardy live cd I have to see if that would work, and all my usb devices worked perfectly! What's wrong with my intrepid?! =(

---

### Post by diebels on 2008-08-12
> **matthewbpt said:**
> My usb on intrepid has suddenly stopped working and I have no idea why, a few days ago i had my ipod connected and it was working fine, but today I discovered it stopped working when I plugged in a usb wireless adaptor, it didn't work and I thought there was something wrong with the adaptor, but then I tried plugging in a usb memory stick, nothing, my ipod, nothing. Very worried I booted into a Ubuntu hardy live cd I have to see if that would work, and all my usb devices worked perfectly! What's wrong with my intrepid?! =(
There's probably many things wrong with your Intrepid. If you want to help improving it, you maybe need to learn a bit more basics.

You could try
```
tail -f /var/log/dmesg
```when you plug in/remove usb devices.

---

### Post by matthewbpt on 2008-08-13
Well it turns out it turns out it has something to do with the usb wireless adaptor (Edimax EW-7318USG), when you plug in the adaptor any usb devices plugged in afterwards (even after the adaptor has been unplugged) don't work, and of course the wireless adaptor itself doesnt work either. Rebooting makes usb work again for any devices except plugging the wireless adaptor which starts the problem all over again. This doesnt happen on the livecd of Ubuntu Hardy though. I think it may be because of the internal wireless card inside my laptop, whose drivers are loaded through ndiswrapper module, maybe this module is causing a conflict with the usb wireless and making usb stop working on my system, because on the livecd ndiswrapper isnt loaded of course, and the internal wireless adaptor is detected but doesnt work, though the usb wireless works immediately out of the box and receives much stronger signals than the internal wireless with ndiswrapper. The reason I got the adaptor in the first place was because half the time the laptop doesnt seem to load the ndisrapper drivers properly so the wireless has become a real nuisance. I'll try to uninstall ndiswrapper and see if it fixes the issue. Any thoughts?

---

### Post by diebels on 2008-08-13
If there's some development of a native driver going on for your internal wireless adapter, you could get involved in bug reporting for it.

---

