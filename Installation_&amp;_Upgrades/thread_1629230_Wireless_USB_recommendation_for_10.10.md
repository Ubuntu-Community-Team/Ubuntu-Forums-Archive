---
title: "Wireless USB recommendation for 10.10"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by frankmoss on 2010-11-23
Hi,

I have 10.04  now and had a lot of issues with my usb adapter and could not get it to work. Now, I consider upgrading to 10.10 and want to know if anybody has succeeded to successfully install USB driver for the wireless usb device. Last time I was trying some kind of CNet and Netgear with ndiswrapper and found on this forum out that those devices were not working for others either. 

So, please write some words here which USB device did work for you on 10.10, 64bit. 

Thanks.

---

### Post by cybergnome on 2010-11-23
Wireless devices are not generic.  That means they need drivers that are specifically for them.  Linux development for USB wireless is lagging, and success, where it has occurred, usually involves using ndiswrapper with the proprietary Windows drivers.

---

### Post by Bucky Ball on 2010-11-23
> **cybergnome said:**
> Wireless devices are not generic.  That means they need drivers that are specifically for them.  Linux development for USB wireless is lagging, and success, where it has occurred, usually involves using ndiswrapper with the proprietary Windows drivers.

Untrue, in part. They generally have the same chipset as the internal card. Realtek are generally fine, I use an Australian one called Open Networks (which you should be able to find on ebay); worked straight out of the box. 

If a company is friendly (like Realtek and others) they will provide open source drivers for Linux (my Realtek laptop card worked immediately and doesn't need 'Additional Drivers' ('Hardware Drivers' in other releases)).

Broadcom is another that should work. The only reason many don't work 'out of the box' is that you need to get online with a cable, get your updates, then plug the dongle in *while you are online with the cable*. Proprietary drivers and firmware should be offered if available.

---

### Post by confused57 on 2010-11-23
This one has worked great in both 8.04 & 10.04:
[http://www.newegg.com/Product/Product.aspx?Item=33-156-152&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=33-156-152&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo)

Newegg occasionally drops the price to $9, may be worthwhile to check on Black Friday.

---

### Post by frankmoss on 2010-11-24
Thank you for replies.

@confused57 have you tried getting it to work on 10.10?

@Bucky Ball does it also work on 10.10?

---

### Post by confused57 on 2010-11-24
> **frankmoss said:**
> Thank you for replies.

@confused57 have you tried getting it to work on 10.10?

@Bucky Ball does it also work on 10.10?

I'd recommend sticking with Ubuntu 10.04, IF everything is working well on your pc other than the USB wireless.  Ubuntu 10.04 is an LTS and will receive security updates until 04/2013.

The Trendnet wireless USB  worked out of the box(WPA2-psk) and I haven't had any problems with dropped connections(25 ft from the router through 2 plaster walls plus a freezer).  Connections speeds are nearly as high as a wired internet.

It may take a few days, but I'll try downloading a 10.10 live cd & see if it works OK, if you really need to use the latest version.

---

### Post by Bucky Ball on 2010-11-24
> **frankmoss said:**
> 

@Bucky Ball does it also work on 10.10?

The Open Network USB dongle has a Realtek chipset and works out of the box with 8.04 which means it would work with 10.10. Realtek drivers seem to get better rather than disappear in the next release.

My laptop has a Realtek card, as mentioned earlier, which worked out of the box.

No additional drivers or firmware required for either. Maybe I was lucky  but they have plenty of Linux drivers on the Realtek site if you're  not. Should be easy to fix.

Identify what you have. What brand? You haven't mentioned exactly which USB dongle you have!

---

### Post by frankmoss on 2010-11-24
I don't have any right now. I want to buy and thats why I am asking...

---

### Post by Bucky Ball on 2010-11-24
[http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ac6lzq8-dhwz&ie=UTF-8&sa=Search&q=wireless+cards+ubuntu&hl=en](http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ac6lzq8-dhwz&ie=UTF-8&sa=Search&q=wireless+cards+ubuntu&hl=en)

That easy.

---

### Post by confused57 on 2010-11-30
> **confused57 said:**
> This one has worked great in both 8.04 & 10.04:
[http://www.newegg.com/Product/Product.aspx?Item=33-156-152&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=33-156-152&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo)

Newegg occasionally drops the price to $9, may be worthwhile to check on Black Friday.

This Trendnet wireless usb adapter(realtek) worked out-of-the box with Ubuntu 10.10 64-bit live cd, using wpa2-psk.  Any realtek wireless usb should work well with Ubuntu. I believe Bucky Ball has mentioned this previously.

---

### Post by Bucky Ball on 2010-11-30
> **confused57 said:**
> This one has worked great in both 8.04 & 10.04:
[http://www.newegg.com/Product/Product.aspx?Item=33-156-152&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=33-156-152&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo)

Newegg occasionally drops the price to $9, may be worthwhile to check on Black Friday.

Yea, I bought the Open Networks one for about AU$12, including postage on ebay Australia. Prob about 80c to make! lol

---

