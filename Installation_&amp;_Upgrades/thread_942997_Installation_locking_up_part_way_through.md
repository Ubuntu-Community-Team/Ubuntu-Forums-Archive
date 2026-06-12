---
title: "Installation locking up part way through"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by johnsonsl on 2008-10-09
I am trying to install 8.04.1 on an older dell ispirion 2500 laptop.  I run the disk and select install and it gets to the point where it displays the brown screen with the bird and then freezes. That is all that is there and the mouse pointer wont move. It stays like this until the screen goes black. I hold the power button down and eventually the disk drive starts spinning at a high speed but it never really does anything.  I checked and the hashes were correct before i made the cd and I put the cd in another computer and it works just fine so what is the problem with this inspirion?

---

### Post by overdrank on 2008-10-09
> **johnsonsl said:**
> I am trying to install 8.04.1 on an older dell ispirion 2500 laptop.  I run the disk and select install and it gets to the point where it displays the brown screen with the bird and then freezes. That is all that is there and the mouse pointer wont move. It stays like this until the screen goes black. I hold the power button down and eventually the disk drive starts spinning at a high speed but it never really does anything.  I checked and the hashes were correct before i made the cd and I put the cd in another computer and it works just fine so what is the problem with this inspirion?

Hi and welcome, what are the specs of the system? 
You may try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add noapic. Removing the quiet splash will allow you to see any errors.

---

### Post by Drakoon on 2008-10-09
Hi Overdrank,

Well, I don't know about him, but I have kind of the same problem. In my case, the reading head of my CD drive is getting crazy, you can listen how it goes up and down in the disc...

I've tried what you said, and without the quiet splash and with the noapic I can see a lot of messages, such as: 

[47.823986] Driver 'sd' needs updating - please use bus_type methods

and

[47.82.8460] sda:<4>Driver 'sr' needs updating - please use bus_type methods

And then:

[47.914462] end_request: I/O, dev fd0, sector 0

at this point the installation stops for about 3 or 4 minutes, and then goes on with checking clocksource, registering unionfs 1.4 and a message about squashfs.

After that there's a lot of messages with [OK] at the right end of the line, and then I see again the image of my well known multicolor bird on a brown backgrounds... and the CD keeps spinning, the reader keeps going crazy. last time I've tried the installation (without the changes you've mentioned), it was still going on after 3 hours.

All of this tried in an old HP Omnibook XE3 crap, that is with a 1.06 GHz Intel Pentium III, 256 SDRAM and 20 Gb Hard disk

Thanks for the help (in case you can do something with this info!)

Edit: I must say, in case you haven't noticed, that I'm so new in Linux that I stink :)

---

