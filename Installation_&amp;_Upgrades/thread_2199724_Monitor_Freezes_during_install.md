---
title: "Monitor Freezes during install"
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by jpluck on 2014-01-15
[COLOR=#333333][FONT=Lucida Grande]Hi everyone,[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Wonder if anyone can help me with a problem that has got me totally foxed. I am trying to resurrect an old desktop for my partners kids to use and was hoping to install xubuntu[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] on it,[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] I chose xubuntu as its an olldddddd PC with old hardware.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]The problem I am having it that at various stages the monitor is putting itself into standby and the only way to get it out is to do a forced system shutdown. It happens at any moment, during loading of the live CD, after the cd has loaded and when I then try and install. Basically at any random time. I have tried installing  Xubuntu, Zoring OS7, Net Runner, Lubuntu, [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]Mint xfce, [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]blah blah. I have downloaded the ISO in chrome, firefix and via torrent. I have tried burning the ISO with K3b, Brasero, windows 8 built in burning software and Magic ISO. Still the same result. I have also tried installing from USB, again same result.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]All of which would give the idea that it is a fault with the hardware, BUT, I have been able to install windows xp from an old Dell cd with no problems at all!! Twice in fact. No problems with the monitor at all.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]If any one has any ideas please let me have them as I am running out of hair to pull out [/FONT][/COLOR][IMG]http://forums.linuxmint.com/images/smilies/icon_eek.gif[/IMG][COLOR=#333333][FONT=Lucida Grande] 

Thanks,

James
[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-01-15
Welcome. Long shot, but if you can boot from the Live install disk/USB and get to the screen 'Try Ubuntu' 'Install Ubuntu' etc., hit F6 and choose 'nomodeset' from the popup menu. Proceed. Any different?

---

### Post by jpluck on 2014-01-15
I'll give it a try and see what happens.......

---

### Post by jpluck on 2014-01-15
Okay, tried that with xubuntu on cd and usb, both resulted in monitor shut down. Tried it with xubuntu alternate cd on usb, managed to get to the options through F6 and chose nomodeset,  resulted in a frozen screen with what looks like the options menu repeated four times across the top, then a black space and then a load of random stuff that looks like a patchwork quilt underneath.

end result, even less hair on my head lol.


As a possible option if we can't find a work around for this, if I was to plug the HDD from this machine into my own desktop, would I then be able to load xubuntu onto it and then unplug it and put it into the old PC or would that result in even more issues?


Cheers,

James

---

### Post by Bucky Ball on 2014-01-15
> **jpluck said:**
> As a possible option if we can't find a work around for this, if I was to plug the HDD from this machine into my own desktop, would I then be able to load xubuntu onto it and then unplug it and put it into the old PC or would that result in even more issues?

Do it and find out. That would normally work fine.

BUT ... there seems to be some issue with Ubuntu and your hardware, probably graphics but not for sure, so there are no guarantees this will work.

BUT ... having said that, give it a go. It would work fine under normal circumstances. ;)

---

### Post by efflandt on 2014-01-16
How old is the computer, how much RAM does it have, and does it have dedicated graphics or integrated graphics using shared RAM??

---

### Post by grahammechanical on 2014-01-16
> [COLOR=#000000]As a possible option if we can't find a work around for this, if I was to plug the HDD from this machine into my own desktop, would I then be able to load xubuntu onto it and then unplug it and put it into the old PC or would that result in even more issues?[/COLOR]

If you do that do not tick the box "Install Third Party Software." That will install a proprietary video driver compatible  with the video adapter of your desktop machine. Which may or may not be compatible with the video adapter in the machine you really want Xubuntu installed on. Especially if the cards are from different makers (Nvidia, AMD or Intel). When we do not tick that box we get an open source video driver that is usually compatible with more than one make of video adapter.

Regards.

---

### Post by Bucky Ball on 2014-01-16
> **grahammechanical said:**
> If you do that do not tick the box "Install Third Party Software." That will install a proprietary video driver compatible  with the video adapter of your desktop machine. Which may or may not be compatible with the video adapter in the machine you really want Xubuntu installed on. Especially if the cards are from different makers (Nvidia, AMD or Intel). When we do not tick that box we get an open source video driver that is usually compatible with more than one make of video adapter.

Regards.

Very good point. Didn't think of that. :-k

---

### Post by jpluck on 2014-01-16
In reply to efflandt i'm not sure how old exactly but at least 10 years old. It has an MSI motherboard, 1gb of RAM, and a Radeon 9550 graphics card.

I have another old graphics card which I might have a go with, if that doesn't work I'll trying putting the HDD into my own PC and see what happens then.

Cheers

James

---

### Post by jpluck on 2014-01-16
Ok, now totally confused. Put alternative graphics card in, still couldn't get anywhere. Monitor didn't shut down but loading of live cd would just hang. Decided to try something not Ubuntu based. Loaded and ran openSuse from live cd with aternative graphics card. Swapped to original card, loading just hanging with blinking cursor, so back to alternate card.

So then I thought I would have one more go with Xubuntu before installing a non ubuntu distro properly.
 
Low and behold it only bloody installed!!!!!! 

The confusing thing is that I have tried the alternate card at various times over the last 4 days of trying to get this to work with no joy, so I don't know if it was a dodgy download/burn of the iso when I happened to have the alternate card installed or what.

The main thing is I have a working system with Xubuntu installed and running :D

It would seem that the fault lay with the original graphics card, I noticed that the heatsink was very hot when I swapped it out. What I can't understand is why it would let me install and run windows but none of the linux distros I tried. Wonder if anyone has any thoughts, if not I will just have to live in ignorant bliss ;)

Thanks for your help guys.

James

---

### Post by Bucky Ball on 2014-01-16
Ubuntu can sometimes be a bit more sensitive, or 'idiosyncratic' perhaps, about dodgy hardware than Windows.

Please mark your thread as solved by following the instructions in my signature. Enjoy!

---

