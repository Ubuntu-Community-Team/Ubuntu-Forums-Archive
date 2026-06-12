---
title: "Can I Uninstall Ubuntu but Keep &quot;Grub&quot;"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Wejdan on 2011-01-29
Hi,

Can I uninstall Ubuntu but keep grub??

the reason is that I have Ubuntu, Ubuntu Studio & Windows Vista .. so I want to keep vista, ubuntu studio and add the partition volume that currently has Ubuntu to Ubuntu Studio Partition but I'm concerned about "Grub"


thank you :)

---

### Post by mikewhatever on 2011-01-29
Yes, as long as you have a Linux partition, in fact, a /boot partition, grub can be used. You'll probably need to reinstall grub after removing the Ubuntu partition, which is fairly easy, just make sure you have a live cd/usb ready.

---

### Post by Wejdan on 2011-01-29
well, how do I unistall it?
is deleting the partition enough?
+
about the live CD/USB, ... I've googled that, didn't find a CD for Grub, would you plz explain a bit more...

p.s. im so worried cuz I removed linux partition before and got Grub removed too, I couldn;t fixed by any means, an so I had to reinstall ubuntu, then reinstall vista to have my notebook work as it used to

---

### Post by mikewhatever on 2011-01-29
Yep, deleting the partition is as far as it gets, as for the live cd, I meant the one with *buntu, presumably of the same version you want to keep. Reinstalling Grub is easy ([see how]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")), and if you ever face the situation of reinstalling everything just because of the bootloader, post here, using the live cd.

---

### Post by Wejdan on 2011-01-30
here is the issue
> Open a terminal by selecting *Applications, Accessories, Terminal* from the menu barhow would I do that if i cant log into the system?
unless i should've done that before shutting down?

---

### Post by mikewhatever on 2011-01-30
Reinstalling grub is done from the live cd.

---

