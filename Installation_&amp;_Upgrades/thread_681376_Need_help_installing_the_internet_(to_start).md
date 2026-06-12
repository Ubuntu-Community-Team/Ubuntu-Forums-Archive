---
title: "Need help installing the internet (to start)"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by mike9682000 on 2008-01-28
Hello,

First, here is my configuration:

AMD 64FX62
2 GB RAM
Radeon X1950
NVIDIA nForce Networking Controller (network card on the motherboard - connected to a Telus 2wire modem-router-switch)
D-Link DGE 530T (not connected)
Nothing wireless.

Tried to test drive Ubuntu 7.10. The graphic interface would not load (got a black screen after the progress bar)
I downloaded the CD - text only version. Checked OK. Installed Ubuntu on a SATA hard drive. Upon startup, the system will not load the graphic interface. I got to the terminal and tried to install the proprietary ATI driver, but noticed it required internet connection.
The MAC adress is already registered with the ISP.

I tried:

sudo /etc/init.d/networking restart

and got:

"Reconfiguring Network Interfaces
ignoring unknown interface eth0=eth0"

From what I figure, there must be a way to input my ISP username and password somewhere.

How do I setup my internet connection FROM THE TERMINAL only?

Much appreciated
Mike

---

### Post by Partyboi2 on 2008-01-29
When you are at a terminal have you tried to reconfigure xserver and choosing the vesa driver? If this works it will give you a working desktop while you sort out your internet and graphics problems.
```
sudo dpkg-reconfigure xserver-xorg
```choose "vesa" for the driver and answer all the questions, if unsure just choose the default answers.
then 
```
startx
```

---

### Post by Carl H on 2008-01-29
> **mike9682000 said:**
> 
From what I figure, there must be a way to input my ISP username and password somewhere.


You usually put  those into your router, not your PC. Was your internet connection working properly before you started installing Ubuntu?

You may need to boot from a Live CD so you can connect to the router and enter your account details.

---

### Post by mike9682000 on 2008-01-29
> **Partyboi2 said:**
> When you are at a terminal have you tried to reconfigure xserver and choosing the vesa driver? If this works it will give you a working desktop while you sort out your internet and graphics problems.
```
sudo dpkg-reconfigure xserver-xorg
```choose "vesa" for the driver and answer all the questions, if unsure just choose the default answers.
then 
```
startx
```

Set VESA, introduced startx and got:

(EE) VESA(0): SET VBE MODE FAILED
Fatal Server error
AddScreen/ScreenInit failed for driver 0.

---

### Post by mike9682000 on 2008-01-29
> **Carl H said:**
> You usually put  those into your router, not your PC. Was your internet connection working properly before you started installing Ubuntu?

You may need to boot from a Live CD so you can connect to the router and enter your account details.

Indeed my interned connection does work. I am writing this using the same computer under Vista. Vista is on SATA 1 drive, Ubuntu is on SATA 2. I make the switch from BIOS.

If I recall correctly, Vista did ask me for the username and password when I installed it. I could be wrong.

I never needed to provide my ROUTER with my ISP username and password...

The 2 Wire is an phone line connected ADSL modem - router -  switch with wireless capability (currently disabled)

---

### Post by Pumalite on 2008-01-29
You need a real router to provide you with DHCP

---

### Post by Carl H on 2008-01-31
> **mike9682000 said:**
> Vista did ask me for the username and password when I installed it. I could be wrong.

I never needed to provide my ROUTER with my ISP username and password...


Is this an actual router that plugs into your ethernet port, or a USB modem/router device?

What's the make and model of it, and where did you get it? Was it provided by your ISP?

---

