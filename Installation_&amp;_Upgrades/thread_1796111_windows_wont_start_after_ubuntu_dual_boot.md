---
title: "windows wont start after ubuntu dual boot"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Alex715 on 2011-07-03
Hi everyone so im new to linux and everything and have never done a dualboot before but i have instaled ubuntu 10.10 (going to update to 11.04) and everything went as planed and i partioned the hard drive equally on the live cd installer. but now when i go run windows xp pro from the GRUB menu it boots with the xp loading bar for about 3 seconds the goes onto the windows bluescreen. Ive tried this about 5 times. Could somebody please help me out with plain english please not to technical linux stuff if possible as i am new to this. Thanks in advance.

---

### Post by in-dust-rial on 2011-07-03
hey

did you try to enter a save mode?

maybe there is an explicit error within the bluescreen?
if yes, google for it.



if this happend to me...

I would use the windows CD
to recover my windows installation.
afterwards I would follow a how-to to install 
linux on the windows boot-loader
or 
reinstall grub from live-cd.

how to recover windows is of cause dependent of the type of windows. 
most of the time it is enough to insert the CD and just use common sense :)

GOOD LUCK BUDDY!

---

### Post by Sef on 2011-07-03
From 10.10, Applications > Accessories > Terminal -

then copy and paste the following command:

```
sudo fdisk -l
```

Then copy and paste the results here.

---

