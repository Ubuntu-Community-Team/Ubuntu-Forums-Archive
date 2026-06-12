---
title: "Hewlett Packard 2133 Mini-Note PC (KZ960PA) with Intrepid Ibex"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rogirwin on 2008-09-11
I recently brought an HP 2133 (KZ960PA) and installed Handy Heron onto it. With the help of the _[wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133")_ I managed to get everything working apart from the internal microphone and wireless.

lspci | grep BCM4312
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

After spending a few days playing with the b43 and ndiswrapper wireless driver I concluded that they were not going to work properly. I did manage to get it to connect to some access points and list the available networks but it was far from reliable.

I decided to try the alpha version of _[Intrepid Ibex]("http://cdimage.ubuntu.com/releases/intrepid/alpha-5/")_.

The good news is that wireless seams to work much better and maybe even 100% out of the box using the b43 drivers.

The bad news is that as yet there isn't a version of the Chrome9 drive for Intrepid on the _[Via website]("http://linux.via.com.tw/support/downloadFiles.action")_. The version there won't work for me as I guess it's the wrong kernel version(?).

Has anyone managed to get video working properly under Intrepid? If so with which drivers and how?

Thanks
Roger

---

### Post by ibutho on 2008-09-11
If its an option, you could try the [openchrome]("http://www.openchrome.org") drivers. They work fine for me (using a chrome9 hc igp based card) with Mandriva 2009 rc1. On openSUSE they don't work as well as they do using Mandriva. If that does not work, then try using the fbdev driver.

---

### Post by alan426 on 2008-09-11
There are open-source drivers available.  Apparently it's not so easy to compile against Ubuntu but people are working on it.

See
[http://forums.mininoteuser.com/viewtopic.php?f=11&t=549](http://forums.mininoteuser.com/viewtopic.php?f=11&t=549)

---

