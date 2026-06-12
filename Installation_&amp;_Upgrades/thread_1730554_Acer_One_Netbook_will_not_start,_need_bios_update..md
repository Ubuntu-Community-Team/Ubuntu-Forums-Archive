---
title: "Acer One Netbook will not start, need bios update..."
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by Squall79 on 2011-04-16
I have installed Ubuntu on my Acer One Netbook one 2 years ago, and recently updated it to 10.04 (or 10.10 I do not actually remember, but it was back in last november so I suspect 10.10). 

I normally connect a usb disc I use to the netbook, and a few days ago I again connected the USB disc but now before I turned the netbook on (normally I would do it after the op. system desktop comes). 

After this, the green power button was lit but the screen stayed black. It is like this since than. 

This happened to me before and I took the netbook to an Acer service center. Since I bought the netbook from abroad it was not under warranty, and they told me they made a bios update, and charged me 30 usd. It was working fine since then. 

I suspect that I did not change boot sequence since I installed ubuntu from a usb disc, and when I turned it on with the usb disc on, the boot sequence caused this. 

Now, the only bios update files in Acer website are for XP, so I could not find anything there. 

Now does anyone know anything about this problem, and if I have to make a bios update, how do I do this with for Ubuntu ?

Many thanks in advance for any help...

---

### Post by mörgæs on 2011-04-16
A BIOS update is normally released with long time in between. I doubt that you need this.

Can you boot into recovery mode and apply all updates here? 

If you don't see the boot menu, keep pushing left-shift at the moment when the BIOS part of the boot ends and the Ubuntu part begins.

---

### Post by Squall79 on 2011-04-17
Unfortunately, when I turn the netbook on, only the green power light is lit, and nothing appears on the screen, neither boot part nor anyother part of the start suquence. The screen is completely black...


I know this is not a hardware problem, since the service center managed to fix the very same problem. If I cannot manage to find a solution to this problem, I will have no choice but to take it again to a service center.

---

### Post by mörgæs on 2011-04-17
Can you boot into a live session from USB?

---

### Post by varunendra on 2011-04-18
BIOS update is potentially a risky business, so try to reset BIOS first if you can get into it.

Otherwise, I'd suggest to spend the money to let the service center guys do it for you, for it will then be their responsibility if something goes wrong (you should confirm if they take full responsibility).

Now if you want to try it yourself while understanding the risk (the netbook may become completely unusable if updated with wrong BIOS file or broken file or update is interrupted before completion) try this:
> Solution: Update the bios as follows: 
1.	 Go to [www.support.acer.com]("http://www.support.acer.com/") 
2.	Click on Driver & Downloads 
3.	Select Product Family “Netbook” 
4.	Select Product Line Aspire One 
5.	Select your Product Model i.e.: AOA150 (located after MFG.Date:xxxx AOA 150 – xxxx) 
6.	Click on the BIOS tab below 
7.	Download the bios to a blank USB flash card. 
8.	Turn off your computer 
9.	Insert the USB flash card (containing the bios) into your Aspire One. 
10.	Hold down the FN key and the Esc Key at the same and turn on the computer. 
11.	Wait until the Power button starts flashing before letting go of the keys. 
12.	Allow the computer to complete its task (5 or more minutes). 
(source: [http://www.tomshardware.com/forum/261352-28-aspire-battery-recognized](http://www.tomshardware.com/forum/261352-28-aspire-battery-recognized) , 15th post by chetwynd)

Or this (if the BIOS is not completely stuck and you are able to boot from usb flash drive):
[http://www.netbooktech.com/2008/10/01/instructions-for-updating-the-acer-aspire-one-bios/](http://www.netbooktech.com/2008/10/01/instructions-for-updating-the-acer-aspire-one-bios/)


For BIOS reset (if netbook doesn't boot at all):
[http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html)
[http://macles.blogspot.com/2008/08/clearing-cmos-of-acer-aspire-one.html](http://macles.blogspot.com/2008/08/clearing-cmos-of-acer-aspire-one.html)


If not sure about whats and hows, I'd again suggest to leave it to the service guys, or post back complete model no of your netbook (on the backside sticker - AOA150 or something else? Please excuse me if it is a stupid question - I am not familiar with netbooks yet).

---

