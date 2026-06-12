---
title: "Installation fails with Diamond Stealth Radeon 9250"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by faldrich on 2010-02-17
I have an IBM x3200 64-bit system which I installed a Diamon Stealth Radeon 9250 (ATI) card in.

In either version of Ubuntu/Kubuntu the CD will boot, give me the menu, and when I select either Live or Install, the screen flickers and the system reboots.

Previously, when I installed using the on-board card, I loaded the FGLRX drivers and was eventually able to get something working.  Though it would not enable desktop effects (and clearly this card is more than capable of it); But not with a new install.  

From reading on the net, there seems to be a proprietary driver I should be using -- but the instructions I found did not work and rendered the test installation useless.

There must be some way to get this working - I'm a little surprised that it doesn't out-of-the-box as it's an older card.

Can someone help me figure this one out?


Thank you in advance...

---

### Post by gordintoronto on 2010-02-17
This site describes the problem with old ATI cards:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

I have installed Ubuntu 9.10 with an old ATI card and it works fine, I just don't use proprietary drivers.

The rebooting when you try to install sounds like a different issue, though.  Which CPU is in your X3200?  This site describes the many options:
[http://www-03.ibm.com/systems/xbc/cog/Withdrawn/x3200/x3200aag.html](http://www-03.ibm.com/systems/xbc/cog/Withdrawn/x3200/x3200aag.html) 

Several of those options are not 64-bit.  Have you tried installing 32-bit?  If you have less than 4 GB of memory, there's not much advantage to using 64-bit Ubuntu.

Could you install using the on-board video, don't do anything about video drivers, just add the ATI video card?

---

### Post by faldrich on 2010-02-17
The IBM x3200 I have is the 4362-52U, which I didn't see listed on the URL.  I think this has 2gb of RAM.

I have indeed tried installing on with the on-board card, then installing the ATI card and it did the same thing.  Only when I installed the FGLRX drivers on the old card, then installing the new one was I able to get it working.

I had no idea this was such an outdated card -- just assumed it would "just work."   Problem is, the slots on this system are PCI and only PCI-E x8 or something not wide enough for graphics.

With regard to the next release 10.x, I wonder if this issue has been fixed -- I would be willing to install and try it out.

What threw me off, too, was that the system would just reboot and reboot until I stopped it -- if the Xorg server can't start, shouldn't it just default to text-based login?


Thank you.



> **gordintoronto said:**
> This site describes the problem with old ATI cards:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

I have installed Ubuntu 9.10 with an old ATI card and it works fine, I just don't use proprietary drivers.

The rebooting when you try to install sounds like a different issue, though.  Which CPU is in your X3200?  This site describes the many options:
[http://www-03.ibm.com/systems/xbc/cog/Withdrawn/x3200/x3200aag.html](http://www-03.ibm.com/systems/xbc/cog/Withdrawn/x3200/x3200aag.html) 

Several of those options are not 64-bit.  Have you tried installing 32-bit?  If you have less than 4 GB of memory, there's not much advantage to using 64-bit Ubuntu.

Could you install using the on-board video, don't do anything about video drivers, just add the ATI video card?

---

### Post by faldrich on 2010-02-17
I got a little farther with Lucid -- at least it doesn't just reboot the machine; rather, the screen goes black and will reboot if I do CTRL-ALT-DEL.

Maybe it's better to just get another video card -- LOL   It will need to be PCI for this IBM x3200.  Any suggestions?

---

### Post by gordintoronto on 2010-02-17
> **faldrich said:**
> I had no idea this was such an outdated card -- just assumed it would "just work."   Problem is, the slots on this system are PCI and only PCI-E x8 or something not wide enough for graphics.

With regard to the next release 10.x, I wonder if this issue has been fixed -- I would be willing to install and try it out.

What threw me off, too, was that the system would just reboot and reboot until I stopped it -- if the Xorg server can't start, shouldn't it just default to text-based login?


Thank you.

I have had good success with eBay; I bought an older card for $10.  Just make sure it's an nVidia. [smile]

If you can afford a new card, newegg.com still has several PCI video cards.

And yes, I think the constant rebooting is worth filing a bug report.

---

### Post by faldrich on 2010-02-18
I found this one:

PNY Verto GeForce FX 5200 PCI Video Card

They are cheap... so I'm safe with any nVidia card with Ubuntu?

---

### Post by gordintoronto on 2010-02-18
That card is almost 7 years old, but it was well reviewed when it was new.  I *think* it should be OK with Ubuntu.  (I used a much older nVidia card up until recently.)

Funny, the card is also on Amazon:
[http://www.amazon.com/PNY-Geforce-FX5200-256MB-Graphics/dp/B000F5IE9Y](http://www.amazon.com/PNY-Geforce-FX5200-256MB-Graphics/dp/B000F5IE9Y)

---

### Post by faldrich on 2010-02-18
It's an older card, yeah... but I need PCI for video.   Can you recommend a newer/better one?

Thanks.

---

### Post by gordintoronto on 2010-02-19
> **faldrich said:**
> It's an older card, yeah... but I need PCI for video.   Can you recommend a newer/better one?

Thanks.

I don't have a recommendation.

---

