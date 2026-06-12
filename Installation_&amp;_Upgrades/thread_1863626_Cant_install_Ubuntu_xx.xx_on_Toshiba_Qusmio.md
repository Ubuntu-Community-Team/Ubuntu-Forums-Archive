---
title: "Cant install Ubuntu xx.xx on Toshiba Qusmio"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by devxdev on 2011-10-18
Hi guys im having issues while trying to install ubuntu any version, on my Toshiba Quosmio X500 S1801

It starts to install and I get a message that its mounting ? or something for 2 seconds then my entire screen pixelates?

Strange thing is if i take that exact same copy and put it in VMWare Workstation it works 100% no problems..

Just wondering if anyone had any ideas what could cause this.

method:
reboot laptop.
boot from cd.
it starts & shows the "Ubuntu XX.XX" " .   .   . "
the next screen is where it pixelates..

any questions just ask i was referred here by a friend and would really like to be able to dual boot on my laptop..

---

### Post by Quackers on 2011-10-18
Welcome to UF :-)
Which graphics card are you using?
You may need to use a boot option (such as nomodeset) temporarily until proprietary video drivers can be installed.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by devxdev on 2011-10-18
> **Quackers said:**
> Welcome to UF :-)
Which graphics card are you using?
You may need to use a boot option (such as nomodeset) temporarily until proprietary video drivers can be installed.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Hey thank you very much i wish i would have been signed in while i was searching all night so i would have seen your post before i resurrected this post [http://ubuntuforums.org/showthread.php?t=1494430]("http://ubuntuforums.org/showthread.php?t=1494430")
opps.. but thats exactly what i had to to as he stated in that post too, nomodeset
Intel i7 990x
nVidia GeForce GTX 460M

Its also now working on other nvidias too,
3xxM series, and the 5x0M series thanks for the help too Quackers!

---

