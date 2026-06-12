---
title: "no unity bar no top bar"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by avidesh on 2012-10-19
I upgraded to ubuntu 12.10 today. after reboot I do not get unity side bar launcher or top bar. I can't start any applications

What could be the issue?

---

### Post by proggy on 2012-10-19
You have an unsupported NVIDIA CARD for Unity

---

### Post by avidesh on 2012-10-19
I use onboard graphics (IGE).

So how do I get ubuntu working now?

---

### Post by avidesh on 2012-10-19
Another observation is that when I boot from USB and try ubuntu 12.10 all bars (launcher + top bar) appear properly and work.

The problem seems to be with the upgraded system.

how do I debug

---

### Post by proggy on 2012-10-19
Thats because the live cd uses open source drivers, you&#8217;ll have to install them by terminal (open terminal with [COLOR=#666666][FONT=Helvetica Neue]Ctrl+Alt+T) and install the nouveau drivers.[/FONT][/COLOR]sudo add-apt-repository ppa org-edgers/nouveau
sudo aptitude update && sudo aptitude install xserver-xorg-video-nouveau

---

### Post by avidesh on 2012-10-20
I already have latest nouveau drivers. That is the message I get when I try to install those.

---

### Post by avidesh on 2012-10-20
Now I get the following message

The system is running in low-graphics mode

Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

Post that I get a screen asking me to select the options 
[LIST]
[*]Run in low Graphics mode
[*]Reconfigure graphics
[*]Troubleshoot the error
[*]Exit to console
[/LIST]

Default is run in low graphics

I managed to go to the next screen where it asked 'How would you like to reconfigure your display?

options:
[LIST]
[*]Use default (generic) config
[*]use your backed-up config
[/LIST]

Tried selecting both but nothing happens.

---

### Post by DwalerXIII on 2012-10-20
I did a fresh install and all worked well using the nouveau (open source) driver. After installing the binary driver I got the same problem as mentioned above. 
This is strange because that driver worked with 12.04.

---

### Post by proggy on 2012-10-20
> **avidesh said:**
> Now I get the following message

The system is running in low-graphics mode

Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

Post that I get a screen asking me to select the options 
[LIST]
[*]Run in low Graphics mode
[*]Reconfigure graphics
[*]Troubleshoot the error
[*]Exit to console
[/LIST]

Default is run in low graphics

I managed to go to the next screen where it asked 'How would you like to reconfigure your display?

options:
[LIST]
[*]Use default (generic) config
[*]use your backed-up config
[/LIST]

Tried selecting both but nothing happens.
When you upgraded to 12.10 did you get a warning stating that your card was not supported? If so you will have to install 12.04 lts until it can run the newest version of Unity.

---

### Post by avidesh on 2012-10-21
thanks for the reply.

Looks like I'll have to buy new graphics card to sort this out :)

---

