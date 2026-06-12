---
title: "Couple of installtion questions."
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by Mathew on 2005-05-05
Hey all,
First of all I want to say how great I think ubuntu is. I have migrated
over from running rh,fedora, and suse and I will say that this is my
absolute favorite.  I have some "basic" install questions and I have
been following the [www.ubuntuguide.org](www.ubuntuguide.org) which is very resourceful.

Question 1:
I will follow the guide and goto install one of their plug-ins or apps.
Everything starts to read the packages, etc etc. then I will get the 
error "E: Package transcode has no installation canidate."
For where the the "transcode" is it can be be replaced with 
"libdvdcss2" as well. So that is one question/error I am running into.

Question 2:
RealPlayer installs absolutely fine and creates everything it should
under sound/video.  However when I double-click the icon, nothing 
at all happens.  Any ideas?

Last question:
I am running a Dell Inspiron XPS with an integrated broadcom 570x series NIC.
However I also have installed a mini-pc wireless NIC (4390 chipset by broadcom) 
My integrated card is autodetected works great no problems.  When I goto device manager I see my wireless card.   In terminal when I lspci I see 0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03) ... Ideas?  Can I use ndiswrapper on the windows driver?   

Sorry about the long post.  I really appreciate all the help. 

Thanks
Mathew

---

### Post by Professor X on 2005-05-05
Welcome to the community.

Make sure your /etc/apt/sources.list contains the correct repositories.  The related section of the ubuntu guide must be followed exactly.  Then do a ```
sudo apt-get update
``` 

Realplayer has issues with esd, gnome's sound server.  You can configure it to release control of the sound card so that realplayer can use it.  Instructions to do this can be found [here](http://ubuntuforums.org/showthread.php?t=23840).  Another option would be to disable esd.

I can't help you with your last question.

---

### Post by Mathew on 2005-05-05
Thanks for your help with the software issues.  Real player
is functioning still fiddling with the other apps but they are 
slowly getting there.  Now I am just stuck with my wifi :)

Thanks again

---

