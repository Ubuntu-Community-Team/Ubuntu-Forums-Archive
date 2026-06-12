---
title: "No Audio - UNCLAIMED MULTIMEDIA"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by vmi on 2010-09-23
Hello and thank you in advance for any help or guidance you may be able to offer.

I'm new to Linux/Ubuntu although I'm fairly comfortable with Windows.  I'm trying to learn my way around Linux and I thought Ubuntu would be a good place to start so I've decided to run Ubuntu under VirtualBox as guest on a Vista host.  I've been able to successfully use Ubuntu under VirtualBox as well as download and successfully install some other virtual box images for a few other distros like LinX and Backtrack.

The problem I'm experiencing is with a Ubuntu image I recently imported into VirtualBox for web development.  Almost everything works fine except I can't seem to get the hardware setup correctly as I was able to in another virtual machine when I installed Ubuntu [clean] and Ubuntu just detected and installed everything during initial installation on it's own. After I installed guest additions for the clean install everything worked flawlessly.  In the imported webdev install however, I don't have any audio, the vm is lagging and slow to respond and I feel it's due to the hardware config from the original system the image must've been created on.

I'm not sure how Linux/Ubuntu work underneath but in Windows installations Windows will sometimes tend to bind itself to the hardware, forcing a reinstall.  Is this the case with Ubuntu? or is it possible to re-detect / reinstall hardware changes? Ideally I would like to somehow extract the hardware config from my clean working VM into the webdev VM - is this possible? ie. some solution like driver genius for windows? Also how can I remove unused hardware settings that may be there from uninstalled / unavailable hardware?  How can I claim UNCLAIMED hardware?  If there are GUI and CLI solutions - I'd like to learn both.

Some things I've already tried:
-Matching the VM settings for the working and imported VM's
-Booting the VDI from the imported VM on the working VM
-Updating Ubuntu
-Enabling and disabling sound from VirtualBox/VM 
and under Ubuntu/hardware drivers/pc speaker
-Updating/Enabling/Disabling Virtualbox guest additions form "hardware drivers"

I've read around a few forums and have been unable to find any solutions. I've attached the usually requested terminal outputs from both machines as well as screenshots of the "Hardware Drivers" screens.  The terminal outputs for both VM's include:
[B][I]uname -a
dmesg
lspci
lsmod
lshw[/I][/B]

---

