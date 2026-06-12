---
title: "Grapics driver issue"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by Farving on 2010-10-02
Hi folks,

I'm new to Linux, and have tried making myself a Media Center from a Zotac ION motherboard, and running Ubuntu 10.04 with XBMC..

I've had it all up and working, with playing from my NAS and send it to my TV through HDMI... Yesterday, I switched out from XBMC startup session to GNOME-session and saw there was updates, which I of course installed (As a windows user, you know updates are kinda importent), but after reboot I couldn't get Ubuntu to launch my drivers, and keeps running it in low graphics mode.. Making my media center kinda useless..

So my question is, how do I determine what went wrong, and how to fix it? I have though of reinstallling my NVidia drivers, but I found a site describing it, and can't find it anymore, something going out of the GNOME KDE, and type some very long lines of codes and then the nvidia driver installed :)

Any suggestions how to get it up and running?

Btw the driver i installed was version 256.53, since the propritaire driver couldn't run VDPAU properly..

Begging for help,

// Farving

---

### Post by jesse c on 2010-10-04
i dont really have an answer for you since im not a techie but i have a similar post running that has the same issue that i resolved by pulling my tuner card out at upgrades.It seems that there is some code that is reading your tuner card as the primary graphics card and your nvidia card as a secondary driver so everything you do to try to start your nvidia driver is really trying to mess with your tuner card and is not a compatable command.Im sure there is someone out there that can make sense of what im describing andcan explain a simple fix

---

### Post by Farving on 2010-10-04
The only problem related to that, is that, there is no Tuner card in my computer.. All I really have i my Zotac Motherboard with 2 Ram modules insertet.. the rest is onboard chips and processors :)

---

### Post by Farving on 2010-10-04
A friend of mine told me, that a reinstall of the driver could solve the problem.. I had already tried that without any luck, but the reason why it didn't was because I did it the Windows way.. 

I just re-ran the installer hoping it to remove all conflicting-prio drivers, which it obviously couldn't..

So my solution to my problem was to do a manual driver uninstall by envoking

sudo sh location/NVIDIA-driver-package.run --uninstall

and reinstall it this way

sudo sh location/NVIDIA-driver-package.run -k $(uname -r) --xorg-modules-path=/usr/lib/modules --x-libraries-path=/usr/lib

It is now up and working again (until next update)

---

### Post by WannabeFantasma on 2010-10-05
I had kinda the same issue today, wanted to install 10.04 instead of my 9.10. installed graphics drivers  (256.53)
rebooted, installed updates and low graphics mode...

Since I have another fast error at boot-up (need to find a way to pause that thing so i can see it) I gave up and wanted to install 9.10 back....
but now that i read this i should test it!

Does vdpau work after that?
Or do you still need libvdpau-dev stuff?

Got an ION ITX too.

---

### Post by Farving on 2010-11-08
Everything works just before my update..

Just did a manual uninstall then manual install with the lastest driver (which happened to be the same as my previous one), and it worked flawless again :-)

No need to do anything else - atleast for me

/greets

---

