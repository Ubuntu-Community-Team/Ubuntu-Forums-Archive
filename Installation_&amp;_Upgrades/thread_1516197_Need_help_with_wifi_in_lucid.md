---
title: "Need help with wifi in lucid"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by dcates1 on 2010-06-23
I installed Lucid and have it pretty well configured. Wifi actually worked right out of the box( previous installs i had to use ndiswrapper)

Here's the problem, even though it works it is slowwwww and doesn't play well.

What I need help with is finding which driver is actually loaded so i can blacklist it. Then I will run ndiswrapper with the XP drivers that worked fairly well in previous versions.

I tried device-manager(directions from the Begining Ubuntu Guide) , I can see my netgear WN 111v2 usb dongle, but I can't find the driver that was installed for it.

Thanks Dan

---

### Post by darkod on 2010-06-23
To find out your chipset, first use:

lsusb

Write down the chipset and the hex codes which mean manufacturer and product code like xxxx:yyyy.

Then search online for bext solution about that chipset. There might be better drivers already within Lucid, I don't think ndiswrapper is needed any more.

Anyway, if you still want to proceed with installing by ndiswrapper, after finding your chipset usually online there will be information which driver (module) is used by default by Lucid. To make sure this is the driver loading in your case, you can check if it's loaded with:

lsmod grep|drivername

PS. I'm not sure if you needed sudo for the above commands.

---

### Post by Bucky Ball on 2010-06-23
Plug in an ethernet cable, make sure you're online, then plug in your dongle. Then update:

```
sudo apt-get update
```

Then check System->Admin->Hardware Drivers. Anything in there?

---

### Post by dcates1 on 2010-06-23
I've already done the updates andnothing showed up.

If I can find out which one Ubuntu loaded, I can blacklist it. 

Then i can use ndiswrapper(I've already got it and the drivers ready).

Dan

---

### Post by Bucky Ball on 2010-06-23
As you wish but ndiswrapper? Good luck with that. I would try installing wicd instead of network manager first and see if that helps before resorting to the aging and largely superseded ndiswrapper. Network manager can be c**p on some machines and wicd has my card running a treat.

---

