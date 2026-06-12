---
title: "Update to 16.04 using live dvd, but want to revert"
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2017-02-09
I wanted to check out Ubuntu 16.04.1 and thought I'd done it all right, and set it up through the Live CD. But I want to quit 16.04 and revert to 14.04
I went through the steps, set it to a dual install. It split one of the partitions and proceeded. But I want to revert back to 14.04 - for a little while longer.
As I went through the help stuff, and then my system froze. I checked the wireless keyboard and mouse batteries - both are full. I finally did a soft reboot to free
the freeze. However, it booted into 16.04. I don't how to revert the install and it looks like that is all that is on my system now. 
It also appears to have split into 4 partitions - but I want to go back to 14.04. I tried the option to revert to a previous install - but that doesn't work.
Can someone tell me if I messed up and have to live with it or can I roll it back to 14.04?

Thanks

---

### Post by wildmanne39 on 2017-02-09
There is no way to revert to an earlier version of Ubuntu you have to reinstall 14.04 if you want to use it.
If you did a dual boot instead of getting rid of 14.04 then just go into the grub and choose 14.04.

---

### Post by Gnusboy on 2017-02-09
Thanks Wildmanne39

Do you know why it installed the operating version of 16.04 instead of the trial version?

---

### Post by wildmanne39 on 2017-02-09
The try it function is a feature of the livecd or liveusb, and you just hit the try button and it runs from the livecd, if it installed you must have told it to at some point.

If you set it up to keep 14.04 reboot and as soon as it starts to boot up start pressing the shift key until you see the grub menu and see if there is a kernel that corresponds to the one used in 14.04 which will be 3.13 and 16.04 is 4.4.

---

