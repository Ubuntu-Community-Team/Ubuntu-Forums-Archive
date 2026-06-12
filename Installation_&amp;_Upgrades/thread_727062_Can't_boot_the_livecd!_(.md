---
title: "Can't boot the livecd! :("
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Dinchamion on 2008-03-17
Heya,

I was finally getting ready to install 7.10 on my mother's computer, so I got my livecd and started doing my thing...

... except that the damn thing won't even boot up! :( It loads just fine until it comes to loading cupsd, then it just hangs there, doesn't respond to anything but a hard reset. I've tried adding noapic and apci=off to the boot options, first no change, second it now hangs at the loading hald phase.

It's not a very recent computer, so I decided to let it work, maybe it's just slow. But no, after 35 minutes (and counting) it still does nothing. The computer is not THAT old.

Any help would be appreciated, googling didn't work.

---

### Post by sandysandy on 2008-03-17
what r the computer specs

RAM, Processor ...

assuming live cd is 32 bit.

regards

---

### Post by Dinchamion on 2008-03-17
It's an Intel P4 1,8GHz with 1,5GB RAM, GeForce7600GS card. (What specs should I include?) Yes, it's a 32bit CD, and as I recall I once tried it out on this very same computer, and it didn't have any problems whatsoever. Not to mention I used the very same CD to install my system.

Meanwhile I tried out with a 6.06 and 5.04 install cd too, just to rule out drive error, the latter got into a loop with the users (I properly added a user, and it kept asking for password), the 6.06 booted into the graphical desktop, I ran the installer just fine, but when rebooting into the fresh system it crashes with the following:

```
Check root= bootorg cat /proc/cmdline
or missing modules, devices: cat/proc/modules ls dev

ALERT! /dev/disk/by-uid/verylongthinghere doesn't exist. ropping to a shell.
```

Which leads me to believe something is wrong, I just cannot figure out what. I tried googling the above message, and tried the solution (reinstalling grub), didn't help.

Meanwhile, 7.10 still doesn't work.

---

### Post by Peter09 on 2008-03-17
Worth providing the spec of the motherboard as well.

PC

---

### Post by Pumalite on 2008-03-17
Tell me if you are dual booting or Ubuntu alone.

---

### Post by Dinchamion on 2008-03-17
Ubuntu alone, no dualboot. The motherboard is an Abit SA7.

---

### Post by Pumalite on 2008-03-17
Looks like a bad burn. Your specs are OK. for a Live CD. I prefer to install with the Alternate CD.
Follow this guide: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, as 'image'

---

### Post by Dinchamion on 2008-03-17
> **Pumalite said:**
> Looks like a bad burn. Your specs are OK. for a Live CD. I prefer to install with the Alternate CD.
Follow this guide: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, as 'image'

It's the very official Ubuntu CD, ordered from shipit. But I'll try downloading the image and burning it myself, maybe I'm just unlucky. (But then again, I installed my own system from it, and a while back I tried the livecd on the computer in question -- didn't install Ubuntu that time --, and it worked fine.)

---

### Post by Pumalite on 2008-03-17
You might need the Alternate CD. Mark box below sign 'Start Download'
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Dinchamion on 2008-03-18
Update: I downloaded the alternate CD, install went fine. However, after finishing and rebooting, the system hangs when it gets to the point to load cupsd. (Same place, as before, only it now does it during a normal boot)

I'm getting crazy here, any ideas?

---

### Post by Pumalite on 2008-03-18
At the time of boot, at the blank screen; try this:
Ctrl+Alt+F! to get a command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver; then: startx

---

### Post by Dinchamion on 2008-03-18
I finally pinpointed the source of the problem: when I removed the pci wireless card, it booted up just fine.

So i have a whole another problem now. The card is brand new, Windows sees it and uses it perfectly, it IS vital to the system (who can live without internet these days? :P), and i just don't get why Ubuntu can't handle it?

I have a card from the very same manufacturer, different modell though, never had any problems. Weird, to say at least.

It's a TP-LINK TL-WN353G 54MB card by the way. I'm currently using an usb wireless adapter in that computer, but it has some annoying things I'd like to get rid of and use the pci card.

---

### Post by Caml_Craig on 2008-03-18
I know this seems like a dumb question, but have you tried a booting into safe mode? Alternatively, can you boot using your live CD again? If you can, then take a look at the cups config file /etc/cups/cupsd.conf and see if there is a problem with it? Can you post its contents here (assuming you can boot either in safe-mode or using the live CD)? Maybe its something simple related to this.

---

### Post by Peter09 on 2008-03-18
I have seen something like this before but it a very different configuration so it might not be applicable.

Try turning off your wireless router while you are booting the system - what happens?

PC

---

### Post by Tomatz on 2008-03-18
I

---

### Post by miketowninc on 2008-03-18
I have the same problem with nothing plugged in? My computer is slower but stilll.. I installed ubuntu with wubi and it worked there. Why not now?

---

