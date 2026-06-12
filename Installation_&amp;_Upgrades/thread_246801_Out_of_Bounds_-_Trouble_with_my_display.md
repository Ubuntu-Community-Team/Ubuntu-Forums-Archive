---
title: "Out of Bounds - Trouble with my display"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by Ray901 on 2006-08-29
I'm using the LiveCD, but it appears that Ubuntu does not recognise my monitor (or maybe my video card). I just see a monitor msg saying "Out of Bounds".

I have tried to reconfigure xserver with "sudo dpkg-reconfigure xserver-xorg", but after applying the settings I get the message on my monitor saying "Out of Bounds" again - which I think is talking about the refresh rate (and I did set the rate to 60). This is a monitor message not a Ubuntu msg.

Question: During the configuration of xserver I am prompted to "Specify the BusID of the video card" - I let it stay at the default, but is this something I should change, if I should try changing it where do I find out that info for my card/s?

My monitor is a ViewSonic VP2030b 20 inch LCD. The refresh rate is 50-60 hz.

It might also be my cards maybe? I have two NVidia 7900s hooked up with SLI - though I don't care if Ubuntu only uses one of them.

Any info would be appreciated.

cheers

---

### Post by orb9220 on 2006-08-29
Yes it looks like your dual sli cards are way above what ubuntu is expecting.

You may try to choose the second option at boot safe graphics something or rather.

Good Luck!

---

### Post by yetanothername on 2006-08-30
Thanks Orb,

I am now thinking that the 'Out of Bounds' msg might have something to do with the placement of the screen on the monitor. 

I will try borrowing an older crt monitor and try that - if it works then I'll download the nvidia drivers, install them and then reconnect my new monitor.

If this is because of the SLI - not sure what I will do. (It might be expecting two monitors as there are two cards and is maybe placing the screen on the monitor that does not exist)

---

