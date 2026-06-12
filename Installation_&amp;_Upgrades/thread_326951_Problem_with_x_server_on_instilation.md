---
title: "Problem with x server on instilation"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by Brudus on 2006-12-28
I'm having a pretty big problem with xserver when I try to install ubuntu.  I get to this screen where it tells me there is a problem with xserver and all i get is a screen of garbled text.  The iso file I was using to make the CD was 6.06 the LTS.  My graphics card is nvidia geforce FX 5200.  I snaped a shot with my camera phone, take a look.

[IMG]http://img226.imageshack.us/img226/3484/ubuntufailsc4.jpg[/IMG]

---

### Post by Brudus on 2007-01-02
:bump:
Can't anyone help me?

---

### Post by confused57 on 2007-01-02
Here's a site explaining problems with the xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

I assume you're getting this screen trying to boot the live cd, you can try:

Ctrl+Alt+F1, which will get you to a console.

press enter to login(believe that's all you'll need to do)

enter the following(at the $ prompt), one line at a time, pressing enter after each line:

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```

Select "no" at the first screen to detect your monitor, then just select the defaults, until you get to the video driver selection...select "nv" as the driver to use...you can also select which resolutions you want to use.   When you've completed configuration, enter:
```
sudo /etc/init.d/gdm start
```

or enter startx, press enter

You might be able to boot up in "Safe Graphics" mode with the live cd...you could install Ubuntu using the alternate cd, but you'd probably still have the same problem.

---

