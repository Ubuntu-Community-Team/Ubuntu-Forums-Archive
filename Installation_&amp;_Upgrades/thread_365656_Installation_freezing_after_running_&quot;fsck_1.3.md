---
title: "Installation freezing after running &quot;fsck 1.39&quot;"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by brianfgonzalez on 2007-02-19
[IMG]http://i66.photobucket.com/albums/h280/brianfgonzalez/100_1476-1.jpg[/IMG]
This is the exact error that I see before the screen goes black.  This is the Laptop Im trying to load ubuntu too...
[http://www.linuxhardware.org/article.pl?sid=01/09/04/0135236&mode=thread](http://www.linuxhardware.org/article.pl?sid=01/09/04/0135236&mode=thread)
 

any help!!! is well appreciated.. THANKS!!

bri
[email]briangonzalez@gmail.com[/email]

---

### Post by bandie on 2007-02-20
the spec on the link you sent says 128mb ram? how much ram have you installed? Running the live CD with only 128 is too little, you need to use the alternate CD or xubuntu which will happily run in 64mb ish

---

### Post by brianfgonzalez on 2007-02-20
your right!.. i wish i could find a cheap place to buy some extra ram for this thing..
I found a way to install ubuntu using the alternate cd like you said.. thanks!

[http://ubuntuforums.org/showthread.php?p=1514405#post1514405](http://ubuntuforums.org/showthread.php?p=1514405#post1514405)

---

### Post by PlaHPoy on 2007-02-28
I am getting this SAME problem, and I have 512 ram. amd64, 60gb hd.  Any other ideas?

---

### Post by lawrens on 2007-03-04
I'm also having this exact same problem minus the module error in the screenshot, it just hangs with no hdd loading or anything.
However alt-ctrl-del works during the hang, and screen would even go dim when I leave it sitting for a while, alt-ctrl-del interrupts whatever process it was having with a message init: rcS process (3750) killed by signal 15 or something like that.

Doing that allows me to boot the live dvd and even lets me install ubuntu, but after installation, when booting the os off my hdd I keep getting the same fsck 1.39 screen every boot, ctrl-alt-del takes me into xwindows, but I could not find the culprit to the problem, this is my first time installing ubuntu, I couldn't find anything strange other than usb errors and a few wacom directory error which I think shouldn't be the problems (unplugged my wacom, all usb devices other than keyboard during dvd boot). 

I have 2gb ram, I'm trying to install ubuntu on a dell m1710 laptop, I've looked at other posts regarding m1710 but it seems like no one are getting this problem and infact saying it works right out of the box.

Any ideas?

Update: Sorry about that, I found out the problem to be my wifi wireless card, I tried unplugging all my usbs, disabled/enabled my bluetooth, and finally disabled my wifi and found it to be the problem, it boots fine now in both the dvd and the os boots fine too after install, I haven't really looked at howtos and tutorials yet on the matter, but it might've already been a known problem, since I'm pretty sure I've seen howtos around on getting the wifi card to work, I didn't thought it would cause a problem for leaving it not configured, but I'll look into that later.

One interesting thing is that the same wifi card on my m1710 was causing a system lag problem on my suse10.2 installation, it had the newest driver from the repository but since I hooked up my laptop through wired, I never bothered with it and uninstalled the driver, it never occur to me of trying the same on ubuntu =(

---

