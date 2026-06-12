---
title: "[SOLVED] Got Ubuntu 7.10 installed now it wont boot need help"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Sicundercover on 2007-12-04
First I tried to install with the live disk and that didnt work I just got a blank screen the MD5SUM checked out fine but i didnt work I eventually tried the Alternate disk and that worked for the install.

I Got Ubuntu 7.10 installed now it wont boot Grub loads and I select Ubuntu 7.10 and I get the same blank screen as before nothing happens.

Any suggestions.

BTW ran a memtest and that all good.


AMD X2 5200+
Asus Crosshair Mobo
8 Gigs Corsair XMS TwinX Ram
2x Nvidia Quadro FX5600

---

### Post by Severun on 2007-12-05
try turning off apci, there a boot option you can specify called noapci.  That's worked for me before where I had machine that wouldn't boot.  Do a search for "ubuntu boot noapci" and you should be able to find more detailed instructions on how to set it

---

### Post by Sicundercover on 2007-12-05
Thanks Ill give that a shot

---

### Post by Sicundercover on 2007-12-05
Well Ive tried  noapci, noapic, and noacpi and none of them worked.

Still same thing, as with the Live CD , Kernal Alive loading please wait blank screen nothing happens.

---

### Post by kragh on 2007-12-05
> **Sicundercover said:**
> Well Ive tried  noapci, noapic, and noacpi and none of them worked.

Still same thing, as with the Live CD , Kernal Alive loading please wait blank screen nothing happens.

This may be a graphics problem. Have you tried Ctrl-Alt-F1 thru F7 at the blank screen to see if you can get to a terminal? When installing did you select all the resolutions available? Try selecting the lower resolutions.

---

### Post by Sicundercover on 2007-12-05
> **kragh said:**
> This may be a graphics problem. Have you tried Ctrl-Alt-F1 thru F7 at the blank screen to see if you can get to a terminal? When installing did you select all the resolutions available? Try selecting the lower resolutions.

I just tried the ctrl-alt-f1 thru f7 and nothing happens.

I wasnt aware you could select multiple resolutions I just selected 1 resolution which was 1680x1050.

---

### Post by kragh on 2007-12-06
> **Sicundercover said:**
> I just tried the ctrl-alt-f1 thru f7 and nothing happens.

I wasnt aware you could select multiple resolutions I just selected 1 resolution which was 1680x1050.

That may be something to look into. Your graphics card and/or monitor driver as installed by Ubuntu may not support this resolution. During install there is a screen that allows you to select the resolutions. Since you have no access to the terminal you may not be able to edit the conf files. You could try booting into recovery mode and see if you can access these files. You would boot form the install CD and select recovery.

---

### Post by MQMike on 2007-12-06
[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)
How to get started with no GUI

And herman steps you through X configuring the video, at:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by Sicundercover on 2007-12-10
Sorry i didnt update this thread.

I figured most of the problem out. The issue wasnt X at all (At least I dont think it was).

I had to delete "quite spash" from the Kernel boot instructions. I did this by selecting the Ubuntu boot option in Grub and hitting "e" and then selecting Kernal and hit "e" and delete the commands followed by "enter" and then "b". After this is booted right. 

I then did some research and found out how to change the grub. 

Only issue is I dont get a nice splash. Though everything is working fine I would like to find out what the direct link between "quite splash" and not booting into desktop is.

However Im really liking this Distro just need to get every thing tweeked how I want it.

---

