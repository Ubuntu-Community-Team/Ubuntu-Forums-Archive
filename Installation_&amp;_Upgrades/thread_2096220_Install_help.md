---
title: "Install help"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by k1fdp on 2012-12-19
I am installing Ubuntu 12.10 I want to install it on my acer laptop. I am currently using windows 7. After installing Ubuntu and then restarting, I get a purple blank screen for about 1 minute then it goes black / off. I have to hold the power button down to restart my laptop.

What am I doing wrong? Has this happened to others and how do I get past this so I can use it?

Thanks!!

---

### Post by k1fdp on 2012-12-19
anyone?

---

### Post by darkod on 2012-12-19
Did you try it in live mode first? Did it boot the desktop ok?

---

### Post by k1fdp on 2012-12-19
I downloaded it via windows installer, no usb or disk and used the wubi icon to begin the installation. When it prompted to reboot, I did so. It then gave me an option to start via windows 7 or ubuntu and I chose ubuntu. The screen went purple, with no icons and then black / blank.
 
I uninstalled ubuntu and reinstalled it and I get the same results.

---

### Post by snowpine on 2012-12-19
A good first step is to run Ubuntu as a Live DVD or Live USB to determine whether or not it is compatible with your hardware.

Instructions here, follow Step 1 only and choose "Try Ubuntu" (do not proceed to Step 2 yet): [http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

I also recommend that you use the forum Search feature for your specific computer model number, to see if other users have had this problem and how they solved it. Also good to tell us this info so we can help: model number, CPU, RAM, video card, etc.

---

### Post by darkod on 2012-12-19
It sounds like video driver issue, but since you are using wubi and not a proper installation, it's more difficult to troubleshoot and try to fix. Wubi is just virtual ubuntu inside windows. Just for a quick test.

It's recommended to run ubuntu on its own partition. I don't use wubi so can't really give you any specific advise since it's slightly different from ubuntu. It might be video issue but installing a driver inside wubi would be slightly more difficult than into ubuntu.

---

