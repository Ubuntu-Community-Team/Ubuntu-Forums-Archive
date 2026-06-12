---
title: "Linux wont boot with USB 2.0 onboard enabled..."
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by fudda on 2008-09-21
First of all:

Hello everybody! Im the new guy. ;)

Now my problem:

I have Windows XP and Linux Mint Elyssa (5.0) [pretty much Ubuntu] installed on my Desktop Computer.

Mainboard Biostar TP35D2-A7 Intel P35 Bearlake Northbridge and Intel ICH9 Southbridge with an Intel Core 2 Duo e8400 CPU 2GB PC800 and GeForce 8600GT etc.

So far so good. After I had Windows XP installed I booted the Mint Live CD but it wouldnt load. Hung up on BusyBox and some errors about failure to load some devices. After several trial and error sessions by turning off IDE etc. on my mainbord, it happened to load after I had USB 2.0 onboard device disabled.

Great... had to use PS2 mouse and keybord for install but okay I thought. Maybe I´ll install some USB packages and then re-enable USB. Done that. Wouldnt load... same thing as with Live CD.

Funny thing is, that when I uninstall the USB host controllers in Windows and reboot from Linux it works just fine. Right until I boot Windows again (Playing Games -.-) and install all the USB drivers again (auto install) which I actually need so I can use mouse and keyboard.

Here´s my thought. On my notebook I had to blacklist the Broadcom WLAN Drivers to get them to work with ndiswrapper. So they woant be loaded at boot but after Linux is done booting and loading ndiswrapper.

Cant I do that also with USB 2.0 drivers? So that they will only load after Linux has finished booting and not during it? I think that should solve my problem. Is that possible? And if yes, how exactly would I do that?

Or is there a better "workaround" or yet a solution for this problem?

I´d really appreciate any help here since the guys on the Mint forums seem to be very lazy in helping lately. Thanks in advance for any hints.

---

### Post by wpshooter on 2008-09-21
I don't think you should have to disable USB 2.0 to get the O/S to work.  If so, I would think that there is something wrong with the O/S.

Does the MINT O/S have an ALTERNATE (text based) version similar to Ubuntu ?  If so, I would try to install from that instead of the live CD version.

---

