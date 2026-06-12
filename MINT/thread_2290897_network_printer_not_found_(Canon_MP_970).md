---
title: "network printer not found (Canon MP 970)"
date: 2015-08-16
forum: MINT
---

### Post by Peter_Huebner on 2015-08-16
I was hoping to hitch a ride with a year-old thread on this forum where somebody could not get their Canon MP970 working.

My problem starts at a much more basic level: the laptop simply can't see the printer. I have started the New Printer process, gone to 'find network printer' and ... nothing.
I assume "Host" in that window stands for either the IP of the router or  the IP of the printer on the LAN, but neither IP works when I try it on the cups (what does cups stand for, anyway?) - it simply doesn't register. The printer works fine with 3 windows machines over the same router. There are various options for ipps but I can't  make heads or tails out of that lot. 

No idea what to do - I'm a complete linux noob. Incidentally I am using Mint, not Ubuntu, but they seem to have the same mechanisms  ...

---

### Post by PaulW2U on 2015-08-16
*Thread moved to **MINT*** as you're not using an official Ubuntu flavour.

---

### Post by Peter_Huebner on 2015-08-16
Unfortunately shortly after I posted this,  Mint crashed alltogether - I tried to open firefox to test an alternative method suggested in a tutorial, by using the browser, but it would not  start the browser, crashed to a black screen instead and the USB stick installation of Mint won't boot any more  at all. 

I tried once more with the live version, but that, also, can't see any network printers.

---

### Post by yancek on 2015-08-16
>  (what does cups stand for, anyway?) 

Common UNIX Printing System

Ask the obvious, is it plugged in and turned on when you make these efforts.  If yes, is it connected to one of the other computers?  If not, give the link below a read as it has some suggestions that may help.

---

### Post by ajgreeny on 2015-08-16
Have you, or perhaps I should now say, had you, installed a printer driver package of any kind from Canon?

I'm not sure how well supported that printer is, but in the past when I used a Canon MFP I had to go to the Canon site to find the driver for both printer and scanner; then the printer worked brilliantly.  A quick search suggests that Canon do not have their own driver for that model but they suggest that the OS may support it, which I presume means cups.

Try again when you get your OS up and running and come back again if you still have ongoing problems.

---

### Post by Peter_Huebner on 2015-08-16
@yancek - printer is connected to the router (network printer!) and yes, it was turned on. That's how I managed to find out what IP it's sitting at ... 

@ajgreeny - no support from Canon, no driver package available on their site. There was a thread on the ubuntu forums a year ago and everybody there reported that Ubuntu was able to see the printer even if they had not managed to find a driver & get it to print initially,  so maybe I'll have to download a vanilla ubuntu iso and give that a try.

---

### Post by Peter_Huebner on 2015-08-17
> **PaulW2U said:**
> *Thread moved to **MINT*** as you're not using an official Ubuntu flavour.

Well since Mint crashed horribly, trashing the install on my 16 Gb usb3 stick with it, I downloaded and installed Ubuntu. 

My problem has not changed, the 'add-printer' software is to all appearances the same, it still won't find my printer regardless of 
my using the  router (192.168.1.1) or the printer IP (192.168.1.17) as host. 

So I haven't got any further yet.

---

### Post by trtle on 2015-09-09
I had the same problem with my printer until I found out the router had 'wireless isolation' turned on.
Secondly I had to turn on like every plugin on the router to share information on the network plug-in-play, UPnP, etc. I forget all what but until I did that nothing would really work without strong-arming, port 631.

---

