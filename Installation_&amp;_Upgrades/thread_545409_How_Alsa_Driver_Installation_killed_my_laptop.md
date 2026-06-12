---
title: "How Alsa Driver Installation killed my laptop?"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Kxpress on 2007-09-07
I followed instruction of ALSA project to install the driver for my T62 laptop with Intel Audio Chip 82801H (ICH8) rev 3.
" https://help.ubuntu.com/community/HdaIntelSoundHowto"
Until the last step to reboot the sysem. The login screen came back OK, I entered the username and password, but the screen went blank (actual default brownish color of Ubuntu) plus one white icon with no words, buttons, icons, pictures whatsover. It stayed that way forever.

The I used Alt+CTRL+F1 to get in X-window, this is what I see:

------------------------------------------------------
Loading, please wait &#8230;
kinit: name_to_dev_t(dev/sda5) = sda5(8,5)
knit: trying resume from /dev/sda5
knit: no reume image, doing normal boot

Ubuntu 7.04 khunbuntu tty1

Khubuntu Login:

-----------------------------------------------------

I have install ALSA twice, the first time I had NVidia Diver installed and the graphic part worked fine. The recent ALSA installation, I used the "Vesa" mode for graphic. The results after Alsa installation are exactly same in both case, I don't know how to get my laptop back to the previous wotking condition...

Anyone have this experience ?

---

### Post by markoloka on 2007-09-08
Same problem. Thanks to previous update of kernel. 
Wondering what should i do... Found this: [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)

I try to solution if/when i find it.

---

