---
title: "Hardy online upgrade renders system unbootable"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by erlenddavidson on 2008-04-24
My parents have a preinstall Dell Ubuntu system.  Today they decided to do the Gutsy -> Hardy upgrade.  It seems to have rendered their system unbootable.

On bootup, the usual grug loading stage 2 appears followed by the Ubuntu startup screen (with logo).

However the progress bar bounces back and forth, instead of proceeding from the left to the right.  Shortly afterwards the error:
```

ata2.00: exception Emask 0x0 SAct 0x0 action 0x2 frozen
ata2.00: cmd a0/00:00:00:24:00/00:00:00:00/a0 tag 0 pio 36 in
ata2.00: status [ DRDY ]

```

I have my parents trained to use 
Alt+SysRq+R
to reboot the system when these things happen.  From what they tell me *sometimes* it works if you do that.

Assistance would be very much appreciated, please!

---

### Post by Patsoe on 2008-04-24
Looks a lot like this bug report: 
[https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25](https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25)

I guess it's tricky to blacklist any drivers if you can't get into the system though. There's a chance you could attempt such a thing from a rescue-cd. You might want really to wait for a more expert opinion though!!

---

### Post by Patsoe on 2008-04-24
Accidentally ran into someone on a Dutch forum mentioning a "pci=nomsi" boot option because the update to hardy had broken his sata-controller driver. Had to think of your case... worth trying?
See also [http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html](http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html) which seems mostly unrelated but mentions this boot parameter.

And in case you're wondering what that does: [http://lwn.net/Articles/44139/](http://lwn.net/Articles/44139/)

---

