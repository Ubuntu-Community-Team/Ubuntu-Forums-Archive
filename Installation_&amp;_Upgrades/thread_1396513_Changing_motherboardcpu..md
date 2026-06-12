---
title: "Changing motherboard/cpu."
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by frncz on 2010-02-02
Hi

I plan to change my motherboard and cpu. Will I need to reinstall karmic, or will the system recognize the hard disk installation?

Would there be any advantage to reinstall?

Thanks for the advice

Mike

---

### Post by Rhubarb on 2010-02-02
The few times I've done this, I've had very little problems doing so.
I would however make a backup of your important documents / data first.

To give you some history:  I currently install ubuntu server on my old laptop by taking the hard drive out, putting it into a generic computer, and install, then put the hard disk back into my old laptop.
I do this because my old laptop is unable to boot from USB, and has no optical drives.
The architectures of my old laptop and generic computers are very different.
The only problem I encountered that may be relevant to you, was that the LAN on the laptop is now configured as eth1 rather than eth0.  - This is generally not a problem for a desktop computer as the Network Manager will do its magic and all is well.

If your old CPU is 32bit, and presumably your new CPU will be 64bit, then you should seriously consider installing 64bit Ubuntu Karmic.  Some applications get a big speed improvement if you're running on a 64bit platform :)

---

### Post by frncz on 2010-02-08
Thanks

Mike

---

