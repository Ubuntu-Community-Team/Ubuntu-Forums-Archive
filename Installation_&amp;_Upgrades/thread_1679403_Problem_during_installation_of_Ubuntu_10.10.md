---
title: "Problem during installation of Ubuntu 10.10"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Hallstein on 2011-01-31
My problem is during the installation of Ubuntu 10.10 desktop edition, nothing happens post loading screen.
I've burned the ISO to disc twice, and twice (using unetbootin and universal usb installer) i have put the image on a USB stick.
I've redownloaded it on two occasions.

Once the loading screen finishes, all that happens is that i get a mouse cursor and a grey bar at the top. It doesn't respond to anything i do with my mouse. 
I'm assuming there's supposed to be a GUI, but i see no such thing.

Motherboard: Lanparty DK P45-T2RS
Graphics: Nvidia GTX295.
Harddrive: Corsair SSD force series 40GB. Problem occurs when installing to regular SATA harddrive too.

Am i just making a stupid mistake, or have i missed something in the hardware section like the MoBo being incompatible?

---

### Post by Quackers on 2011-01-31
Welcome to UF :-)
Whilst booting from the live usb, you should see a purple screen with a little man graphic at the bottom. Press any key at this screen and then choose language and you should get a screen with some options. Choose "check cd for errors" even though you're using a usb key. If that checks out ok, press F6 and you should get more options. One of those options should be "nomodeset", try using that option and see if things progress.

---

### Post by Hallstein on 2011-02-01
@Quackers
Solved my problem. Thank you!

---

### Post by Bucky Ball on 2011-02-01
Please mark thread as solved from 'Thread Tools'. ;)

Job well (and quickly) done!

---

### Post by Quackers on 2011-02-01
Glad to hear it :-)
If you run Additional Drivers and find a video card driver you shouldn't need to use nomodeset again. If you don't find a driver and you need to make nomodeset a permanent boot argument, see below

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

