---
title: "Hypthetical install - Dapper server on 256MB compact flash"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by ocdude on 2007-02-02
Okay, I am posing a hypothetical question here. 

I like Ubuntu's apt system and I want to install a ridiculously small version of Ubuntu onto a compact flash card that has 256MB. Starting from a server install, I want to have some form of X, possibly with fluxbox and Gtk libraries. I know DSL is out there, but I don't really like how long it takes for stuff to get approved to Debian's repositories (DSL installs as debian, in case anyone was wondering).

The purpose of this would be to have a functioning, light weight system that ran completely off of the flash card so I can convert an old laptop (using a converter for the flash card to the laptop's HD port) into a picture frame or some other "embedded" type device, while having the flexibility to use it as a lightweight "coffee-tabletop" machine.

Is this even possible?

---

### Post by jaripetteri on 2007-03-18
256MB might be a bit too small but you can always try. I have 2GB CF card on my T23 on ide bus with CF to IDE adapter where HDD should be. And its working fine. Not that much faster that I expect but at least it is silent. I have Ubuntu Desktop on that with MythTV and that Thinkpad is my bedroom TV/multimedia player. 

Only problem is that there are limited numbers of disk writes that CF can handle until it gets corrupted. I'm currently looking for the way to disable all log writings to minimize disk writes.

I used [this]("http://www.ubuntuforums.org/showthread.php?t=204842&highlight=compact+flash+install").  

For Ubuntu desktop I need to first install it on HDD and then uninstall packages what I do not need to get it small enough to fit on 2GB. Then I copy all to CF and rewrite grub with livecd to make CF able to boot. I will make back up of that install and if card gets corrupted I can easily at least make another one. no idea how long that might last anyway... 

Xubuntu can be installed directly on 2GB CF but somehow I couldn't get MythTV run smoothly on that one.

---

