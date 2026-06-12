---
title: "No Wireless Connection (or, Not Exactly Plug-n-Play Yet...)"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by MinutiaeMan on 2005-07-23
I've had a very frustrating time installing Ubuntu so far.  First, I'd already pre-partitioned my hard drive to have two volumes, and I'd also installed Mac OS X (v10.3) on the first partition, but I couldn't get the installer to let me pick the right volume -- I ended up having to erase the entire hard drive and let Ubuntu do whatever it wanted. (The obscure instructions didn't help either, at that stage. I could've sworn I had things chosen right, but it wouldn't let me continue.)

Now, it seems that things are up and running, but I'm completely unable to create a wireless network connection.  I've poked around and around, and everything I've read said I've made the appropriate configurations.

BUT... I've come across [this thread](http://ubuntuforums.org/showthread.php?t=42821) which indicates that I might not be able to connect to a wireless network that is powered by an Apple Airport Express/Extreme base station.

My computer is an Apple iBook G3/600MHz, using an original Airport card plugged into the guts of the machine.  My family's network is an Airport Express station, and it's using 128-bit WEP encryption.

So, is this anything I can fix with some configuration changes, or am I pretty much stuck with an un-networkable Linux install?

---

### Post by WildTangent on 2005-07-24
im not much a wireless expert and i dont think ill be much help, but i hear people mentioning something called ndiswrapper when talking about non-functional wireless ;) try searching around for that.

-Wild

---

### Post by majikstreet on 2005-07-24
Hi,
One word: Ndiswrapper.

I am *NOT* sure if an Airport card will work with ndiswrapper, but I don't see why not. Have you used it with Windows?

I can help you with installing ndiswrapper and installing drivers.

One thing that is a little odd about ndiswrapper, is that you use the *Windows* drivers for linux.

If you can find windows drivers for your card, I can help.

(I checked on the website for another driver with a gigantic list of cards and I saw two apple cards on there.)

I hope you can find the windows drivers for the card!

majikstreet

---

### Post by MinutiaeMan on 2005-07-25
[QUOTE=majikstreet]Hi,
One word: Ndiswrapper.

I am *NOT* sure if an Airport card will work with ndiswrapper, but I don't see why not. Have you used it with Windows?

I can help you with installing ndiswrapper and installing drivers.

One thing that is a little odd about ndiswrapper, is that you use the *Windows* drivers for linux.

If you can find windows drivers for your card, I can help.

(I checked on the website for another driver with a gigantic list of cards and I saw two apple cards on there.)

I hope you can find the windows drivers for the card!

majikstreet[/QUOTE]
 majikstreet, my computer is entirely Apple hardware -- the iBook, the Airport card, everything. I can't use a Windows driver for it. ;)

---

### Post by Ken.Lank on 2005-07-25
[QUOTE=MinutiaeMan]
BUT... I've come across [this thread]("http://ubuntuforums.org/showthread.php?t=42821") which indicates that I might not be able to connect to a wireless network that is powered by an Apple Airport Express/Extreme base station.
[/QUOTE]

MinuteMan,

I am able to get my intel based laptop connected to my Airport Extreme/Express network (I have the Express set up to act as a repeater) under ubunto,  so you should be able to make the connection.

From what I read the there are no drivers for the AirPort Extreme card on the laptop side (which you don't have).  I have not attempted to load ubuntu on my PowerBook (or ever plan to as I see no reason to move away from OSX).

Were you able to connect to an "open" network?

Ken

---

### Post by MinutiaeMan on 2005-07-25
[QUOTE=Ken.Lank]MinuteMan,

I am able to get my intel based laptop connected to my Airport Extreme/Express network (I have the Express set up to act as a repeater) under ubunto,  so you should be able to make the connection.

From what I read the there are no drivers for the AirPort Extreme card on the laptop side (which you don't have).  I have not attempted to load ubuntu on my PowerBook (or ever plan to as I see no reason to move away from OSX).

Were you able to connect to an "open" network?

Ken[/QUOTE]
 Ken, I haven't tried that yet -- mainly because I try to stay away from networks I don't own when possible. But I suppose that a quick test would be a good idea. ;) I'll try it this evening -- right now, I've got to leave for work.

---

### Post by newbie2 on 2005-07-25
Linux scripts make wireless management a snap
[http://www.osdir.com/Article6544.phtml](http://www.osdir.com/Article6544.phtml)
[http://www-128.ibm.com/developerworks/linux/library/wi-wiisp.html?ca=dgr-lnxw01BuildISP](http://www-128.ibm.com/developerworks/linux/library/wi-wiisp.html?ca=dgr-lnxw01BuildISP)
[http://linux.slashdot.org/linux/05/07/25/0538217.shtml?tid=193&tid=106](http://linux.slashdot.org/linux/05/07/25/0538217.shtml?tid=193&tid=106)

---

### Post by MinutiaeMan on 2005-07-27
Okay, it took me a reinstall (although the wireless problem wasn't the reason I was reinstalling, my problem with the partitioning was the main cause), but I tried taking a closer look at the wireless networking configuration options.  It was a bit of a pain in the rear, but it turned out that the problems were (1) that our Airport Express isn't configured to broadcast itself, and (2) Ubuntu didn't give an immediate, obvious option for me to give it the name of the network I was looking for. I had to let it try, fail, and ask for input before I could try doing things manually. (I don't even remember exactly what I did now, I just know it worked. And I didn't know it worked until I'd finished the install and reboot and launched Firefox.)

Anyway, thanks for the tips -- it helped in that I knew it *should* work, so I dug around more to find how to configure things.

(Insert generic rambling about obscure Linux installers and limited documentation here.  I know, I know, it's still growing. ;))

---

### Post by majikstreet on 2005-07-27
[QUOTE=MinutiaeMan]Okay, it took me a reinstall (although the wireless problem wasn't the reason I was reinstalling, my problem with the partitioning was the main cause), but I tried taking a closer look at the wireless networking configuration options.  It was a bit of a pain in the rear, but it turned out that the problems were (1) that our Airport Express isn't configured to broadcast itself, and (2) Ubuntu didn't give an immediate, obvious option for me to give it the name of the network I was looking for. I had to let it try, fail, and ask for input before I could try doing things manually. (I don't even remember exactly what I did now, I just know it worked. And I didn't know it worked until I'd finished the install and reboot and launched Firefox.)

Anyway, thanks for the tips -- it helped in that I knew it *should* work, so I dug around more to find how to configure things.

(Insert generic rambling about obscure Linux installers and limited documentation here.  I know, I know, it's still growing. ;))[/QUOTE]
 manual configuration is much more flexible :P

---

