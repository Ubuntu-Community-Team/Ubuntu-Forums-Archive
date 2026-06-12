---
title: "How can I get the internet to work on my laptop???"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Alternative Solution on 2010-07-12
[SOLVED]

I just installed the latest ubuntu (10.4 or something) on my computer, and it seems nice, but it won't connect to my wireless internet.  Shouldn't it just automatically detect it? It doesn't seem to.

I'm not very computer savvy, but I figured that it may need to have drivers downloaded so it will work with my computer's wireless internet hardware.

But I don't think I can get any drivers if I'm not connected to the internet.

I do have another little USB wireless receiver, but that has an installation disk with an EXE file, which apparently does not work on ubuntu.

Note: My computer is a Dell Inspiron 1525.  Ubuntu is installed as the only operating system.  It is freshly installed.

So, any ideas? Your help is greatly appreciated.

[SOLVED]

---

### Post by TheNTW on 2010-07-12
Have you enabled wireless networking on your laptop ? ( Fn + the button where you see wireless icon :) ).
Do you see a wireless icon of any kind in top right corner ?

---

### Post by Alternative Solution on 2010-07-12
> **TheNTW said:**
> Have you enabled wireless networking on your laptop ? ( Fn + the button where you see wireless icon :) ).
Do you see a wireless icon of any kind in top right corner ?

I would, but it's grayed out.  It won't let me enable it. :(

---

### Post by samstreet101 on 2010-07-12
Try using your USB reciever. A lot of them work with Linux without installing any drivers, plug it in and see what happens

---

### Post by Alternative Solution on 2010-07-12
> **samstreet101 said:**
> Try using your USB reciever. A lot of them work with Linux without installing any drivers, plug it in and see what happens

I did that, and it does seem to recognize that it is in, but the internet still doesn't work.  Wireless internet is still set on disabled, and I can't get it enabled.

---

### Post by samstreet101 on 2010-07-12
is the device flashing at all? can it detect that networks are available? a screenshot would also be helpful

---

### Post by Alternative Solution on 2010-07-12
> **samstreet101 said:**
> is the device flashing at all? can it detect that networks are available? a screenshot would also be helpful

The device is not flashing

It isn't giving any indication that it can detect the networks.

The icon is just the internet bar thing faded out with a red exclamation point over it.  The tooltip says "No network connection"

And when I click it, it does list two wireless networks.  One is the USB network adapted and the other is what I assume is the laptop's adapter (broadcom).

Problem is, they are grayed out and there seems to be nothing I can do. :(

---

### Post by samstreet101 on 2010-07-12
Ok that usually indicates that the deivce isnt working or at least not without extra drivers. You could try installing windows wireless drivers utility but I don't think it will solve your problem. MIght need someone else's help here. Do you have access to any kind of wired connection? Any ethernet cables around?

---

### Post by Alternative Solution on 2010-07-12
> **samstreet101 said:**
> Ok that usually indicates that the deivce isnt working or at least not without extra drivers. You could try installing windows wireless drivers utility but I don't think it will solve your problem. MIght need someone else's help here. Do you have access to any kind of wired connection? Any ethernet cables around?

Well, my house has a modem hooked up to a router.  I'm not what cables to use-- like which ones are ethernet.

But would directly wiring it to the router or modem be safe?

---

### Post by samstreet101 on 2010-07-12
absolutely. its a sure way to get online for a start just until wireless issue is sorted out. Most ISPs provide an ethernet cable with their routers so you should have one there, maybe still in the box. It has a transparent square end that has many tiny little ribs on it and a small clip/safety catch on the top of it. Hope that helps

---

### Post by dino99 on 2010-07-12
which broadcom driver is installed (look into synaptic: search "broadcom") STA should work

---

### Post by Alternative Solution on 2010-07-12
> **samstreet101 said:**
> absolutely. its a sure way to get online for a start just until wireless issue is sorted out. Most ISPs provide an ethernet cable with their routers so you should have one there, maybe still in the box. It has a transparent square end that has many tiny little ribs on it and a small clip/safety catch on the top of it. Hope that helps

Ok, I just looked and there is a cable like what you described, but it's going from the modem to the router.  I would have to unplug it from the router to hook my laptop up.  So should I just plug my laptop into the modem? (I have DSL)

Hey thanks for your help so far btw.

---

### Post by Alternative Solution on 2010-07-12
> **dino99 said:**
> which broadcom driver is installed (look into synaptic: search "broadcom") STA should work

OK I searched and one thing came up.  It's "Modaliases for the Broadcom 802.11 Linux STA driver".  

Apparently it's already installed.

And apparently the one I have is 802.11b/g

---

### Post by samstreet101 on 2010-07-12
Its slightly odd that you have both a modem and a router. You usually don;t need a modem if you're connecting via DSL, just a router. I would try plugging the phone line into the router and then take the ethernet cable from the modem and plug it in so it's connecting the router to you're laptop.

---

### Post by efflandt on 2010-07-12
samstreet101 apparently is not very familiar with DSL, because you cannot simply skip the modem.  That would only work if the OP had a combination wireless/modem/router, and then it would not have a separate modem connected to it now.

It would help if you posted the output of **lspci** (or **sudo lspci -v**) related to your wireless device.  I imagine that you have BCM4311 or BCM4312 which should work with Broadcom STA or maybe Broadcom B43, but I have only used those Broadcom devices in 9.10 and not sure which works best in 10.04.

If you have an Ubuntu install CD for your version, insert it.  And if your system does not automatically ask if you want to add it to the repositories, open Synaptic, go to repositories, and check the box to add the CD.

Then close Synaptic if it was open, and go to System > Administration > Hardware drives and see if one of the drivers for your internal wireless is activated.  Note that if neither Broadcom STA nor Broadcom B43 is activated, you can only activate one or the other.  Whichever one you activate last will deactivate the other one.

One test to see if wireless is working is to try **sudo iwlist scan** from a terminal and see if anything shows up.  Even if you connect to one from the applet in the top panel, you may need to go to System > Preferences > Network Connects and check the boxes for that connection to "Connect automatically" and "Available to all users".

Once you get it working, you can uncheck the CD in Synaptic repositories.

---

### Post by samstreet101 on 2010-07-12
sorry was referring to the need for a separate modem and router, not the ability to modulate/demodulate. Not sure about older routers but I've been through many in the last few years and never needed a separate modem.

---

### Post by sgenome on 2010-07-12
I do have the same problem with "Alternative Solution". I have installed ubuntu desktop edition 10.04 and I couldn't get my laptop connected through wireless. The wireless option in the right upper corner was disable. I could connected with wired through the router. I'm using Dell XPS 1330 with the wireless button set to on. I have also tried to install the windows drivers but it seems ubuntu didn't recognize .exe extension. I'm a beginner for linux and want to try it. Thank you.

---

### Post by realzippy on 2010-07-12
> **sgenome said:**
> I do have the same problem with "Alternative Solution". I have installed ubuntu desktop edition 10.04 and I couldn't get my laptop connected through wireless. The wireless option in the right upper corner was disable. I could connected with wired through the router. I'm using Dell XPS 1330 with the wireless button set to on. I have also tried to install the windows drivers but it seems ubuntu didn't recognize .exe extension. I'm a beginner for linux and want to try it. Thank you.

Can you open your own thread?Thats threadnapping.  ;)
And post the output from

```
lspci
```

---

### Post by sgenome on 2010-07-12
> **realzippy said:**
> Can you open your own thread?Thats threadnapping.  ;)
And post the output from

```
lspci
```

Oh I'm so sorry, I thought that since we have the same problem, so I just need to join in and solved it together. Once again, I'm sorry.

---

### Post by realzippy on 2010-07-12
> **sgenome said:**
> Oh I'm so sorry, I thought that since we have the same problem, so I just need to join in and solved it together. Once again, I'm sorry.
Wrote you a PM.Problem is only the same if wireless chip/ubuntu-version is exactly the same..

---

### Post by Alternative Solution on 2010-07-13
Hey everyone,

Thanks for you help.  I finally got wireless to work.  I connected directly to the router with a ethernet cable, and then I was able to download the drivers that I needed for wireless.  

This thread can be closed.

Thanks again everyone.

---

