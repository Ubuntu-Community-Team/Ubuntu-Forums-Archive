---
title: "Upgrading Videocard soon, Have any tips?"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Drezliok on 2006-12-12
I'm planning on getting a new Nvidia Videocard after New Years. Although I have toyed with Linux and now moved into Xubuntu as my primary O/S I was wondering just how I would go about installing the the card for Ubuntu.

I'm replacing a Nvidia Geforce 5200 with a new Nvidia card, hopefully a 6800 but I'm looking for better options.

Any tips and or instuctions?


Thankyou for your time.
Drezliok

---

### Post by drphilngood on 2006-12-13
I would get a GeForce 7900GS.  Newegg has them for $180 now and they perform nicely and usually overclock well.

---

### Post by Drezliok on 2006-12-13
> **drphilngood said:**
> I would get a GeForce 7900GS.  Newegg has them for $180 now and they perform nicely and usually overclock well.

Not what I had in mind [it must also be a AGP card], I was looking for more help wth the actual process of replaceing the card. I don't want ot botch the install because I can't get a peice of hardware running. reconfiguring the Xserver with dpgk [that was off the top of my head at 4am I'm sure it's wrong but I can remember the whole line.]

I don't know why I didn't say this the first time, it seems so important.

Ok, I want to manual change the Xserver config becuase when ever I use the reconfigure package command I screw it up.


I'm sorry if this makes no sense. I got up because I couldn't stay asleep at 4am. So I'm tired and not thinking really straight. 
[yeah I forbid the use of sudo when I'm like this, I've killed my machine like that many times]

---

### Post by gn2 on 2006-12-13
What is the reason for changing the card?

---

### Post by drphilngood on 2006-12-13
> **Drezliok said:**
> Not what I had in mind [it must also be a AGP card], I was looking for more help wth the actual process of replaceing the card. I don't want ot botch the install because I can't get a peice of hardware running. reconfiguring the Xserver with dpgk [that was off the top of my head at 4am I'm sure it's wrong but I can remember the whole line.]

I don't know why I didn't say this the first time, it seems so important.

Ok, I want to manual change the Xserver config becuase when ever I use the reconfigure package command I screw it up.


I'm sorry if this makes no sense. I got up because I couldn't stay asleep at 4am. So I'm tired and not thinking really straight. 
[yeah I forbid the use of sudo when I'm like this, I've killed my machine like that many times]

You should be able to just change them out if you stay with nVidia since Nvidia drivers support most cards and you already have the drivers installed.  If you need to reconfigure your xserver, enter:

```
sudo dpkg-reconfigure xserver-xorg
```

Here is a nice guide for installing the new GPU:
[A Video Card Upgrade HOWTO]("http://www.linuxjournal.com/comment/reply/8511")

---

