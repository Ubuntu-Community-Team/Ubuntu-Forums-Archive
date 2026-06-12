---
title: "ATI drivers in Karmic, How do I install?"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ram130 on 2009-08-27
> **Stochastic said:**
> No need to run to GetDeb.net for your 2.8.2 package, it's in Karmic's official repositories.


LiVES does not look to be in REVU yet, so it's unlikely that it will make it into the repositories before the feature freeze (August 27).  There was some talk on the mailing list about it being one that should get packaged soon though.


As for Karmic in general, look for 2.6.31-RT to be very stable as it is a release patch from the upstream RT guys rather than a snapshot of their development work (as some of the other RT kernels have been).

I've yet to get much testing in on 2.6.31-RT because it's not happy with my graphics card (ATI Radeon XPRESS 200M).  But overall Karmic looks good.

Yes karmic seem really stable, no problem except drivers. Heres my problem, i got  a ATI Radeon 3200HD and cannot install the ati drivers, why is that? I tried, envy(comes up a display line error after reboot yet the system seems to boot fine), ati site(comes up to a blank screen with nothing loading after the boot screen) and hardware drivers method(says its downloading then disappears)..any solutions? :confused:

---

### Post by Stochastic on 2009-08-27
I've moved your post from the multimedia production setion to its own thread in the Karmic Koala Testing & Discussion section because of a couple reasons
a) it was straying from the main thread topic
b) it was asking for technical support on a development release (which should only be done in the testing & discussion section)
c) by constantly mentioning how stable Karmic's RT kernel is, I've noticed a large influx of new and inexperienced users attempting to install Karmic alpha releases as their main OS (you and I both know how dangerous that is)

So as to tackling your techincal issue, by ATI drivers I assume you mean the fglrx drivers?

Have you tried the open source Radeon drivers?  They work great for my radeon card and then I don't have to wait around for ATI to release an appropriate driver.

---

### Post by ram130 on 2009-08-27
Ok thanks I didn't that posting went that way. Yes its the fglrx drivers, tried installing thoose and the one the main ati site. How do I install the open source radeon drivers for my card?

---

### Post by alphacrucis2 on 2009-08-27
> **ram130 said:**
> Ok thanks I didn't that posting went that way. Yes its the fglrx drivers, tried installing thoose and the one the main ati site. How do I install the open source radeon drivers for my card?

To install the fglrx driver you will have to wait until ATI produce a Catalyst release that supports the 2.6.31 series kernels.

[http://www.phoronix.com/scan.php?page=news_item&px=NzQ2Mw]("http://www.phoronix.com/scan.php?page=news_item&px=NzQ2Mw")

---

### Post by ram130 on 2009-08-29
> **alphacrucis2 said:**
> To install the fglrx driver you will have to wait until ATI produce a Catalyst release that supports the 2.6.31 series kernels.

[http://www.phoronix.com/scan.php?page=news_item&px=NzQ2Mw]("http://www.phoronix.com/scan.php?page=news_item&px=NzQ2Mw")


That is the problem why the drivers wont work with the ubuntu studio RT then, cause ATI has yet to release a new version for there driver for support with the new rt kernel, correct?

---

### Post by photographerHU on 2009-09-01
Hi,

Is any chance to get support in the near future(Karmic) for ati xpress 200M/1150 card. Unfotunatelly I bought the worst laptop for Linux. "Nothing" supported normaly.... So just because of this card I need to start to think to buy a new one? This situation is reminds me 4 something...

---

### Post by taavikko on 2009-09-01
> **photographerHU said:**
> Hi,

Is any chance to get support in the near future(Karmic) for ati xpress 200M/1150 card. Unfotunatelly I bought the worst laptop for Linux. "Nothing" supported normaly.... So just because of this card I need to start to think to buy a new one? This situation is reminds me 4 something...

The open driver should work on that GPU.
ATI's fglrx driver support is only for 600 and up.

---

### Post by photographerHU on 2009-09-01
Hi,

Thank you for the quich reply. I tryed a few tutorial: to downdrade xorg (I got 100% CPU), an other one (black screen) and finally I found this one: [http://ubuntuforums.org/showthread.php?t=1174943&highlight=photographerHU&page=4](http://ubuntuforums.org/showthread.php?t=1174943&highlight=photographerHU&page=4) Its still faaaaaar from perfect, but at least, I can have effects. Just a few things working in 3D. I still can not use skype for long time, because I get high CPU and other problems....
So Im just interest, that anything will change in Karmic, in the ati topic?

---

