---
title: "help with wireless card"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by zygoat_D on 2010-04-25
to start off. i have been using Linux off and on for years now. still fairly new.

i just installed ubuntu 8.04 (hardy heron) I CAN NOT UPGRADE TO A NEWER VERSION. due to some software i need to use.



the problem is with my wireless card. i can not install it. it does not work out of the box. but the drivers are available here.

[http://www.edimax.com/en/produce_detail.php?pl1_id=1&pl2_id=44&pl3_id=86&pd_id=1#03](http://www.edimax.com/en/produce_detail.php?pl1_id=1&pl2_id=44&pl3_id=86&pd_id=1#03)

unfortunately i do not know what in the world to do with them.


any help is greatly appreciated.

---

### Post by padnoter on 2010-04-25
I had a similar problem on an old dell laptop. Here are the notes I made about how I got round it;

download the windows driver on another pc & copy drivers to a usbkey & plugin to laptop.

system>administration>software sources
  "tick" the "installable from cd-rom" & put ubuntu 9.10 into cd drive

sudo apt-get install ndisgtk
              
system>administration>windows wireless drivers  or type...
sudo ndisgtk

select airplus.inf (this was my wireless windows driver) from usbkey
   (you get "unable to see...." error, just ok, & you will see card flashing & working)
              click on wireless & choose "default" connection.


hope this helps some.

regards
PN

---

### Post by zygoat_D on 2010-04-25
they have linux drivers. 

[http://www.edimax.com/en/support_detail.php?pd_id=1&pl1_id=1&pl2_id=44](http://www.edimax.com/en/support_detail.php?pd_id=1&pl1_id=1&pl2_id=44)

at the bottom. i have them downloaded, i just need to know how to install them.

im sure your method would work, but i would rater use the linux drivers.


also this is a pc not a laptop. and the adapter is a pci card.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041)


thanks again for any help

---

### Post by zygoat_D on 2010-04-25
bump

---

