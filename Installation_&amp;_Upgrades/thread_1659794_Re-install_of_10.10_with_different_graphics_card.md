---
title: "Re-install of 10.10 with different graphics card"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by paddydd on 2011-01-04
Hi,
  I am re-purposing a DELL Optiplex 270 SFF to be my living room skype device. Formally I had a GEFORCE video card in the machine but it had only VGA and DVI. The new HIS ATI RADEON card has VGA, DVI and HDMI and I need HDMI for the LCD TV.

  So I swapped the cards out (they are both AGP) and now I see nothing on the monitor for HDMI or VGA. The machine is running but I cannot see anything on the monitor. Further, I can't ping it either. I was able to ping and ssh with the old card. 

  What is happening here? Should I expect UBUNTU 10.10 to recognize the new video card in the AGP slot. If I have to put the old card back in then what is the procedure to change cards?

Thanks
Paddy

---

### Post by cascade9 on 2011-01-04
If you have the nvidia drivers installed, then changing cards to ATI (or anybody else) will result in exactly what you have had happen. 

you should renstall the nVidia card, remove teh drivers, shut down. I'd try rebooting, just to check its not usign the nVidia drivers, then shut it back down. Install the ATI card (and closed drivers if you want), then you should be fine. 

BTW, you can get DVI-> HDMI adapters and ables. You wont get sound over HDMI that way, but you will get display.

---

### Post by paddydd on 2011-01-04
Just curious... I may want to make the HD bigger in this computer so if I get a new hard drive and put that in replacing the one with the current install of 10.10 can I install off of the CD and would this make the other card or the default ON-BOARD VGA work again?
Thanks
Paddy

---

### Post by paddydd on 2011-01-04
Just curious... I may want to make the HD bigger in this computer so if I get a new hard drive and put that in replacing the one with the current install of 10.10 can I install off of the CD and would this make the other card or the default ON-BOARD VGA work again?
Thanks
Paddy

---

### Post by cascade9 on 2011-01-05
Yes, reinstalling you OS (on a new HDD or the old one) will let you use the onboard video, or the ATI card. 

The only reason why changing the cards didnt work is because you have the nvidia proprietary driver installed.

---

### Post by paddydd on 2011-01-05
UPDATE:

 I put in  a blank HDD and the system still would not show anything on the monitor when I connected it to the ATI card. So I pulled the card out of the AGP plug and connected the VGA monitor to the def VGA on-board VIDEO and I can see the install screens on the monitor. After the system is running I will add in the ATI card.

Paddy

---

### Post by paddydd on 2011-01-05
UPDATE Number 2:

So I have put 10.10 onto the new system that DOES NOT YET CONTAIN the ATI4350 video card. The only way I could get the install to work was by plugging into the on-board video.

Once the system is up and running though I have another issue.

I download the fglrx via the Pack Mgr and it installs ok. I tried to run the aticonfig initial command but it didn't see the card. I shutdown the computer then install the card and when I re-booted I get a black screen while using the VGA plug of the card.  I move the VGA plug to the onboard video and I still don't see anything. 

Any suggestions?

Thanks
Paddy

---

### Post by cascade9 on 2011-01-05
> **paddydd said:**
> UPDATE:

 I put in  a blank HDD and the system still would not show anything on the monitor when I connected it to the ATI card. So I pulled the card out of the AGP plug and connected the VGA monitor to the def VGA on-board VIDEO and I can see the install screens on the monitor. After the system is running I will add in the ATI card.

Paddy

Normally, if you install an AGP card the onboard video automatically 'turns off'. You could try looking in the BIOS (hooked up to the onboard video, with no video card installed) and see if there is a 'use AGP video' or similar settings (I think that model only has 'onboard' and 'auto' options though). 

I think you might have hit a comptability porblems from what I can see here- 

[http://www.tomshardware.com/forum/289933-33-need-card-dell-gx270](http://www.tomshardware.com/forum/289933-33-need-card-dell-gx270)

Several people with that computer and card, and nobody gets any video output. :(

---

### Post by paddydd on 2011-01-06
Thanks very much for the info.

I guess it's time to return the card and get my money back.

Too bad I didn't see the information that you just showed me earlier. I did see a lot of reviews that said the card would work including one on the newegg site. 

I really wanted to buy a pre-configured system like System76 Meerkat ION with the HDMI card but $450 was a bit much for a box that really was only going to run skype video. I have seen some others boxes built on the ATOM tech that look like they would do the job as well.

What the world needs is skype on my Blue-ray player just like Netflix so all I had to do was plug in the camera.

Thanks Again.

Paddy

---

### Post by cascade9 on 2011-01-06
Its really hard to know about comptibility porblems like that, I'm sorry to say.  

The only reason I found that thread was because of the search string I used.

---

