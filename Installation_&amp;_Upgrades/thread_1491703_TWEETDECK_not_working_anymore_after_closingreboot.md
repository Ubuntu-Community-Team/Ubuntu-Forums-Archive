---
title: "TWEETDECK not working anymore after closing/reboot"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by sanoelk on 2010-05-23
I was able to successfully install Tweetdeck and Adobe Air using the instructions here: [http://www.technixupdate.com/install-tweetdeck-on-ubuntu-linux/](http://www.technixupdate.com/install-tweetdeck-on-ubuntu-linux/)

BUT after I closed the program, when I tried to re-open it, it wouldn't load anymore. It would show that it is "Starting Tweetdeck" but it would not lead to anything - it would just close.

So I tried to uninstall everything and re-install from scratch. But the same thing happened - the program would not load.

I tried to isolate the issue by trying to install another AIR application. When I double-click on the icon or click on install using Adobe AIR, it would not run. So that only means that the issue is with Adobe AIR.

Here's what I did:

Uninstall Tweetdeck.

Download the Adobe Air 2 Runtime Release Candidate here: *[http://labs.adobe.com/downloads/air2.html](http://labs.adobe.com/downloads/air2.html)*
(I downloaded the .bin one. Filename: air2_rc1_runtime_lin_051110.bin)

Install air2_rc1_runtime_lin_051110.bin by entering the following commands in the Terminal:

*chmod +x air2_rc1_runtime_lin_051110.bin*

*sudo ./air2_rc1_runtime_lin_051110.bin* (It will ask for your password.)

It will then load the installer. Go through the step-by-step process until it's finished.

Install Tweetdeck again (Just double-click on its .air file).

And there you have it. :)

---

### Post by arturhoo on 2010-05-25
Thank you very much!

Just what I needed

---

### Post by kartook on 2012-07-15
How to install tweetdekck clinet on the ubuntu ... 

I made good stuffs 


[http://bit.ly/MvAyJL](http://bit.ly/MvAyJL)

---

### Post by oldos2er on 2012-07-15
Please don't bump old threads.

---

