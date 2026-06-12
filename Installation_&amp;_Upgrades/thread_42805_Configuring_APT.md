---
title: "Configuring APT"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by Mr.Clark on 2005-06-19
Hi, first time Ubuntu user.

I've brushed with Mandriva before, but I wanted to use Ubuntu, partly for the compatibility with the particular WiFi card (Netgear WG311 v2) and partly because it's for my brother and I want it to be as easy as possible for him.

I follow the installer without problems until I get to:

```
-configuring apt...-
25%
Setting up primary installation repository
```

Then it hangs here indefinately.

I've downloaded the Live CD as well, but that seems to have Checksum errors. Both ISO images on my Windows box have the correct checksums.
I'm downloading the DVD as I write this, but if anyone can advise me, that would be appreciated :)

---

### Post by Mr.Clark on 2005-06-20
Ok, by indefinately, I can confirm that I left it overnight and still no change. There is no hard drive activity, and I don't think the CD is spinning. I can't eject it though. :?

---

### Post by blind0wl on 2005-06-20
As a guess, do you have the internet configured on that PC?  Could be the cause...

---

### Post by Mr.Clark on 2005-06-20
A few times the wireless card has picked up my network (I was really impressed with that!). Should I not have it configured on install? How do I do that?

I set the wireless as the primary network device, as I don't have any network cable long enough to get from the router to the ethernet port. Is this a problem?

Cheers

---

### Post by blind0wl on 2005-06-20
If I was you, and for purely testing purposes, I would plug an ethernet adapter instead of relying on your wireless.  Im not completely fluid with the installation process, but if its got anything to do with APT it probably wants some form of outside connection...

---

### Post by TeeJay on 2005-06-20
[QUOTE=Mr.Clark]Hi, first time Ubuntu user.

I've brushed with Mandriva before, but I wanted to use Ubuntu, partly for the compatibility with the particular WiFi card (Netgear WG311 v2) and partly because it's for my brother and I want it to be as easy as possible for him.

I follow the installer without problems until I get to:

```
-configuring apt...-
25%
Setting up primary installation repository
```

Then it hangs here indefinately.

I've downloaded the Live CD as well, but that seems to have Checksum errors. Both ISO images on my Windows box have the correct checksums.
I'm downloading the DVD as I write this, but if anyone can advise me, that would be appreciated :)[/QUOTE]

are you selecting " download software from the internet now" when installing, my system hung for a few hours when I tried that the first time I installed Ubuntu. I so try skipping that step.

---

### Post by Mr.Clark on 2005-06-20
[QUOTE=blind0wl]If I was you, and for purely testing purposes, I would plug an ethernet adapter instead of relying on your wireless.  Im not completely fluid with the installation process, but if its got anything to do with APT it probably wants some form of outside connection...[/QUOTE]
Ah! Excellent! Plugged the ethernet into the router (had to move a lot of stuff around to get the cable to reach) and it installed. :grin: 

Many thanks.

So... how do I get the wireless card working? I've disabled the ethernet, enabled the Wifi, it found the network name, I selected DHCP, but it doesn't seem to pick up an IP address.

If you guys can help me get on the internet with this, I can hand the PC off to my brother, fully working.

Anyone seen this before? :-?

---

### Post by blind0wl on 2005-06-20
Do you have any settings like WEP that you havent configured?  Entered the SSID?

---

### Post by Mr.Clark on 2005-06-21
The GUI picks up the SSID, and I disabled WEP and MAC Address filtering on the router to try and make it as easy as possible to connect.

I know that is is possible, as it picked up the wifi on install once or twice, but those installs never completed.

EDIT:
I followed the instructions on [this page](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Ubuntu) so am now running from ndiswrapper, but still no luck :(

What's the Ubuntu equivalent of ipconfig?

EDIT EDIT:
Um, bizzarely, with no explanation, it's started working... [IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG]

Now to get WEP active...

EDIT3: Ok, it doesn't seem to like WEP or MAC Filtering, but I can live with that.
Tonight: Get films working, update Firefox. Learn .tar.bz2 install files.

Thanks for your help guys![IMG]http://ubuntuforums.org/images/smilies/icon_mrgreen.gif[/IMG]

---

