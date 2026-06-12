---
title: "Ubuntu 10.04 _Lost Keyboard"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Maxji on 2010-05-09
I installed Ubuntu 10.04 on my Dell Inspiron notebook.  I installed over Windows XP.  

During install I could not use the keyboard nor touchpad so I added an external mouse (usb) and keyboard (ps2 connection).   The install went well however when I rebooted the "external" mouse worked fine so I could click the user name on the login screen....however "external" keyboard was unresponsive.  The built-in keyboard/touchpad was also nonresponsive (no surprise there).

Any ideas how I can get my internal keyboard and touchpad working? or get through the login screen into Ubuntu?  If I can get on Ubuntu...how to activate my internal keyboard/touchpad?

---

### Post by vishwajeet.dusane on 2010-05-11
Hi 

If your mouse is still running and on login screen you are able to select konsole mode ? 
then you are in, on konsole mode your keyboard might work. Once logged in from konsole 

type 
```

sudo add-apt-repository ppa:pitti/sru-test

sudo apt-get update

sudo apt-get upgrade


```


and reboot, your machine keyboard will start working

---

### Post by Maxji on 2010-05-12
Hi vishwajeet.dusane,
Thanks for your response.  I don't know how to get to the konsole from the login screen.
I'm thinking perhaps its the ps2 connection of my keyboard to the notebook thats causing the problem as the usb connection of my mouse works fine.   My first thought is to buy an adaptor that will make my ps2 connection a usb connection.  If this doesn't work I'm thinking perhaps to reinstall 10.04 and set things up so that I don't get the login screen. 

If I can get in then I'll definitely try your suggestion to get the keyboard working.

Thanks so much.
best regards,
maxji

---

### Post by Maxji on 2010-05-15
Well.  I was able to login using a keyboard with a usb connection.  On re-booting for some unknown reason my notebook keyboard now works.   I've no idea why.

Wasn't able to connect to the internet.  Ubuntu did not recognize my Linksys compact wireless-G USB Network Adapter (model WUSB54GC).  

So the big challenge is to get on the internet....

---

