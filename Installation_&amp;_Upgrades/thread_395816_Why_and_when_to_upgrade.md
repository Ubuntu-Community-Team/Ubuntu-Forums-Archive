---
title: "Why and when to upgrade"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by tc101 on 2007-03-28
I am relatively new to linux and ubuntu.  I installed Edgy (6.10) a few months ago and after a few weeks got everything working the way I wanted and vowed not to use windows for a year.

Now Fiesty is coming out and I am wondering if I should upgrade when the official release is available.  I have a fear that I will create lots of problems and not be able to use my computer and spend weeks getting it working just right again, just like when I first installed Edgy.  On the other hand I would like to get any new features in the new release.  

I have read that each release is supported for 18 months, so I guess I could skip half the upgrades and just upgrade once a year.

How do you decide to upgrade of not if your system already does everything you want?

---

### Post by esodin on 2007-03-28
Like you, I am also new to Ubuntu. It sounds as if you are pretty happy with the way things are. I did upgrade to Feisty - and I am happy that I did. I had some freaky issue with my USB under Edgy. Ubuntu would not boot if anything was plugged into a USB hub other than the motherboard hub, and when I shut down the computer power would stay on for the USB ports. Feisty fixed this and - even the Beta - seems more stable than Edgy.

All my programs worked after the upgrade (including Beryl and Windows programs like CS:S under Wine). Perhaps the best thing for you is to wait for the official release (next month) of Feisty, but I my experience suggests the you can do it without much fear of messing up your current setup. :)

---

### Post by Drezliok on 2007-03-28
I'd wait for Feisty to come out of beta. In fact I think I'll wait longer because I tried feisty beta and it was buggy [for me] and my of my preferred programs were not ready for mainstream use. So I downgraded back to Edgy. After Feisty is released I'll get my ISOs


If it Ain't Broke don't Fix it.

---

### Post by tc101 on 2007-03-28
Thanks for your thoughts.  If I do upgrade I will wait for the regular release.  I was not thinking of using the beta.  I was just asking so I could make a decision later.

How hard is it to downgrade once you upgrade if you have a problem?

I have a high speed cable connection.  If all goes well, how long will the upgrade take?

---

### Post by esodin on 2007-03-28
My download was 900Mb. It took 40 min. The upgrade from 6.10 to Feisty Beta took 22.5 min on my machine (I timed it)

---

### Post by Chappy7777 on 2007-03-28
> **esodin said:**
> My download was 900Mb. It took 40 min. The upgrade from 6.10 to Feisty Beta took 22.5 min on my machine (I timed it)
Esodin, what did you do to upgrade? Did you have to uninstall Edgy before installing Feisty? As in, did you have to reformat your HDD or did you install Feisty on top of Edgy? 
So far, any time I have up or downgraded Ubuntu, I have uninstalled the existing OS every time, before installing the new one.
Chappy

---

### Post by esodin on 2007-03-29
I installed Feisty on top of Edgy. I followed the instructions here: [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

It was basically like any other update - it only took longer. I did, however, have some issues with my graphics driver. I had, in Edgy, used the proprietary nVidia driver.  

When Feisty booted the first time it could not load the desktop. 
 - I resolved this by selecting the VESA driver when prompted for a "different driver". 
The program made some changes to my xorg.conf file. 
- This allowed me to start Feisty with a desk-top. 
The update manager found a lot of new updates witch a said "yes" to install
I then re-installed the nvidia driver (with Synaptic package manager) and restarted the desktop with "sudo init 1" then "sudo init 2" from the terminal.

All the eyecandy (Beryl, desctop, gDesklets, etc) was as I left it in Edgy before the conversion. Very smooth. :)

---

### Post by rillip on 2007-03-29
Where can you find a good description of the differences between versions?  I've looked at this before, and never had much luck in figuring it out.  I'm using Dapper and quite like it, but am not opposed to upgrading, per say, but at the same time I don't really see the point in doing it for no reason either.  Like Drezliok said, if it ain't broke don't fix it, but then again shiney and new is always nice. :)

Edit: I checked out the link above and know that it'd be a more inovled process upgrading to Edgy then to Fiesty if I felt like doing so.

---

### Post by Roobert on 2007-03-29
> **rillip said:**
> Where can you find a good description of the differences between versions?  I've looked at this before, and never had much luck in figuring it out.  I'm using Dapper and quite like it, but am not opposed to upgrading, per say, but at the same time I don't really see the point in doing it for no reason either.  Like Drezliok said, if it ain't broke don't fix it, but then again shiney and new is always nice. :)

Edit: I checked out the link above and know that it'd be a more inovled process upgrading to Edgy then to Fiesty if I felt like doing so.

Well, exactly; I have Dapper running right now, and although everything is stable, I don't want to be stuck using OO.org 2.02 and Firefox 2.0 forever either. 

Does anyone know if the upgrade from Dapper to Edgy has been made smoother than it was 6 months ago? Specifically, in terms of video card/driver detection and error handling.

---

