---
title: "PLEASE HELP installation problems"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by capncrunch on 2008-01-24
okay, so before you read this, know that I have tried redownloading the ISO and burning a new livecd many times, im trying to install ubuntu 7.10 desktop edition,  32-bit, the ISO is called ubuntu-7.10-desktop-i386

So i wanted to take my old piece of **** desktop (2GHz, 255MB RAM, 115G HD, Intel) n put ubuntu on it so that i could actually use it, it was just sitting in a corner in my room. At first when i used a livecd and tried to start ubuntu, itd go to a login screen at which i didn't know the username or password. 

So naturally i asked my fulltime linux user friend, and he told me to try to use Kill Disk and then try again. so i backed up evrything i needed, ran kill disk off a boot cd, and it swiped my HD. then when i tried to run the ubuntu livecd, as soon as i turned my comp on it made an entire symphony of beeps for about a minute. proceeding that, it displayed a "Master Hard Disk Error, press <F4> for menu" so of course i press F4. this brings me to a BIOS setup utility. all seems fine, boot config is fine, set up to run off of livecd. so i exit the menu

When i exit the menu, it goes to the ubuntu loading animation screen, then to a command prompt looking page. [IMG]http://i30.tinypic.com/2hgwnxx.png[/IMG]
No matter what cd i use, even after redownloading ISO, and trying OEM installation or start and install, they all result in this page. Can somebody please help me out? this is EXTREMELY frustrating

---

### Post by Happy_Man on 2008-01-24
> **capncrunch said:**
> okay, so before you read this, know that I have tried redownloading the ISO and burning a new livecd many times, im trying to install ubuntu 7.10 desktop edition,  32-bit, the ISO is called ubuntu-7.10-desktop-i386

So i wanted to take my old piece of **** desktop (2GHz, 255MB RAM, 115G HD, Intel) n put ubuntu on it so that i could actually use it, it was just sitting in a corner in my room. At first when i used a livecd and tried to start ubuntu, itd go to a login screen at which i didn't know the username or password. 

So naturally i asked my fulltime linux user friend, and he told me to try to use Kill Disk and then try again. so i backed up evrything i needed, ran kill disk off a boot cd, and it swiped my HD. then when i tried to run the ubuntu livecd, as soon as i turned my comp on it made an entire symphony of beeps for about a minute. proceeding that, it displayed a "Master Hard Disk Error, press <F4> for menu" so of course i press F4. this brings me to a BIOS setup utility. all seems fine, boot config is fine, set up to run off of livecd. so i exit the menu

When i exit the menu, it goes to the ubuntu loading animation screen, then to a command prompt looking page. [IMG]http://i30.tinypic.com/2hgwnxx.png[/IMG]
No matter what cd i use, even after redownloading ISO, and trying OEM installation or start and install, they all result in this page. Can somebody please help me out? this is EXTREMELY frustrating

Try running "startx" (w/o quotes) and if everything's all right, it should load up a GUI for you.

---

### Post by capncrunch on 2008-01-24
i ran "startx" and "sudo startx" both made the screen black and white fuzz, then sum random colored bars for about 3 seconds, then it went right back  to the command prompt screen from b4. it's the first sign of anything graphical ive seen yet, but it didn't work =( any other suggestions?

---

### Post by capncrunch on 2008-01-24
i just reburned a new cd, even on a new brand of cd, still doing it. here's a screen of what it looks like after i run "startx" and the screen glitches out for a second then goes back to the command prompt

[IMG]http://i25.tinypic.com/zwtiq.png[/IMG]

---

### Post by stevescripts on 2008-01-24
Please see the following: [http://www.easy-ubuntu-linux.com/ubuntu-system-requirements.html](http://www.easy-ubuntu-linux.com/ubuntu-system-requirements.html)

Looks like your system doesnt have enough ram.

Maybe try Xubuntu?

Hope this helps.

Steve

---

### Post by capncrunch on 2008-01-25
oh my god, the requirements are 256MB RAM... i have 255! ahhhhh im one MB away. ill either have to buy some more RAM, or try Xubuntu. are there any advantages or disadvantages to Xubuntu? and what is the difference between ubuntu and Xubuntu? 

One of the main reasons i want ubuntu is because i have a mac, and i love gaming but mac doenst have much to offer. ubuntu has a lil bit more than mac as far as gaming goes (and also, linux is kickass). so what're youre thots regarding xubuntu or ubuntu on gaming?

---

### Post by stevescripts on 2008-01-25
FWIW - 255mb of ram is ... unusual ... to say the least.

As far as gaming goes, I am the wrong guy.  I do virtually no gaming.

I have never had a need for xubuntu, but based on the few weeks I have
been using ubuntu, I would *certainly* give it a shot on your box.

Steve

---

### Post by capncrunch on 2008-01-25
haha yes 255 is pretty damn random. and alright, im excited to install it and try it out for myself!! i cant install it until monday, but i look forward to it :) ill msg back if sumthin goes wrong again

---

### Post by capncrunch on 2008-01-28
okay so i tried xubuntu,. i put in the livecd, it loads up the cd menu n i choose "start or install xubuntu", it runs fine but without any top/bottom bar, just a desktop and icons. and when i try to double click the "install" icon it takes 30 minutes or so to load the first menu of 7. any suggestions?

---

### Post by digital_exhaust on 2008-01-28
> **capncrunch said:**
> okay so i tried xubuntu,. i put in the livecd, it loads up the cd menu n i choose "start or install xubuntu", it runs fine but without any top/bottom bar, just a desktop and icons. and when i try to double click the "install" icon it takes 30 minutes or so to load the first menu of 7. any suggestions?

Use the [alternate install cd]("http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.10/release/").

---

### Post by capncrunch on 2008-01-29
will do. =D

---

