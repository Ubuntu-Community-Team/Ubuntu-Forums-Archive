---
title: "Hardy Heron LiveCD Freezes."
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Eax.exe on 2008-05-18
Hi :)

I ordered the LiveCD from SendIt before Hardy Heron came out, and I got it a couple of days ago.
Now I´m trying to install over my Feisty Installation on my Acer TravelMate 4310.

The problem is that when I try to use the LiveCD to install HH it freezes when loadinng :confused:

I installed Feisty via the livecd to.

Here´s the specs:
AMD Mobile Sempron 3500+ / 1.8 GHz
RAM: 512 MB 
80GB
ATI Radeon Xpress 1100

Any help would be greatly aprreciated :)

---

### Post by Pumalite on 2008-05-18
Use the Alternate CD to install.

---

### Post by Eax.exe on 2008-05-18
> **Pumalite said:**
> Use the Alternate CD to install.

Which Alternate CD?
Where do I get it? 
Why doesn´t the LiveCD work?

---

### Post by Pumalite on 2008-05-18
Download it from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check box below sign 'Start Downloads'
You have a graphics problem. You can configure your xserver at the end of the installation if necessary.

---

### Post by Eax.exe on 2008-05-18
> **Pumalite said:**
> Download it from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check box below sign 'Start Downloads'
You have a graphics problem. You can configure your xserver at the end of the installation if necessary.

Okay thanks :)
Why do I have a graphics problem?
And how do I configure it/what to configure in it?

---

### Post by Pumalite on 2008-05-18
'ATI Radeon Xpress 1100'
At the end; if you end up with a blank screen:
Ctrl+Alt+F1 to get command line,
sudo dpkg-reconfigure xserver-xorg
Choose vesa as the driver
Later install appropriate driver.

---

