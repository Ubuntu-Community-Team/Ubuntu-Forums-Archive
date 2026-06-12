---
title: "AMD Radeon 6970 and problems.."
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by Dr.Paneas on 2011-03-19
Previously this week I was trying to play Unigine Heaven benchmark with my Ubuntu 10.10 64bit using integrated graphics from my CPU Core i5 2500K (Sandy Bridge). Unfortunately I couldn't make it, so I decided to try with my Radeon 6970.

Ok, fresh install.
```

sudo apt-get update
sudo apt-get upgrade

```

Trying to launch the Unigine Heaven...error..

app-apt-reposity xorg egde
sudo update and upgrade

error again...

installing proprietary drivers... BLANK SCREEN, cannot even boot with Ubuntu

Ok re-install format disk etc etc. Let's try the *.run from AMD official website... it says you have not 64bit version...

I WILL KILL IT ! :popcorn:

---

### Post by Claus7 on 2011-03-19
Hello,

&#947;&#949;&#953;&#945; &#963;&#959;&#965; &#916;&#961;. &#928;&#945;&#957;&#941;&#945;!

concerning the issue you are facing, I think that by just installing the proprietary drivers from amd's website, this won't solve your problem. You should try to create a xorg.conf file first.

I have a similar card and I had made some tweaking, so as to make it work!

first of I would try:
```
sudo aticonfig --initial
```

so as to create a descent xorg.conf file (under /etc/X11). Then reboot. If that does not work, then you have to tweak this file manually, yet this is another issue.

About the program you are mentioning, hope that if you fix your driver's installation issue, then you would be ok.

edit:under System->Administration->Additional drivers, have you enabled your card's driver?

&#935;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;,
Regards!

---

### Post by Dr.Paneas on 2011-03-19
&#915;&#949;&#953;&#945; &#963;&#959;&#965; &#966;&#943;&#955;&#949; Claus :D

I followed this super guide ( [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide) ) and everything seems Ok :)

I will try to play Crossfire with my 2x6970 just for testing purposes.

Thank you very much

&#954;&#945;&#955;&#972; &#946;&#961;&#940;&#948;&#965;
Regards

---

### Post by walidzohair on 2011-06-14
nope not solved it just do not work even when you follow the guide exactly

---

