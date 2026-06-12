---
title: "Trying Jaunty to get my wireless card to work"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JacobRogers on 2009-03-16
I recently bought a new emachines (cheap) desktop and I read that the Belkin 7050 wireless cards are supported out the box.  But after buying the card and researching the matter more I learned that your system has to be updated for it to work.

Since I don't have internet on this computer I tried to use keryx to update it.  It worked, I guess and I was able to get the right kernel and after following this tutorial [http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30) I'm still not able to get it working.

I'm kind of at the end of my patients.  

So I thought maybe if I tried this alpha version of jaunty with an updated kernel, that I would have some success.

Do you think this is a bad reason to try alpha software?

I will update you and let you know if it works though.  Hopefully it will work out of the box!

---

### Post by sgosnell on 2009-03-16
It might work.  It supports lots of newer equipment, and the 2.6.29-rc8 supports even more.  Using an alpha OS with a release candidate kernel is getting ahead of the herd, but it's stable on my system.  You should be able to get a wired connection to work long enough to update your system.  Can you not move the router close enough to do that for a short time, or else get a long ethernet cable?

---

### Post by pspsampsp on 2009-03-16
my belkin f5d7050 v3.xxx works out of the box so if yours is a 3.xx yours should to

---

### Post by Halow on 2009-03-16
I've been using a Belkin F5D7050 (on a eMachines, no less. laugh, I do) since late in the Hardy cycle. It worked right out of the box, and with Jaunty it's behaving better than ever.

---

### Post by JacobRogers on 2009-03-16
success?

Ok after installing Jaunty I wasn't having much luck with the belkin wireless card.  So I followed this tutorial [http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30)

I still wasn't having much luck so on a whim I decided to switch usb ports.  Then all of a sudden it worked, kinda.

It shows my card, the card will let me connect to my network.  But then the internet is really slow.  Usually it will come up as page cannot be displayed but one time after like 5 minutes I got google.com to come up.

So I thought that "maybe it was the usb port all along.".  So everything I changed in the tutorial, I went back and put back the way it was.

The card still works but the issue is the same.

This is sort of frustrating.  

Any help greatly appreciated.

---

### Post by kilinu5889 on 2009-03-16
Try ndiswrapper. That is what I am using right now. I am just fine and i have not found any problems with my wireless card.

---

### Post by JacobRogers on 2009-03-16
I'm reinstalling Jaunty with the wireless card in the usb port that I know works.

I wonder if only some of my ports are usb 2.0.

---

### Post by JacobRogers on 2009-03-16
well that didn't work.  I'm exactly where I was before.  It says it works and connects but then the internet doesn't work.  And I know the internet is working because I've got other computers on the network using the internet.

---

### Post by linux6994 on 2009-03-16
My f5d7050 Belkin works great with Juanty. My lspci is:
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
 I have installed b43-fwcutter to handle it.

---

### Post by pspsampsp on 2009-03-24
if its not to late try diabling ipv6 [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

