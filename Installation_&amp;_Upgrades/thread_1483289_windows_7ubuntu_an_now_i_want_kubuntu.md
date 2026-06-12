---
title: "windows 7/ubuntu an now i want kubuntu"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by teddy101 on 2010-05-14
I know that you clever peeps have made it so I can run many diffrent types of Linux at the same time with no trouble [IMG]http://kubuntuforums.net/forums/Smileys/classic/smiley.gif[/IMG].
However I only have a Dongle that will work on windows (which i am co running with Ubuntu) so I can only download Kubuntu on to my windows side of the harddrive (I know ubuntu can read windows) but being rather new to Linux I'm not sure if this would work as easily as it sounds [IMG]http://kubuntuforums.net/forums/Smileys/classic/smiley.gif[/IMG]. 
 
So Thanks any advice on how I have totally miscalculated would be appreciated [IMG]http://kubuntuforums.net/forums/Smileys/classic/cheesy.gif[/IMG]

---

### Post by darkod on 2010-05-14
If your plan is to boot windows, download the kubuntu image, and burn a cd, it will work.
It would also work downloading the image in windows, then booting your ubuntu and copying it over from the windows partition. Then you can burn it in ubuntu.

Depending what you actually wanted to achieve.

One note: if you want to add kubuntu and make it a triple boot, it's better to click the Advanced button in the last screen in the installer and tell it not to install a bootloader. Grub2 is already there from ubuntu and it can boot kubuntu. After the installation you just need to boot ubuntu and run:

sudo update-grub

to detect the new kubuntu OS.

---

### Post by teddy101 on 2010-05-14
Thankyou you legand!! :D

---

