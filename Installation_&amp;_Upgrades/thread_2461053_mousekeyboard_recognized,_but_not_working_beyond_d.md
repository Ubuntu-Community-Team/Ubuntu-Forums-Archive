---
title: "mouse/keyboard recognized, but not working beyond dongle."
date: 2021-04-23
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2021-04-23
I have had a wireless mouse/keyboard that was working great for the past couple of years.  
Then I attempted to move to a never version of Python3.10
I was able to get this to work, but then a few days later I noticed that my wireless keyboard/mouse stopped working.

SO I thought perhaps bad peripheral.  
Ordered a new wireless dongle with keyboard/mouse.  
Didn't work.
Worried that something wrong with the motherboard - that would be terrible.
BUT it can be used during boot.... Just not in Ubuntu 20.10.

SO I then upgraded to 20.10.
Still doesn't work,
BUT when I run lsusb, I see the dongle:
[B]  Bus 001 Device 004: ID 25a7:fa67 Areson Technology Corp 2.4G Receiver

So what else can I use to debug this.  The hardware is good, but somehow neither the mouse or the keyboard work.

On another machine Ubuntu 20.10 - all is good.  

What is another step to trace the failure???

Thanks for you help.
[/B]After hunting and pecking and discovering an old bug where turning bluetooth off/on in settings, where bluetooth stayed off,
I found that one must reboot to remove stale data.
NOW all works as expected.  It only took 2 days, and complicated by a failing laptop.
[B]SO if you can't get wireless mouse/keyboard set not working.  
make sure bluetooth is on, and reboot and check.
I had to do  '[/B][COLOR=var(--black-800)][FONT=Consolas]sudo /etc/init.d/bluetooth start' at the command line to insure the bluetooth is powered on.
[/FONT][/COLOR][B]Strange in the wireless dongle related to the mouse/keyboard doesn't seem to have anything to do with bluetooth, but go figure.

Hopefully this will help another.

[/B]

---

