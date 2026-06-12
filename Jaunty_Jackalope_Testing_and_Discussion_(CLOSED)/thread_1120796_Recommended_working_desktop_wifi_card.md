---
title: "Recommended working desktop wifi card"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mykrob on 2009-04-09
Got a friend who wants me to put Jaunty on his desktop computer as he has been thoroughly enjoying Intrepid on his laptop.

Can any of you recommend a desktop wireless card that will work with minimal trouble? 

Thanks,
-myk

---

### Post by skymera on 2009-04-09
Belkin F5D7000 PCI works out the box.
Belkin F5D7050 USB works out the box.

I use both :)

---

### Post by cariboo on 2009-04-09
I recommend D-link products, Every adapter I've tried has worked out of the box.

Jim

---

### Post by go7Ul1ai on 2009-04-09
> **cariboo907 said:**
> i recommend d-link products, every adapter i've tried has worked out of the box.

Jim

+1

---

### Post by Polygon on 2009-04-09
if you have the money, get a atheros chipset that is capable with 'n' networks, they are supported by a completely open source driver (ath9k) and should be the least trouble out of any card.....in theory

---

### Post by ronacc on 2009-04-09
I have 3 intelinet (cheap) wireless cards that work great and the antenna is on a cable so you can get it out from behind your box for better reception , they are only  "G" though not "N" .

---

### Post by mykrob on 2009-04-16
Just got in the wifi card we ordered, a Belkin F5D7000. Placed it in the machine (jaunty, all updates as of five minutes ago), and it boots fine until it hits the login screen then locks up. I have a pulsing yellow ligth on the card. 

If i remove the card, the machine boots as normal...

I understand (now) that the Belkin card ships with a myriad of chipsets, and this one has the RTL8185L chip.

Am i screwed?

Thanks,
-myk

---

### Post by PGHammer on 2009-04-17
> **mykrob said:**
> Just got in the wifi card we ordered, a Belkin F5D7000. Placed it in the machine (jaunty, all updates as of five minutes ago), and it boots fine until it hits the login screen then locks up. I have a pulsing yellow ligth on the card. 

If i remove the card, the machine boots as normal...

I understand (now) that the Belkin card ships with a myriad of chipsets, and this one has the RTL8185L chip.

Am i screwed?

Thanks,
-myk

Ouch; that smarts.

I've used an SMC USB wireless-G adapter in both Intrepid and Jaunty flawlessly; I'm hunting for a wireless-N adapter (USB, of course) that is also supported directly by Jaunty.  (Desktop, not portable; I'll likely be moving my current desktop to my bedroom when I get my new admin station/media server in place.  The new admin box is actually an older Dell Optiplex GX 260 that I will likely throw Windows Home Server on.)

---

### Post by mykrob on 2009-04-17
I ended up putting that wifi card in a Windows machine I just built for a media center in our living room. I was going to put Mythbuntu on it when I receive the new videocard  I ordered, but I need working wifi on it.. Bummer...

---

### Post by Martje_001 on 2009-04-17
Ralink chipsets also have open-source drivers.

---

### Post by talkingwires on 2009-04-17
Anything with the Intel 2100/2200/2915/3945 chips works flawlessly, the drivers were open-sourced a couple years back.

---

### Post by autocrosser on 2009-04-17
I've been using this one:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16833180052](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180052)   It's a Encore that uses the ralink 2680 chipset---after editing the ralink2680.dat file I get 270 to my N router.....Not a bad unit for cheap......

---

### Post by mykrob on 2009-04-20
> **Martje_001 said:**
> Ralink chipsets also have open-source drivers.

unfortunately, though, this machine locks hard as soon as it hits the login screen as long as that card is in the machine..

---

### Post by autocrosser on 2009-04-20
Yes---you have a RTL8185 chipset---we're talking about a RTL2680 chipset---different unit---the Encore card is very lo-cost & a good way to test.....

---

### Post by Phreaker on 2009-04-20
Linksys WUSB54GR works out of the box

---

### Post by ronacc on 2009-04-21
I have an airlink card with an rtl8185 in my test box and it works out of the box with jaunty . try removing quiet and splash from your bootline so you can see where it is hanging .

---

### Post by Reiger on 2009-04-21
ASUS USB N-11, with drivers from Ralink. Will have to edit a .h file though, but after that it compiles & works flawlessly. 2 floors of re-inforced/amoured/w-ever-it-is-in-English concrete and still a good 100Mb/s. Works better than in Vista. :)

So a rt2870 based product (USB).

For laptops: Intel Wireless WiFi Link 4965AGN REV=0x4, works really well too.

---

### Post by bennachie on 2009-04-21
I'll add my vote for D-Link products. Certainly the DWA-110 USB works out of the box on Jaunty (that's how I'm posting this note).

---

### Post by ssam on 2009-04-21
there are a few retailers who specialize in linux. some of them sell wireless cards that are known to work.

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/) is good in the uk.
[http://www.efficientpc.co.uk/](http://www.efficientpc.co.uk/) used to have wifi cards (IIRC), but dont seem to currently

---

### Post by t.alex on 2009-04-21
> **Polygon said:**
> if you have the money, get a atheros chipset that is capable with 'n' networks, they are supported by a completely open source driver (ath9k) and should be the least trouble out of any card.....in theory

AR5008 works just great here! :)

---

