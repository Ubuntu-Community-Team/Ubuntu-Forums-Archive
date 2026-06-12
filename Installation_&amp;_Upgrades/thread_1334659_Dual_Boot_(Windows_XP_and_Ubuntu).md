---
title: "Dual Boot (Windows XP and Ubuntu)"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Muhnamana on 2009-11-22
So I've heard you need to enable the wireless card (wireless light on) before booting Ubuntu. 

See link.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

My question is, how and where do I tell the wireless card to be enabled before booting Ubuntu?

---

### Post by wilee-nilee on 2009-11-22
> **Muhnamana said:**
> So I've heard you need to enable the wireless card (wireless light on) before booting Ubuntu. 

See link.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

My question is, how and where do I tell the wireless card to be enabled before booting Ubuntu?

Is your card listed on the page of your link? You should also list your card here so anybody using the same can confirm.

You also have another thread basically addressing a problem with a wireless card.

---

### Post by Muhnamana on 2009-11-22
Yeah sorry I need to close that other thread as I decided to dual boot instead of just Ubuntu on my system. 

Yes I have a Broadcom card model BCM4318.

---

### Post by schwim on 2009-11-22
Thanks to another helpful person on this forum, I was able to get the same wireless card working by:

1) Installing Ubuntu
2) connect to a wired connection
3) Run system updates
4) Run restricted drivers app and choose to enable the driver for the broadcom chip.
5) Profit!

It's been working perfectly since.

thanks,
json

---

### Post by wilee-nilee on 2009-11-22
> **Muhnamana said:**
> Yeah sorry I need to close that other thread as I decided to dual boot instead of just Ubuntu on my system. 

Yes I have a Broadcom card model BCM4318.

I think the dual boot is a good idea especialy if you own a license to windows, this actually enables you to get a cheaper/upgrade version to W7 if you have a legal version.

So I see that your card is listed and it gives some instructions on what you have to do on the Ubuntu side, I have never had to do this, but many on the forum have. So if the instructions don't make sense then let the forum know through this thread or close this one and go to the wireless section or ask the mods to move it over there, I think your on the right track.
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by wilee-nilee on 2009-11-22
> **schwim said:**
> Thanks to another helpful person on this forum, I was able to get the same wireless card working by:

1) Installing Ubuntu
2) connect to a wired connection
3) Run system updates
4) Run restricted drivers app and choose to enable the driver for the broadcom chip.
5) Profit!

It's been working perfectly since.

thanks,

json


Good job I forgot to mention this route. ;)

---

### Post by Muhnamana on 2009-11-22
I'm very very new to Ubuntu. I wanted to learn something new so many of the things on here is liking reading a foreign language.

What should be my first step to get my wireless card working? Sorry I am a noob and will take some time to get in the swing of things.

Thanks.

---

### Post by Muhnamana on 2009-11-22
> **schwim said:**
> Thanks to another helpful person on this forum, I was able to get the same wireless card working by:

1) Installing Ubuntu
2) connect to a wired connection
3) Run system updates
4) Run restricted drivers app and choose to enable the driver for the broadcom chip.
5) Profit!

It's been working perfectly since.

thanks,
json

Aight. Ubuntu is installed. Once I connect to the wired connection, where is the system update at?

---

### Post by schwim on 2009-11-22
On the top task bar, click "System", Then scroll down to "Administration" then click "Update Manager".

Once you've updated and restarted, Click "System" scroll down to "Administration" then choose "Hardware Drivers".  Let it detect the card, then choose to activate the driver.  Then just restart again.

---

### Post by Muhnamana on 2009-11-22
> **schwim said:**
> On the top task bar, click "System", Then scroll down to "Administration" then click "Update Manager".

Once you've updated and restarted, Click "System" scroll down to "Administration" then choose "Hardware Drivers".  Let it detect the card, then choose to activate the driver.  Then just restart again.

Great, thank you. Let me try this and see what happens.

---

### Post by Muhnamana on 2009-11-22
> **schwim said:**
> On the top task bar, click "System", Then scroll down to "Administration" then click "Update Manager".

Once you've updated and restarted, Click "System" scroll down to "Administration" then choose "Hardware Drivers".  Let it detect the card, then choose to activate the driver.  Then just restart again.

Sweet! Thank you so much for the help. You don't understand the frustration I had today with this. Again, thank you!

---

### Post by Muhnamana on 2009-11-22
Now, where do I mark this thread as solved?

---

### Post by schwim on 2009-11-22
Very glad you're up and running.

Upper right of the first post on the page, you'll find a link called "thread tools".  Click that and choose to mark the thread as solved.

---

