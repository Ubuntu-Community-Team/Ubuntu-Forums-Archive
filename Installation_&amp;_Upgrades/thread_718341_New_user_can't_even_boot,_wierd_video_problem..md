---
title: "New user can't even boot, wierd video problem."
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by pepsifx357 on 2008-03-08
The problem looks like a refresh rate malfunction but I don't know how to fix it.  I'm running a new macbook pro(Nvidia 8600m GT) and using virtualbox.  When it tries to boot up it gets to a screen with the Ubuntu logo hatched and tripled across the screen just like in windows when you would get the wrong refresh rate on your resolution.  It never goes past that.

---

### Post by zvacet on 2008-03-08
Boot in recovery mode and type 

```
dpkg-reconfigure -phigh xserver-xorg
```

select **vesa** driver and when you are finish you should have basic graphic.Search for your card driver later.

---

### Post by firecrow8 on 2008-03-08
I have the same problem. I've installed Ubutnto 7.10 from the alternate text instalation CD. worked fine. but when it boots up I see hte blank screen with horozontal lines

I selected the restore mode boot up option

and then saw a screen full of comands and things and then.
root@ubunto #:
so i entered: dkpg-reconfigute -phigh xserver-xorg
a message came up saying to type --describe to see all the options
**vesa** was not one of them.
so I selected **dkpg-reconfigute -phigh xserver-xorg --all**

after about an hour of all sorts of reconfiguring. nothing has changed.

when you specified to **select vesa** what specifically were you refering too.

any help appriciated. desperately trying to desengage whatever monitor or video driver ubunto is using.

---

### Post by zvacet on 2008-03-09
It is not **dkpg-reconfigute -phigh xserver-xorg.** It is **dpkg-reconfigure -phigh xserver-xorg**.If this command doesn´t lead  you to the drivers section then go to all reconfiguring process and when you come to the driver section select vesa diver and continue to the end.After restart you should have elementar graphic.

---

