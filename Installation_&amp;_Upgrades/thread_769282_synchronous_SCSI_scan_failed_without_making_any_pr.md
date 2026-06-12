---
title: "synchronous SCSI scan failed without making any progress"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by bobonthenet on 2008-04-26
I'm having issues with an hardy upgrade on a DELL Inspiron 530.  Upon powering up the computer I get the black ubuntu loading screen with logo and the bar that goes back and forth.  This stays up for about 5 minutes or so.  From there the screen goes black and a bunch of stuff flashes on the screen too quickly for me to get it all down, although I don't think I missed anything important (hopefully).  Then the following repeats over and over, where # equals some number.

```
[ ###.######] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 Frozen
[ ###.######] ata2.00: cmd a0/00:00:0024:00/00:00:00:00/a0 tag 0 pio 36 in
[ ###.######] ata2.00: status: { DRDY ]

```

somewhere along the way the following is stuck in there before going on for an hour with the previous thing.

```
Warning: synchronous SCSI scan failed without making any progress,
```

I haven't a clue whats going on I've tried restarting a few times, 7.10 worked just fine.

*update*
I was able to enter into the grub loader screen, enter recovery mode, and run xfix.  After xfix does its thing I select resume normal boot and just like that everything boots fine.  Now the problem is that my Nvidia drivers are not enabled.  Enabling the Nvidia drivers takes me back to square one.  Where I have the same issues as before.

---

### Post by bobonthenet on 2008-04-26
*bump* and another update

restarting the computer without enabling the restricted drivers also gives the same problem I had initially mentioned.

---

### Post by k4sgt on 2008-07-12
Enter the BIOS and change the SATA setting from IDE to RAID.  This worked on my Inspiron 530.

---

### Post by Crossbow on 2009-10-20
I was having this exact same problem, so I changed the SATA to RAID as suggested, and it works now but it's still REEEEAAALLLY slow. After the bar sliding screen I get half a page of **"USB 8-1: device descriptor read/64, error -110"**

---

