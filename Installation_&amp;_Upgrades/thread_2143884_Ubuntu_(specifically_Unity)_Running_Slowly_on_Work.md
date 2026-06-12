---
title: "Ubuntu (specifically Unity) Running Slowly on Work PC"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by Phugoid on 2013-05-10
Hi there,

Been using Linux a few years now and a massive fan... decided to change over to it at work as well as at home... well, dual booting with Win 7, at least. Anyway, I installed Ubuntu 13.04, but the GUI seems REALLY sluggish... especially when I try to access the dash or resize windows, or do anything with the unity toolbar. Programs themselves seem to run just fine, and the terminal is as rapid as usual, but seems the computer just isn't dealing with unity.

I actually tried to install 12.10 on it a few weeks ago and had the same problem. Interestingly, I did have ubuntu 12.04 running on this machine on its own at one point last year (no dual boot), and I don't recall these problems back then. But then I had to install Windows for access to a particular software, and now that I'm trying to dual boot I'm getting this problem.

I'm guessing it's something to do with graphics card drivers or SOMETHING along those lines. But maybe you guys have some interesting leads for me to follow...

Cheers.

---

### Post by Mark Phelps on 2013-05-10
Between 12.04.1 and 13.x, AMD dropped support for their restricted drivers for their HD 2x/3x/4x series chipsets.  If your PC is using one of those, you are stuck using the open-source driver now -- which should not be really SLOW, as I'm doing the same and don't notice any lag, but it would help to know what video chipset you are using.  Open a terminal, enter "lspci" and look for the line containing "VGA".

---

### Post by snowpine on 2013-05-10
Completely pointless to speculate unless you tell us about your hardware....

;)

---

### Post by Phugoid on 2013-05-15
> **Mark Phelps said:**
> Between 12.04.1 and 13.x, AMD dropped support for their restricted drivers for their HD 2x/3x/4x series chipsets.  If your PC is using one of those, you are stuck using the open-source driver now -- which should not be really SLOW, as I'm doing the same and don't notice any lag, but it would help to know what video chipset you are using.  Open a terminal, enter "lspci" and look for the line containing "VGA".

Hi there, sorry for taking a while to reply:

The VGA related output from lspci is the following:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV620 PRO [Radeon HD 3470], so it is indeed one of the drivers you said are now dropped...

But it is REALLY slow... anytime I try to use the dash or the unity toolbar, it lags sometimes up to 10 seconds.

---

### Post by Mark Phelps on 2013-05-15
While you are relegated top the open-source Radeon drivers, I'm in the same boat and haven't noticed any lag running 12.10.  With 12.04.1, you would be able to install the fglrx drivers easily, but that would only really make a difference running hardware-intensive gaming.  In day-to-day desktop use, you should see no difference.

Something else must be at work.  Please post the specs of your PC.

---

