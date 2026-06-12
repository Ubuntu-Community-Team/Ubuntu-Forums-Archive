---
title: "problem installing version 14.04LTS"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2015-10-06
Folks,

I get the problem with graphics when trying to install version 14.04. My question is what can I do about it? I'm aware that the next LTS version is due in 2017, but I don't want to wait that long as I need to dual boot with windows 10 (from windows 7).
I've has a bit of a previous discussion on this topic with no real resolution. 

As my graphics is part of the motherboard, if I get a graphics card will that do the job or do I need to get a new motherboard.

My current motherboard is a Gigabyte 78lmtusb3 or are there any other options?

Regards

Bob

---

### Post by Bucky Ball on 2015-10-06
The next LTS is 16.04 LTS, April 2016. They come every two years. You can upgrade LTS to LTS, leapfrogging the interim releases in between (something to remember if you are contemplating interim 15.04 or the soon to be released interim 15.10). 

Have you tried the nomodeset option? Boot the install CD, hit any key when you get to the purple screen with the icon at the bottom (should be first up), hit F6, choose 'nomodeset', continue. Any different? 

Is graphics fine when you boot to a live session from the install media (Try Ubuntu)?

---

### Post by bobmac on 2015-10-06
My apologies,
At the moment I'm using version 12.04LTS on a dual boot machine with windows 7 on 1 hdd and ubuntu on the other. I've got the Software Sources Updates tab set to For Long Term Support Versions. And the Software Updates screen continually informs me that version 14.04 is available.

When I attempt to update to that version is when I get the graphics problem message. The message also states that if I try to install version 14.04 then my machine may well slow down, which you'll appreciate is not what I want.

My intention is to upgrade to Windows 10 (free until 29 July 2016),on the windows hdd and update to the latest ubuntu LTS version on the other disk. 

Reading other posts, it seems that I may need to install version 14.04 after installing windows 10.

My concern is that, since I get the graphics message, when trying to install version 14.4 at present, it's likely that I'll still get it after installing windows 10. So! how do I get out of my dillema? Do I need to get another motherboard that will work with verion 14.04 and subsequent LTS versions or if buy a graphics card will that cure the problem?

Regards

Bob

---

### Post by Bucky Ball on 2015-10-06
Not much to say until we know what the error message for graphics is. You don't give exact details of the message.

I can only guess you have installed a third-party proprietary driver for graphics or added a PPA for them, xorg-edgers for instance. 

What exactly does the message about graphics say (not the bit about it slowing down your machine)? Please be specific. :)

---

### Post by bobmac on 2015-10-06
Folks,

The message is:

Your graphics hardware may not be fully supported in Ubuntu 14.04.

Running the unity desktop environment is not fully supported byu your graphis hardsare. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now.. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWorningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWorningForUnity3D) Do you still want to continue with the upgrade?

At this point in the proceedings I have selected the no button.

Regards,

Bob

PS. I am not too familiar with the inner workings of ubuntu so I'd be grateful is you could explain any answer assuming that I'm pretty dumb.

---

### Post by Bucky Ball on 2015-10-06
All I can think is that your computer does not have a 3D capable graphics card. Try another flavour of 14.04 LTS as an experiment and find out. Try Xubuntu or Lubuntu. As far as I know, the Unity desktop used by Ubuntu now requires 3D graphics cards. I don't use it so no expert. Someone else might chime in with the facts.

---

### Post by bobmac on 2015-10-06
Bucky Bill,

Hopefully you've hit the nail on the head. I will get a 3D capable graphics card and go from there.

Many thanks for your and all others that were patient enough to help me out.

Regards,

Bob

I'll close this thread now.

---

### Post by Bucky Ball on 2015-10-06
Thanks for marking as solved. As I say, before forking out for the 3D card I would experiment with an OS that doesn't need one. You don't need to install it. Just boot from the live media and see how far you get. If all is normal, then that's it. 

Depending how old you machine and motherboard is will dictate the type of card you are going to be able to get in there. Make sure you research this thoroughly before grabbing, say, a PCE-e graphics card. Your machine may not have the slot for it.

---

