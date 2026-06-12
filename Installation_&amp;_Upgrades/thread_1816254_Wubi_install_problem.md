---
title: "Wubi install problem"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by stickylittleleaves on 2011-08-01
I just tried to install the newest version of Xubuntu on my Dell Inspiron 2650 (which has 256 MB of RAM) using Wubi. When I ran Wubi, it said that "only 254 MB of RAM is available", which struck me as strange since System Properties says that my computer has 256. I decided to give it a go anyway.

The installation went on without a problem until I restarted my computer. I selected 'Xubuntu' from the OS selection menu. There was a countdown from 5, as well as some text about hitting 'Esc' for alternate installation modes. When the countdown reached '0', a blinking underscore appeared on the line beneath, and nothing else loaded, even after I waited for a long time.

I also tried safe graphics mode, and a lot of text started loading, but froze at:

```
[ 0.183659] pci 0000:00:1e.0: setting latency timer to 64
```

I'm thinking that the root of the problem is that only 254 MB of RAM was available on my computer, but I'm not sure. 
Please help!

(also, I'm completely new to Linux so I don't know a whole lot of technical terms)

---

### Post by bcbc on 2011-08-01
It could be the ram. The ubuntu installer ubiquity requires 256MB ram, though you are pretty close. It could also be a hardware issue.

If you install it direct to partition (not with Wubi) you can use the alternate installer and that requires much less RAM. Once installed Xubuntu can run on 192MB min but they recommend min 256MB.

---

### Post by stickylittleleaves on 2011-08-02
I tried using the alternate installer, and got to the menu with the Xubuntu logo and 'Install Xubuntu', 'Test CD for defects', etc.

When selected 'Install Xubuntu', I heard the CD-ROM drive starting up, but I only got a completely black screen (with no cursor). Then the CD-ROM drive stopped. The same happened when I tried 'Test CD for defects' and 'Rescue a broken system'.

'Test memory' worked, though. When 'Pass' was 100%, it said that 'pass is complete, press [ESC]', etc.

'Boot from first hard disk' also worked.

---

