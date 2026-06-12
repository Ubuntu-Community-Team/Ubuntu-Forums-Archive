---
title: "Installing on Eee PC. USB recognized, but refuses to boot."
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by HitmanNumber86 on 2010-02-07
I'm installing Karmic remix on my Asus Eee PC. I've created the USB boot disk with wubi. I enter the BIOS to change the order, and I see the USB with the brand name displayed, so I put it first, and deactivate the HDD (Unecesary in most cases, but I've been going at this thing for a while now). I exit the BIOS, and get the message 

"Reboot and Select proper Boot device
or insert Boot Media in selected Boot device and press a key"

I've tried the standard Karmic as well. Suspecting it could be Windows 7 making a bad image, I've run Jaunty off a disc on another PC and used that to make the USB instead. I've also tried downloading the ISOs several times throughout this process. Also, I've been trying between two USB drives. NOTHING IS WORKING!!!

I'm going to attempt a network install, and will post when I fail at that (I'm an idiot with networking). Please help me out. Thanks in advance.

---

### Post by HitmanNumber86 on 2010-02-07
I just read a good bit of this [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet), I think my brain is melting. I can't do this stuff over the network. 

I NEED YOUR GUYS' HELP!!! I can't live with Windows 7. The thing crashed after a half hour of "initializing" on the first startup. 

Is there anyway the network install can be described in the Queen's English, or can I connect the computers directly via USB or network cable? I need some way, ANY WAY, of getting a real operating system on this machine.

---

### Post by HitmanNumber86 on 2010-02-07
I was hoping to get a faster solution on here, but I figured it out myself. It turns out their were two sets of priority options in the BIOS. They both had to have USB set to primary to boot off the stick. Funny thing is, the option isn't there anymore.

---

