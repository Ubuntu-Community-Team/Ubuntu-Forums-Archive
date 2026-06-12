---
title: "Upgrade to 10.04 Causes Blackberry to Constantly Restart"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KFwLsKvVAs on 2010-03-17
So I had messed up my 9.10 installation to the point where I needed to reinstall, and I decided to install 10.04 alpha 3.  My blackberry, which has worked flawlessly with ubuntu on 8.10, 9.04, 9.10 was plugged in via usb when I did the installation.  

So the install went fine, except I noticed my blackberry had started turning on and off any time the computer would shut down to do a restart or whatever.  Which was sort of irritating but not a huge deal.  Except then once 10.04 was completely installed and running off the hd and not the livecd, my blackberry would just sit there and shut down completely, then come up with a white screen and a spinning hour glass and sit like that forever, and then do it all over again endlessly.  

I have a blackberry pearl 8110, i tried installing opensync-plugin-barry, it used to work just fine and now it does not.  Has anybody else experienced this problem, does anybody know any solutions?

---

### Post by KFwLsKvVAs on 2010-03-19
anybody?

---

### Post by soltanis on 2010-03-19
Sorry, I don't have a Blackberry, but have you tried either reverting to 9.10 and seeing if that helped, or does your phone do this even if it's not connected to your computer?

If it does, you might need to do a hard reset (and lose all your settings and apps, I presume :/)

---

### Post by KFwLsKvVAs on 2010-03-28
No, I haven't tried reverting, however I had installed Fedora 13 alpha and it worked fine plugged in via usb, recognized media card and everything.  

it doesn't do the constant restart thing unless it's plugged in to the usb port, if I unplug it it finishes the restart and starts up normally again.

---

### Post by warrenc285 on 2010-03-30
I'm having the same problem with my Blackerry.

---

### Post by Sef on 2010-03-30
Moved to Lucid.

---

### Post by SteveH on 2010-04-12
Yep, same problem.

Acer Aspire 2930 running Kubuntu 10.04 Beta 2.

---

### Post by KFwLsKvVAs on 2010-04-14
Anyone know if a bug has been filed already?

---

### Post by SteveH on 2010-04-14
Bug now filed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562903](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562903)

---

### Post by SteveH on 2010-04-14
And temporary fix provided:

sudo mv /lib/udev/rules.d/85-hdparm.rules /lib/udev/rules.d/85-hdparm.rules.disabled

---

### Post by KFwLsKvVAs on 2010-04-20
ah, the fix worked perfectly, thank you so much this was a huge irritation for me.

---

### Post by kyleflan on 2010-04-21
Unfortunately, that fix didn't work for me. I'm using a Blackberry Curve 8530. Any time I connect it to my laptop via USB it asks for my devices security code to grant Simple Media Transport (or something along those lines) and before I can enter my security code, my phone restarts.

Not a huge deal, but if anyone finds a fix, it'd be great.

---

