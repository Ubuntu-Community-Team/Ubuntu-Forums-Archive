---
title: "HDMI Installation"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by andyd34 on 2010-02-14
I have recently purchased a base unit off ebay, the unit has no monitor and is connected to a philips 42" tv. The ubuntu desktop cd will boot and I can select the language but when the set up initialises the screen goes blank I can only assume its because the HDMI is not set up, I can install the server edition without any issues and it wouks fine but I want a GUI as I am reasonably new to linux and only really want it for web developement. The graphics card is an ATI Radeon HD 2400 series.

Is their anyway I can install a ubuntu GUI on this?? or maybe configure the graphics card under the server set up then install the gnome GUI on top of it.

Any suggestions would be much appreciated

Thanks

---

### Post by MooPi on 2010-02-14
I don't remember if I had any issues while installing my system but I had a similar setup not to long ago. I have a 40' LCD TV that used the HDMI video out to connect to my computer. ATI 3450 video card handled it fine, but the blue-ray stuttered and couldn't use it for LInux. Can you try the install on a smaller monitor first to check if install will continue ?

---

### Post by andyd34 on 2010-02-14
i dont have a monitor anymore as i got rid of them, just have this laptop now but wanted to set up a base unit for web development only. I dont really want to go out and buy a monitor just to install the GUI thats why i asked if the graphics card could be configured from within the server edition then install the GUI over it.

Thanks for your reply anyway

---

### Post by MooPi on 2010-02-14
If you can , try the Ubuntu alternate install CD. It's not a Live CD and can only be used for installation. Uses less overhead and may finish for you. As I pointed out before the HDMI out can work it's just a matter if your card can handle the large display. How much memory does the card hold ? Another alternative would be the Minimal install Cd but the interface is similar to the server install CD. I'm sorry but you can install a desktop over the server installation. Try > sudo apt-get install ubuntu-desktop

---

### Post by andyd34 on 2010-02-14
The box is a quad Q6600 2.4ghz with 8gb ram, 1tb sata hdd, the graphics card has 1gb of ram. At the moment I have vista installed on it with xampp but want to put lamp on it to set it up the same as my hosting company.

It works fine with vista so ubuntu shouldn't be an issue as long as i can get the set up completed

---

### Post by jken146 on 2010-02-14
The live CD doesn't work all that well with some graphics cards. You need to use the Alternate CD to install.

---

### Post by andyd34 on 2010-02-15
Well after downloading the Alternate CD and burning it to disk I thought that would solve my problems how wrong I was :x

After a few blank screens I decided to try the F4 option of installing under safe graphics mode and low and behold that seemed to get the display sorted. I thought i'd cracked it, I followed the steps and set the language and time zone and even type in a few words for it to auto select the keyboard. The next step was to partition my hard disk (SATA 1TB). Guess what, turns out according to the installation i didnt have one.

I decided to give up on Ubuntu 9.10 desktop i386. Out of curiosity I decided to try Ubuntu 8.1 desktop instead and try installing under safe graphics mode(F4) and to my astonishment it worked, I even had a hard disk lol.

Anyway I would like to thank everyone for all their suggestion but it turns out if anyone else has the same trouble just press F4 unless your unstalling 9.10 with a SATA 1TB hdd because it wont find it

---

### Post by jken146 on 2010-02-15
That's weird.

---

