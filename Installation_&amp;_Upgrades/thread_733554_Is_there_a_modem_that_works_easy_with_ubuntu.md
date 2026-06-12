---
title: "Is there a modem that works easy with ubuntu?"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by computermark on 2008-03-23
I'm very new to linux and am trying to do my part promoting open source and linux to the world. I'm currently building systems and have been adding a linux partition to allow my customers to experience linux without having to deal with installation woes. I have many customers that still use ugh.. dialupc :( Is there a specific chipset or model of modem that isn't going to require a bunch of work getting dialup to function without a bunch of footwork required? I have a big pile of modems that have collected in my shop and it appears they don't even come close to plug and play. any suggestions are welcome.

Thanks Much!
Mark

---

### Post by Whiffle on 2008-03-23
Just about any external modem.  I've had good luck with this one:

[http://cgi.ebay.com/56K-Serial-USB-External-V-92-Actiontec-Modem-NEW_W0QQitemZ360021987742QQihZ023QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/56K-Serial-USB-External-V-92-Actiontec-Modem-NEW_W0QQitemZ360021987742QQihZ023QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by computermark on 2008-03-24
> **Whiffle said:**
> Just about any external modem.  I've had good luck with this one:

[http://cgi.ebay.com/56K-Serial-USB-External-V-92-Actiontec-Modem-NEW_W0QQitemZ360021987742QQihZ023QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/56K-Serial-USB-External-V-92-Actiontec-Modem-NEW_W0QQitemZ360021987742QQihZ023QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
Thanks for the info Wiffle!

   Are there any internal chipsets or PCI cards that will work? Sorry for sounding picky but the cost of externals is so much more than the internals and of course the dialup folks are usually the penny pinchers.

Thanks Again
    Mark

---

### Post by Whiffle on 2008-03-24
Its a tossup, i dont know of any off the top of my head.  Some modems can work with

[http://www.linmodems.org/](http://www.linmodems.org/)

but the external ones are definitly the bes.t

---

### Post by zoomzoomzoom on 2008-03-28
> **computermark said:**
> Thanks for the info Wiffle!

   Are there any internal chipsets or PCI cards that will work? Sorry for sounding picky but the cost of externals is so much more than the internals and of course the dialup folks are usually the penny pinchers.

Thanks Again
    Mark

Hardware modems are easiest of course.  There are internal 56k PCI hardware modem cards but they are rare and not sure any sold new, you would have to look on ebay or such.  Do a google to find numbers of these, most will be USR/3com.

If you dont mind serial external modem they are not hard to find.  I've bought new or near new off ebay for **under** $10 total shipped price.  Is that cheap enough for you? There are even some with built in serial to usb adapters.  And there are serial to usb adapters you can add to any serial modem if you need usb.  Want a pl2303 chip adapter, the ch341 chip ones are pain in rear though supposed to be supported under kernel 2.6.24 and newer.  

There are some usb only modems that work, but most are winmodems and you would need to find one that has linux driver.  

And some winmodems are supported under linux, use previous poster's link to find which ones are.  Not always the easiest to get them working, but its possible.

---

### Post by ralford on 2008-03-30
Trendnet ([http://trendnet.com/products/proddetail.asp?prod=110_TFM-560X&cat=51](http://trendnet.com/products/proddetail.asp?prod=110_TFM-560X&cat=51)) makes an external modem that works from the serial port. It is model tfm-560x and average retail is under 30 bucks. I used gnome-ppp as launcher for the modem and set the Firefox connection to auto detect. In the network settings select the modem as internet connection. I have used this modem on friends machines that are stuck with dialup and they have commented that it's almost like having dsl.

---

