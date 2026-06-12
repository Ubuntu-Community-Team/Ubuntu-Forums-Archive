---
title: "NVidia GeForce FX 5200 Install Woes"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by neatokino on 2007-12-03
I'm trying to install Ubuntu Gutsy (dual boot with XP) on a Dell Dimension 8300, 2.6GHz P4 processor, 512MB RAM, Nvidia GeForce FX5200 graphics card, HP 24" LP2465 Monitor. 

I've tried the regular Ubuntu 7.10 install disk and the Alternate Install disk, and in each case, my screen goes haywire early in the process, and I can't continue.  Using Text install with the alternate CD, I can get to the partitioning menu and then the screen blinks, goes snowy, then goes black.

I'm pretty sure it's an issue with the Nvidia card.

Is there a way to get to a command line early in the install process and either download the appropriate NV driver or somehow adjust things to keep my screen from going blank?  I'm pretty much a newbie, so the more specific you can be, the better.

I don't think my hardware's faulty;  it functions perfectly with XP, and I am able to run the latest  Mandriva One Live CD, which seems to have NVidia drivers on it.  But I want Ubuntu!!

Thanks in advance for any help you can offer.

---

### Post by Torgas Prim on 2007-12-03
I think by booting to the Live CD with the Safe Mode option will help you there. Once in Safe mode live, run the install.
Also, if the display is going haywire you may want to check thermal issues going on.
Another, did you upgrade the Dimension with any part not Dell sanctioned? I worked for Dell as a level2 senior support resolver and I can tell you that things like ram and the video card are proprietary. The motherboard and power supply are the culprits really. And any part not supported by Dell can have effects like you are talking about. Even ram can make a new windows install months after the ram is upgraded to fail and seem like hardware is fried.

Hope this helps.

---

### Post by neatokino on 2007-12-03
Thanks so much for the response.  Unfortunately, safe mode doesn't seem to work either.  It's very frustrating!

I picked up the computer second hand, so I don't know what, if any, changes were made through Dell or not.  Is there a way to tell by looking in the computer?

I do know that the computer functions perfectly well with Windows XP, and it also seems to work perfectly when I boot through the Mandriva 2008 Live CD.   

I thought it might be a thermal issue, too, as the problems seem to kick in after a few minutes... but with the Mandriva Live CD, I can run for hours without any trouble, and there are no issues whatsover with Windows XP.

Is there a way to bypass the graphics card in the Ubuntu install?  I keep thinking that if I can get the system on my drive and then use the command line to install the proper drivers (envy or the proprietary nvidia), then I might be able to get it to work.

Right now, safe mode, text install, everything just gets nowhere with the Ubuntu installation.

---

### Post by Torgas Prim on 2007-12-04
Yes, a good way to get around the video card is to either install another one if you are using the on-board video card. Installing a new card disables the on-board in Dells by default. If it is a PCI or AGP video card, remove it and use the on-board for the install...see what happens.

Another thing to look at...have you updated the bios?

Go to [http://support.dell.com/](http://support.dell.com/)
Click on Drivers and Downloads
Click on Choose by Service Tag
Then enter your service tag number.
(It is a sticker on the back, or inside the front accessories door)
Look for a bios update that you can run in windows, it is easier to run and has less chance of you hosing the bios.

Here is the link to the Dimension 8300 BIOS update page...[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R86308&SystemID=DIM_PNT_P4_8300&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=113031](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R86308&SystemID=DIM_PNT_P4_8300&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=113031)
It says rev A07. If yours is a lower number, update it and try the install again.

---

### Post by neatokino on 2007-12-04
Thanks again--  I had already updated my bios to the latest version, so I am pretty sure the video card is the culprit.  I think I'm going to go ahead and upgrade the card.

I guess I need an 8x AGP card that doesn't require too much power.  Is there an AGP video card that is known to be especially friendly to Ubuntu?  A good recommendation would help a lot!

---

### Post by Torgas Prim on 2007-12-04
I do not know which card to recommend, but I have seen in my travels through the boards that nVidia seems to be the best for Linux. ATI does not seem to update their driver support for their cards and a lot of people are having issues with that line of cards.

Best guess...go with nVidia and start at the 6600 series and work up from there. Check Dell's website as you may have to get a card from there... :(

---

### Post by neatokino on 2007-12-04
Thank you Torgas.  I will start looking around, and I'll check the Dell website.  I'm hoping not to spend too much money, though, of course! 

If anyone else has any suggestions, please send them my way.

---

### Post by jimmyjean on 2008-02-07
Did you find a solution to this problem? I also have a Dell PC with an NVIDIA GeForce FX 5200 graphics card and get the same problems when trying to install Ubuntu 7.10. My previous version of Ubuntu installed and ran without any problems with exactly the same hardware setup. 

Please let me know if you managed to install it in the end.

Thanks

---

### Post by cryptozoologist on 2008-02-08
i have a box with that card and the live cd bombed, but the alternate cd worked for me.  not helpful i know, but perhaps for others who stumble on this thread.

peace
cryptozoologist

---

### Post by leg on 2008-02-08
I have that card installed both on my Ubuntu and my Gentoo install. I think you will find that the latest drivers from NVidia do not support it anymore as it is a rather old card. On my system I use the nvidia-drivers-1.0.9631 version which is the last one to include suppport for that card.

---

### Post by BLTicklemonster on 2008-02-08
Are you saying that you try to boot to the live cd and you can't even do that?

Does it act like the graphics are messed up, and get to where you would normally do a dpkg-reconfigure xserver-xorg?

Assuming so, then when you get there, don't do anything yet. Look up at the information you see, and see if it says BusID 2:4:0 or anything *other than* BusID 1:5:0

Hopefully you will find that it does.

This BusID you see (if other than 1:5:0) will need to be entered manually during the sudo dpkg-reconfigure xserver-xorg just look at each screen as it comes up and you'll see where you can change the busid. A word of advice, turn your num lock on.

Hopefully that's all it is?

Good luck anyway, that's a great little card. Get the envy installer and don't waste time with other methods. I've tried the restricted install, and compiling, and envy did the best job overall for me.

---

### Post by jimmyjean on 2008-02-09
Would it be worth disabling the card and trying to install without it. Then I could try installing that driver when I at least have ubuntu up and running?

Thanks for the help

---

### Post by jimmyjean on 2008-02-09
P.S. I haven't tried the live CD. I've only got a copy of the installation cd. I have tried installing in safe graphics mode and that doesn't work either. The graphics mess up and then the screen goes blank.

---

