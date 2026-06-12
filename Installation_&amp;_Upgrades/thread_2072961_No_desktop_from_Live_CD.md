---
title: "No desktop from Live CD"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by ftella on 2012-10-18
Hi!

As my laptop is a bit old I'm trying to boot 12.10 from a USB stick using Plop. I saved the image to the stick using UNetbootin.
I have to use nolapic option when booting any linux compilation I've tried and so I did for 12.10. When it finishes booting I get to an empty screen with just the background and mouse arrow but no top or unity bar. Surprisingly I get a popup notification about available wireless connection. Right click has no effect, but I can hit CTRL+Alt+Supr and I get the window asking if I want to logout or cancel. If I logout I get to the login screen and now I can see the top bar with icons, clock, net, etc. I also can see the login box, and connect to my wireless typing the password.
If I try to login using "ubuntu" as user and no password I get to the same empty screen as before.

Any ideas?


Besides that, if I try to install, the process stalls when I hit continue at the screen where it checks if you have internet connection, 4.8GB of free space, and the laptop is plugged. I can see the top bar there.

---

### Post by ftella on 2012-10-22
Does anybody knows how I could dig for more information?

My graphic card is a Nvidia Geforce4 488 go for laptops.

Many thanks!

---

### Post by ftella on 2012-11-15
Can anybody help with this? I'm having a similar problem installing Elementary Luna new beta. I don't know what else I can try.

---

### Post by mastablasta on 2012-11-15
is the image good? are you sure everything loaded on login? 
 
what are the system specs?

---

### Post by ftella on 2012-11-15
I think the image is ok. Just re-downloaded right now to make sure, but it behaves the same way.

It's a Pentium IV 2666 GHz with 512 MB of RAM
The graphic card is a Nvidia Geforce 4 488 go (kind of rare maybe)
As a reminder I have to boot with nolapic option.


Got  some more info: If I hit Ctrl+Alt+T I can open a terminal window. It's  quite stripped of any decoration: no borders at all, just a grey bar on  top with white text (File Edit View Search Terminal Help), no minimize,  maximize or close buttons, and the black box for code at the bottom, no  borders at all also.

The good news are that I can type whatever, the bad news are that I don't know what to type. (I'm quite a newbee in linux).

Thanx a lot.

---

### Post by mastablasta on 2012-11-16
your RAM is too low for Ubutnu to play nicely. It should load but could load slow. Additionally Ubutnu uses 12.10 3Dacceleration, so if that is not supported for oyur card or if support is poor oyu will face problems. 
I suggest you try Xubuntu instead. It looks different to Ubuntu, but it is still very easy to use and the core system is the same as in Ubuntu (just a different desktop environment). 
 
Ubutnu might work if you install gnome fallback mode. but if you plan to use fallback mode then it's maybe better to just use Xubuntu. it will be faster and looks almost the same.
 
one other thing you could try (if you want to use Unity) is to install version 12.04 LTS (supported for 5 yeras) and then use Unity 2D (looks the same as 3D, but no hardware acceleration needed).
 
additionally some nvidia cards also need nomodeset boot parameter.

---

### Post by ftella on 2012-11-16
Thanks Mastablasta.

I have another drive where I have Mint installed and goes fine. I swap that drive for a smaller one to test other OSs, so it's not a big deal if I cannot make it work, but I like challenges.

So you think it could be due to my graphic card not supporting 3d acceleration... It could be that; I'm having similar problems with Elementary OS Luna Beta 1

Shouldn't fallback mode be activated automatically if the graphic card is not supported?

Can fallback mode be activated in LiveCD? Maybe it doesn't make much sense but...

Thanks.

---

