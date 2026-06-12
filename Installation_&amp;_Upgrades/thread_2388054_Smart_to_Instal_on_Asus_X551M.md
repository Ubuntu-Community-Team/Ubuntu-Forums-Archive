---
title: "Smart to Instal on Asus X551M?"
date: 2018-03-27
forum: Installation &amp; Upgrades
---

### Post by sdansmith on 2018-03-27
Hello everyone! 

I'm a typical end user with just enough knowledge about Linux (mostly through messing around with Ubuntu) to be dangerous. I have an old Windows 8.1 machine that I'd like to repurpose as a Linux laptop (clean slate installation). Basic specs of my Asus X551M are:

[COLOR=#ffffff][FONT=&quot][/FONT][/COLOR][COLOR=#ffffff][FONT=&quot][/FONT][/COLOR][FONT=&quot]Intel® Bay Trail-M Quad Core Pentium N3520 Processor (2.16GHz)[/FONT][COLOR=#ffffff][FONT=&quot]
[/FONT][/COLOR]4GB Ram
500GB HHD (might upgrade to a spare SSD if it goes well the first time I try it)
Integrated graphics

What I'm most interested in knowing is if I should expect any hiccups like wifi that doesn't work, or not seeing a DVD drive. I can add more information, I just don't know what all I need to put in this.

Or if anyone has learned through trial and error that this is a bad computer to install on, please let me know so I don't mess up. I plan to do the installation on Saturday this week.

Thank you.
Dan

---

### Post by oldfred on 2018-03-28
Best to experiment with live installer, you may need a boot parameter.

There used to be some issues with Bay Trail system.

May be similar as issues are common by vendor & vendors UEFI which is uses on many systems.
 Asus x55u UEFI change to BIOS discuses boot keys esp & f2
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html) 

Now older issue:

 The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) 

Different brand, but Bay Trail needs boot parameter:

 Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162)

---

### Post by sdansmith on 2018-03-28
Thank you so much for offering your expertise. I'll read these and try a live installer. Can I assume that, if it works with a live installer, it will work as a full installation?

---

### Post by oldfred on 2018-03-28
It should.

Live installer in live mode is not as quick, but fully functional. But you cannot save settings or easy install additional drivers that sometime make it run a lot better.

---

### Post by sdansmith on 2018-03-29
Tried a live installer tonight and it worked! I did cheat a little and put in a blank SSD in the HDD slot, which meant it couldn't choose a Windows 8 option if it wanted to. Still a little surprised it didn't try anyway. Booted right to Ubuntu. I am ordering a new keyboard as the old one has broken keys, but then it's on to a full install. Thanks again for your help. So far, so good.

---

