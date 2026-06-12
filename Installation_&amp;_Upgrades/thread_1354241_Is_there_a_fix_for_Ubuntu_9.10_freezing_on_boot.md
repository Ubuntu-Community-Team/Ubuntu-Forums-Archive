---
title: "Is there a fix for Ubuntu 9.10 freezing on boot?"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by WRATGUT? on 2009-12-13
When the public release came out for Ubuntu 9.10 I downloaded and installed it, but right after I log in everything freezes. I've noticed lots of other people have this problem and I was wondering if it's fixed already.

---

### Post by WRATGUT? on 2009-12-13
Anyone?

---

### Post by WRATGUT? on 2009-12-19
bump

---

### Post by chrisme on 2009-12-20
I have just upgraded from 9.04 to 9.10 and i have the same problem.
Does anybody have an answer for this problem?

---

### Post by snowpine on 2009-12-20
I'm not sure whether everyone is having the same problem,  or lots of people are having different problems. :)

Karmic froze for me 5-10 seconds after logging in. This is on a  computer with Intel 950 integrated graphics. The simple fix was to disable Compiz desktop effects; maybe that will work for you?

---

### Post by chrisme on 2009-12-20
> **snowpine said:**
> I'm not sure whether everyone is having the same problem,  or lots of people are having different problems. :)

Karmic froze for me 5-10 seconds after logging in. This is on a  computer with Intel 950 integrated graphics. The simple fix was to disable Compiz desktop effects; maybe that will work for you?

How to do this?

---

### Post by darkod on 2009-12-20
> **WRATGUT? said:**
> When the public release came out for Ubuntu 9.10 I downloaded and installed it, but right after I log in everything freezes. I've noticed lots of other people have this problem and I was wondering if it's fixed already.

I installed it also as soon as it was released on both my netbook and desktop and it's working just fine... Did you try to change the video driver?

---

### Post by chrisme on 2009-12-20
> **darkod said:**
> I installed it also as soon as it was released on both my netbook and desktop and it's working just fine... Did you try to change the video driver?

It does not give you the chance to do anything. 5 seconds after the login is freezing. Is there any other way to change the driver?

---

### Post by darkod on 2009-12-20
> **chrisme said:**
> It does not give you the chance to do anything. 5 seconds after the login is freezing. Is there any other way to change the driver?

Yes, in the grub menu you select the recovery mode entry, not the normal mode. In the next menu select something like "root with networking" to have internet access. That will load a text based command prompt.

If you have ATI or Nvidia card/chipset, at the command prompt install EnvyNG package with:
sudo apt-get install envyng-core envyng-qt

Run it in text mode with:
envyng -t

From the menu just select manufacturer (mine was ATI). No need to remove current driver. It will download a driver itself (have no clue from where) and install it. Just follow the questions. After it finishes, it will ask to reboot. Now select the normal mode in the grub menu and see if it worked.

---

### Post by chrisme on 2009-12-20
> **darkod said:**
> Yes, in the grub menu you select the recovery mode entry, not the normal mode. In the next menu select something like "root with networking" to have internet access. That will load a text based command prompt.

If you have ATI or Nvidia card/chipset, at the command prompt install EnvyNG package with:
sudo apt-get install envyng-core envyng-qt

Run it in text mode with:
envyng -t

From the menu just select manufacturer (mine was ATI). No need to remove current driver. It will download a driver itself (have no clue from where) and install it. Just follow the questions. After it finishes, it will ask to reboot. Now select the normal mode in the grub menu and see if it worked.

I followed your instructions and now it seems to work. The problem is that it's working only in low resolution. Maybe i have to open my pc to see what graphic chip is using because it gives me that both drivers (nvidia and ATI) are not compatible.

---

### Post by efflandt on 2009-12-20
At the gui login (maybe after you click your name to login), **GNOME** at the bottom is a dropdown list, try **Failsafe GNOME**.  That may at least get you in, but you probably need an automatic wired connection to get networking, because what you can do in **Failsafe GNOME** seems to be limited (I could not successfully configure wireless from there, but fortunately had a wireless bridge I could use).  I had to do that on an old PC that did not seem to work with default video drivers.  From Failsafe GNOME I was able to install xorg-driver-fglrx with Synaptic for the old ATI card.

When I tried Xubuntu on the same PC, 9.10 actually worked until the first set up updates.  So I reinstalled, then installed xorg-driver-fglrx "before" doing any updates.  Or I guess I could have done that with apt-get from plain xterm or console, but at that time I was not really familiar with apt-get and did not know which package I needed.

Many people that had issues with 9.10 seem to be video related (X changed how it does things, so some old special drivers or configuration files do not work).

---

### Post by darkod on 2009-12-20
> **chrisme said:**
> I followed your instructions and now it seems to work. The problem is that it's working only in low resolution. Maybe i have to open my pc to see what graphic chip is using because it gives me that both drivers (nvidia and ATI) are not compatible.

You might have Intel chipset especially in onboard graphics. Sorry, I don't know about drivers for that. If it allows you to at least enter ubuntu desktop, maybe you can find better driver. Look in System-Administration-Hardware something. (don't remember the exact name). It will offer any drivers it can detect you need. Obviously, you need to be connected to the internet.

---

### Post by WRATGUT? on 2009-12-21
On one computer I installed Ubuntu 9.10 on had Intel 82945G Express Chipset Family graphics and Ubuntu 9.10 froze right after logging in. On the other PC I installed Ubuntu 9.10 on had some other Intel graphics chip but instead of freezing at log in, it simply just didn't boot to Ubuntu anymore after installing updates. I'll just stick with Ubuntu 8.10 and wait for Lubuntu 10.04.

---

