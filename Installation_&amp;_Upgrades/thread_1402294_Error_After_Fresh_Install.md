---
title: "Error After Fresh Install"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by PCHome on 2010-02-09
I'm trying to install Ubuntu 9.10 on a friend's laptop (new hard drive, completely fresh install) but after installation and required reboot, it gives an error:

[INDENT]error: no such device: e1475a08-9d33-405c-9826-a25102c0b48b

Failed to boot default entries.

Press any key to continue...[/INDENT]

Pressing a key does nothing so it is necessary to physically shut down the system by powering it off and restarting it. When it restarts. Grub's menu comes up but the arrow keys do not allow any selections to be made and pressing Enter does nothing either. It just sits there.

I hope someone can help! I am an Ubuntu user myself and have installed it numerous times but have never experienced this problem before.

Don

---

### Post by NightwishFan on 2010-02-09
Try using another keyboard for GRUB. If that does not work, follow some of the advice here that applies to you.
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

The error above seems to me like a required disk drive was misplaced.

---

### Post by PCHome on 2010-02-09
A different keyboard was my first thought too but it made no difference. Interestingly the built-in keyboard has no problems at all when booting from and running a LiveCD.

I've installed Ubuntu on several other HP laptops and never had any problems but then those were older versions of Ubuntu. I've had lots of installation problems with 9.10 and with Grub2 so maybe I need to install an older version. In the meantime, I'll see if your link provides any clues. Thanks for the reply.

Don

---

### Post by PCHome on 2010-02-09
Here's an update in case anyone else has a similar problem. It turns out that the device in question is the hard drive, which is a Western Digital 250GB Scorpio Blue. The LiveCD had no issues with it but apparently it is too large to install Ubuntu onto so I repartitioned it to 65GB and after that, Ubuntu installed and boots up perfectly.

If the size of the drive is the main problem, it might be a good idea if the Ubuntu installer would give a message up front! It would have saved days of struggling.

Don

---

### Post by NightwishFan on 2010-02-10
I never heard of a drive being too large. My drive is nearly that size.

---

### Post by murderslastcrow on 2010-02-10
I might have something to add- I don't know of a hard drive too large to install on, but I DO know of a recent case where we had a hard drive that couldn't boot from an OS that was too far from the front of the hard drive. As in, it couldn't boot with any files further than 10 GB up the hard drive.

This was unfortunate since it was a dual-boot setup, so we had to find another way to boot from Linux while bypassing the limitations of the BIOS.

However, considering the age of the laptop, this is unlikely. I sincerely doubt the hard drive was too large, but if it works it works. It would be extremely helpful if you could report this as a BUG, provided you have specific information about the hard drive in question.

---

### Post by theozzlives on 2010-02-10
I had that problem with an older computer, I had to keep my / 10 GB and place it at the front of the drive. That was a BIOS issue, however.

---

