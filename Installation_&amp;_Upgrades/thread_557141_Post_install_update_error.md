---
title: "Post install update error"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by mr_finn on 2007-09-22
Hi all, I'm a complete beginner to Ubuntu and have installed Ubuntu Ultimate Gamer Edition on my desktop pc without much trouble other than just the learning curve to get everything working. I absolutely love it aswell btw, I dont know why I didnt do it before as it feels so good to let go of Microsoft...phew!

Anyway, I have just installed U U G Edition on my laptop, the install went ok but I am unable to update it and I get the following error message: ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I also got this error on my desktop pc so I tried installing only one update and that worked as did all of the others after the first one had taken.

Is there anything I can do to get this working.

I am very reluctant to put XP back on it.

Thanks for your attention.

: ]

---

### Post by Pumalite on 2007-09-22
Did you run:
sudo dpkg --configure -a

---

### Post by mr_finn on 2007-09-22
I just did and nothing happened. It just goes back to 'user@user-laptop:~$'

:/

Edit: Ok, it didnt seem to do anything but it is now updating itself so thanks mate for that 

: ]

---

### Post by Pumalite on 2007-09-22
You are welcome.

---

### Post by mr_finn on 2007-09-22
Cheers mate, however I have run into more and bigger problems now:

Ubuntu has stopped booting up altogether. WHen it was booting up there was an icon in the system tray and a popup telling me that it was using unsuported drivers.

I upgraded Ubuntu via the update icon on the desktop, then ran the sudo aptitude update, sudo aptitude upgrade, sudo aptitude dist-upgrade comands. 

Then ran Envy to install my grfx card drivers and rebooted, everything seemed ok at this point.

Then I followed this guide to set up beryl, just as I did on my desktop pc: [http://www.arsgeek.com/?p=1313](http://www.arsgeek.com/?p=1313)

And now I cannot boot up, it gets to the 'ubuntu' splash screen and a load of text starts to scroll down the screen and I land on a strange red white and blue screen with strange symbols around the edge and a message on screen which goes something like this after the details of build, release, etc: 

```
Module Loader present
Markers: (==) probed, (**) from config file, (++) default setting
               (++) from command line, (!!) notice, (II) informational,
               (WW) warning, (EE) error, (NI) not implemented. (??) unknown.
(==) Log file: "/user/log/Xorg.0.log", Time: today
(==) Using config file: "/etc/Xorg/X11/xorg.conf"
Parse error on line 119 of section device in file /etc/Xorg/X11/xorg.conf
              The option keyword requires 1 or 2 quoted strings to follow it.
Parse error on line 153 of section screen in file /etc/Xorg/X11/xorg.conf
The section keyword requires a quoted string to follow it
(EE) Problem parsing the config file
(EE) Error passing the config file

Fatal server error:
no screens found

```

I am try to install this on an Evesham Quest A420 laptop

Specs:
Processor: AMD Turion X2 TL-56 1.8GHz(x2) 
RAM: 1024MB DDR2
Hard Drive: 100GB Sata 
Screen: 17" TFT X-Bright 
Optical Drive: DVD±RW Double Layer 
Graphics: NVidia GeForce Go6100 256MB 
Wireless LAN: 802.11b/g 
Gigabit Ethernet 10/100/1000 
Built-In Stereo Speakers 
Firewire 
Express Card 
Flash Memory Card Reader (XD, SD, MMC, MS, MSpro)

I'm determined to get this working! :)

Any thoughts?

---

### Post by Pumalite on 2007-09-22
Do it all again, but leave the eyecandy to the kids.

---

### Post by mr_finn on 2007-09-22
Thats fair enough I guess, for now, but I was getting the notifications about unsuported drivers right from the beggining of the install so I suspect there may be more to it.

I will re-install however see what happens this time.

---

### Post by Pumalite on 2007-09-22
If you have trouble with the drivers; post back. Cheers.

---

### Post by mr_finn on 2007-09-22
Whe n I boot from disk I get:
```
pidof[3596]: cant't read sid from /proc/1/stat

pidof[3596]: cant't read sid from /proc/10/stat

pidof[3596]: cant't read sid from /proc/11/stat
```

Then lots of scrolling text before it lands on desktop.

?

---

### Post by Pumalite on 2007-09-22
Is this on boot after install finishes?

---

### Post by mr_finn on 2007-09-23
No, thats just booting from the disk before installation.

Edit: I have just completely re-installed it and on the first reboot after install it says:

loading grub....

Error 15

And just hangs there.

I must say that I'm beginning to feel a bit fried with all this and my XP disk is giving me a very enticing look right now.  

: ]

---

### Post by Pumalite on 2007-09-23
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

