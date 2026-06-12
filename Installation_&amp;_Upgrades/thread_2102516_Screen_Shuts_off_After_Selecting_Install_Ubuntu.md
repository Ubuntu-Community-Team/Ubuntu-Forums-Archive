---
title: "Screen Shuts off After Selecting Install Ubuntu"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by newtonious on 2013-01-07
This is my first time trying to install Ubuntu, however when I try to install Ubuntu from my live USB I made using LiLi USB creator my screen shuts off. It doesn't just go black but my screens back light just shuts off. 

The good news is that I can hear sounds when at the blank screen. It sounds like an exotic chime, but that is it... which leads me to believe it is my graphics card. 

I am using a Windows 8 PC to dual boot. Its a core i5 with nvidia 640 optimus graphics. 

This is EXACTLY what I do when I turn on my PC. 
1. I select F12 which brings me into my boot menu.
2. I select boot from USB (the one I made using LiLi)
3. I am brought to the GRUB screen where I am prompted to select a few options.
4. I select Install Ubuntu
5. It shows a black screen for a few moments before going completely dark. (This is where I hear a chime)
6. I get pissed and Google the hell out of my issue. 

I never see a purple screen with a keyboard and a person like many of the other post say you will see. I only see the grub screen. 

No matter what option I choose (like try Ubuntu) in grub it goes  straight to the blank screen. 

Ill preemptively thank you guys for your help, I'm sure that this has been solved somewhere else I just cant seem to find one where ^^^ exactly that happens.

---

### Post by grahammechanical on 2013-01-07
You do not say which version of Ubuntu you are using. The purple screen that you have read about is from later versions. Older versions gave us the black text screen with the Try or Install, etc., options that you might be seeing.

At the screen that you call the Grub screen, which it is not by the way, press F6 and from the list highlight nomodeset and press Enter. Then press Esc to back out of that menu and get back to the Try or Install screen and try again from there.

It occurs to be that you just might be seeing a Grub menu. In which case you have not created a live USB stick but you have installed Ubuntu to a USB stick.

Regards.

---

### Post by newtonious on 2013-01-07
> **grahammechanical said:**
> You do not say which version of Ubuntu you are using.

I am trying to install 12.10

Sorry for my misuse of the term grub. I will take screen caps of what I see and post them here.

---

### Post by guyfromfl on 2013-01-07
This is pretty much my issue too..

I get the Grub then NOTHING after I select an option.

Are you booting in UEFI or legacy? 

When I boot the installer from legacy, it works, however my Windows 8 is installed UEFI so I do not install..

What computer are you trying to install on? My problem happens on an hp Pavillion P7-1417.

> At the screen that you call the Grub screen, which it is not by the way, 
On my computer, when I boot the install disc in UEFI, the screen says GRUB 1.99

This is the screen, sorry it is so small, it is straight from ubuntu.com...
[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by guyfromfl on 2013-01-09
any luck newton?

---

