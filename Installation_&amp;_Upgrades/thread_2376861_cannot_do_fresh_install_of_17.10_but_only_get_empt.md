---
title: "cannot do fresh install of 17.10 but only get empty desktop background"
date: 2017-11-06
forum: Installation &amp; Upgrades
---

### Post by antiOST on 2017-11-06
Hi

I have rather old htpc pc I want to install Ubuntu 17.10 from a bootable usb . Whether I choose live usb or install from boot menu, ubuntu only loads the desktop background and nothing else, no icons, no menus, no launcher no anything. Couldn't get a terminal either not sure if keyboard is even reacting. No mouse either. 
I tried same usb on a laptop and it loads live usb with no problems. Pretty sure I tried all boot options (F6 in boot menu) some of them didn't even get me to the desktop.
Just to try something different I also tried ubuntu mate 17.04 with same problem. 

I'm running intel dh61ag board, cpu i3-2120 with integrated HD 2000 grahics

thanks

---

### Post by raja.genupula on 2017-11-07
Have you tried with any other flavor of Ubuntu like Lubuntu or Xubuntu ?

---

### Post by antiOST on 2017-11-07
Only ubuntu mate as mentioned. Should I and which one would be a good choise. Is this for troubleshooting or permanent solution since I'm really interested in try Ubuntu again after they gone back to Gnome.

---

### Post by RobGoss on 2017-11-07
As recommended Lubuntu and Xubuntu, are lightweight distributions and might be a better chioce for your machine. Older machine may not run the heavier version of Ubuntu as well and in some cases my be problematic

The best thing about Linux there are some distributions to choose from

---

### Post by antiOST on 2017-11-07
Thanks, I am familiar with Lubuntu and Xubuntu though I rather think this is a compability issue than er performance. The machine is running win7 and 10 without any problems. So I am not looking for striped down version of real ubuntu but the real thing. I only droped ubuntu back in the days because of unity.

---

### Post by RobGoss on 2017-11-07
So you are not able to get the live desktop ether?

---

### Post by antiOST on 2017-11-07
Yes, I get the boot menu. Both the live option and install option leaves me at the blank desktop (background).. When using the same usb stick in my laptop it load into ubuntu (live or to install menu) with no problem.
I just noticed that I totally overlooked a sticky post with options I can try [https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)

I will let you know how that goes and maybe try Lubuntu if that fails.

---

### Post by antiOST on 2017-11-07
Arhhh got it now! I managed to get mouse > terminal and from there I could reach display settings. I'm running through a projector and for some reason Ubuntu thinks I got two displays, a buildin + protector, I don't. All the menus, icons etc were on the buildin (invisible to me) desktop. So changing displays to mirroring  I got all the stuff on projector display too :-)

Thanks for quick responses and suggestions.

---

### Post by RobGoss on 2017-11-07
That's odd not sure why Ubuntu would think you have two monitors displays, that would explain why nothing was showing on your desktop. Let us know how things work out

---

### Post by antiOST on 2017-11-08
I have several display outputs on my board. I BIOS it was auto which should be used as primary. When changing to HDMI and not auto Ubuntu picked it up right.

---

