---
title: "Still won't detect SATA drive"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by foots2015 on 2006-07-24
Ubuntu and Mepis will not detect my SATA drive (3gbps). When I try to run qt parted i get message, "no device found maybe you're not using root user?". Please help me get linux installed:confused: 

here is a link to the harddrive it is a seagate barracuda, 80 gigabyte, SATA 3 GB/s:[http://http://www.seagate.com/cda/products/discsales/marketing/detail/0,1081,773,00.html]("http://http://www.seagate.com/cda/products/discsales/marketing/detail/0,1081,773,00.html")

Here is a link to the motherboard it is an Asus P5VDC-MX :[http://usa.asus.com/products4.aspx?l1=3&l2=11&l3=0&model=814&modelmenu=1](http://usa.asus.com/products4.aspx?l1=3&l2=11&l3=0&model=814&modelmenu=1)

---

### Post by John.Michael.Kane on 2006-07-24
If your booting with an IDE based device eg:cd/dvd/rw drive you may want to have look at this thread [**[COLOR="Blue"]booting stalls during "mounting root filesystem" - testing workaround(s)[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=1257154")

---

### Post by foots2015 on 2006-08-14
I've found the answer to my problem. My particular VIA chipset(VT8251) does not support running linux from a sata hard drive. It does, however, support running linux from a PATA (IDE) hard drive. At least that is according to some poeple on another forum. [-o<

---

### Post by foots2015 on 2006-08-15
I finally had success in installing ubuntu. I installed it on my PATA HDD. It still won't detect my SATA drive though.

---

### Post by foots2015 on 2006-08-30
Solved ! :)

---

### Post by mxreader on 2006-08-30
Mind sharing your solution?

---

### Post by foots2015 on 2006-09-01
> Mind sharing your solution?

I still haven't succeded in installing Ubuntu on the Sata drive, but I got it installed on the IDE drive. Now I can use ubuntu from the IDE drive and dual boot with XP from off the SATA drive. Windows>SATA, Ubuntu>PATA(IDE).

Is this what you were looking at trying to do?

---

