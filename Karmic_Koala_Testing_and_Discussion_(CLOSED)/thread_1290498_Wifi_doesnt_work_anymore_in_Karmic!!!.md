---
title: "Wifi doesnt work anymore in Karmic!!!"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheEvilOne6620 on 2009-10-13
I am running Ubuntu on a HP dv4 1275mx which uses a Broadcom 4322 wifi card.  If you dont know the only driver that works undert his wifi card is the STA or wl driver.  In past versions of Ubuntu I have never had one issue with my wifi, it has always been up and running upon installation.  This however has now changed and I hope it is only for the beta.

In some Linux distros, Fedora, and OpenSuse are two good examples, I can see the available networks but I cannot connect to them.  One reason I dont use those distros.  However, in Karmic I cant see anyting, it's like there isnt even a driver installed for my wifi.

In fact, there isnt.  It does not make sense to me that this release would remove the only driver that works on my system from installing on a default install.  Secondly, I actually went and installed the driver myself and still nothing.  The really weird thing is that in past versions of Ubuntu if I go into the Hardware Drivers app, it will show the STA driver and the FGLRX driver for my ATI Radeon 3200 chipset.  Now in Karmic, the STA driver is no longer there.

Does anyone know, for one, if this is a bug or if this has been totally removed from Karmic?  And what can I do to get thigns working?  I know from past experience that the b43 driver does not work on a BCM 4322 chip so the only driver I can use is the STA driver.  Like I said though, downloading and installing it does nothing.  I am really disturbed by the fact that the driver isnt even there to begin with.  When I first installed Karmic I thought ok maybe it just didnt install, after all this is a Beta.  To my surprise though after going to Hardware Drivers with the hopes of simply clicking Activate, I was let down to find out it wasnt even on my system!!!!

Please someone tell me this is just a bug, I mean why would they remove the only driver that works for people with systems using this card???  I mean the point of a new release is to provide better hardware support as well as making things that already work better right???

Any help or insights would be great.

---

### Post by kreggz on 2009-10-14
I think broadcom sta is proprietary so you need to install it via Administration\Hardware Drivers

---

### Post by Ayuthia on 2009-10-14
You might want to go into the Terminal and check:
```
lshw -C network
```and see what driver it is trying to use.  It should show something like wl0 or b43-something.  If it shows b43, you can try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If it provides wireless sites, then the b43 module is being supplied as default (and is incorrect).

---

