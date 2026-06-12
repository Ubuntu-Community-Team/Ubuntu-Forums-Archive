---
title: "Installation Problems with ATI Card"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by ramibotros on 2006-08-10
I booted up through the red CD i received from Ubunutu :D  (which is a very nice thing actually) .. now i boot from it, i choose "Run or Install" to open the Ubuntu Live, just like i did on my friend's laptop. Yet i think it has problem with my Graphic Card, because after loading it shows 4 tiny identical squares, which appear to actually include the interface of ubuntu. On Windows, it says my graphics card is called : RAGE 128 PRO AGP 4X TMDS (ATI) ([This one]("http://www.ati.com/products/faqs/rage128profaq.html"))
Through a little bit of googling i found out ubuntu had some problems with ATI. Any quick, clean solutions on how i'll run it? Which drivers should i get and should i install those after i install ubuntu on the HDD, or is there a way to use it in the live session?

---

### Post by John.Michael.Kane on 2006-08-10
ramibotros If you can get a command prompt going you can try to edit your /etc/X11/xorg.conf so that your video card uses vesa drivers. on the other hand you can try [COLOR="Blue"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

