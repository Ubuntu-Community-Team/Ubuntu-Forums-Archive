---
title: "unplug plug monitor works fine strange!!!!"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by napster86 on 2007-11-23
There's something weird going on with my Gutsy Gibbon..which i didnt face when i had Fiesty Fawn..its actually the usual out of sync @ boot up but if i unplug and plugin the monitor cable to pc everything seems to be normal with login window..poppin up and later destop..i ran the usual 
/etc/init.d/gdm stop
dpkg-reconfigure xserver-xorg nothin worked
then 915resolution but later came to know tht it doesnt work wid lates x11..
then edited xorg.conf file as im showin the monitor section..hope thts enough> Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung Samtron 56E/57E/56V"
	Horizsync	30-50
	Vertrefresh	50-90
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync  
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync

	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"640x480@60"
	EndSubSection
EndSection

well yeah im having i845G/GL lolzzzz!!!!

---

### Post by napster86 on 2007-11-23
> **napster86 said:**
> There's something weird going on with my Gutsy Gibbon..which i didnt face when i had Fiesty Fawn..its actually the usual out of sync @ boot up but if i unplug and plugin the monitor cable to pc everything seems to be normal with login window..poppin up and later destop..i ran the usual 
/etc/init.d/gdm stop
dpkg-reconfigure xserver-xorg nothin worked
then 915resolution but later came to know tht it doesnt work wid lates x11..
then edited xorg.conf file as im showin the monitor section..hope thts enough
well yeah im having i845G/GL lolzzzz!!!!
this is 4 the 1st time im facing probs wid ubuntu..and its really frustrating..rolled back to fiesty fawn...but i intend to run bleeding edge tech on pc..so pls do pm..if u got solution do this or just post a reply..

---

### Post by napster86 on 2007-11-24
hello veryone,

whts the reason people hmm no replies.aint it the rite forum to post dis question..anyway after plungin into open-source i realized tht..this is not 4 avg knwledge guy..well im neither a noob nor a xpert..but when i had a go wid ubntu.it workd all fine..until now..with gutsy givin some probs..
GOOD NEWS
i figure out a way..fiesty fawn did wonders 4 me..
1)install fiesty fawn..
2)upgrade it.
no probs again..seems like gutsy has prob wid new installatin in tht case i would ask u carry out dis two steps..hmm guys

innovation without any yelp..:guitar:

---

