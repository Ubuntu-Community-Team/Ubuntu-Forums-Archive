---
title: "No video during installation, even in safe video mode"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by cnbc on 2007-02-04
I was trying to install 6.10 on my desktop. It has an Asus A8N-E motherboard with a [Powercolor X800GT]("http://www.powercolor.com/main_product_detail_dis.asp?id=75") video card in the PCIE x16 slot.

When I boot from the live CD, I can see the main screen (one with booting options) fine. if I boot using normal video settings, I eventually see the screen below and it just stays there.
[IMG]http://img128.imageshack.us/img128/9485/dsc00665ps6.jpg[/IMG]

If I go into safe video mode, it eventually goes to these screens below:
[IMG]http://img266.imageshack.us/img266/7491/dsc00666up5.jpg[/IMG]
[IMG]http://img266.imageshack.us/img266/2774/dsc00667ig8.jpg[/IMG]
[IMG]http://img266.imageshack.us/img266/9896/dsc00668ul1.jpg[/IMG]

I suspect that it's a graphic related problem because Ubuntu is not detecting my video card properly.

The CD works fine on other systems, including one with ATI Radeon 9600 and even a S3 UniChrome integrated.

I really want to get Ubuntu running, but if I can't get this working, I might have to give Debian a try.

---

### Post by PartickThistle on 2007-02-04
The error messages on screen tell you all you need to know.

X cannot find suitable drivers for your card.  Either use the included generic ones or download the proprietary ones from ATI and install once you get to the blue screen.

Ctrl-Alt+Fx to change ttys.

---

### Post by mikewhatever on 2007-02-04
[TRY THIS PAGE]("http://users.bigpond.net.au/hermanzone/p7.html") If it still does not work, try getting Alternate installer CD from Ubuntu.com. It is a text mode installer, similar to that of older Windows. The site I've linked to has a page on how to install and a lot more.

---

### Post by cnbc on 2007-02-05
Thanks for the help. After the xserver failed message, i went to the console and entered :sudo dpkg-reconfigure xserver-xorg.

I then chose vesa instead of ati. Restart x11. Problem solved. ATI is a bit short when it comes to linux drivers.

---

### Post by Meshuggah27 on 2007-02-05
I was having the same problem.

Whenever i get through the xserver errors and hit ok on the last screen my screen just goes black and has a white blinking line and its not console and doesnt work when i type in ANY commands and i cant get to console to configure the xserver. help :(

---

### Post by mikewhatever on 2007-02-05
> **Meshuggah27 said:**
> I was having the same problem.

Whenever i get through the xserver errors and hit ok on the last screen my screen just goes black and has a white blinking line and its not console and doesnt work when i type in ANY commands and i cant get to console to configure the xserver. help :(

An Alteranate CD installer could be the solution. It hardly has any graphics at all and is less fancy, but it may work where a LiveCD fails. Hopefully, you'll be able to install, and then reconfigure Xserver. You can download an AlternateCD from Ubuntu.com. download page.

---

