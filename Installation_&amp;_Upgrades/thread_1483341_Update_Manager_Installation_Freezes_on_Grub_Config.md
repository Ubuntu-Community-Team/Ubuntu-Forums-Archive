---
title: "Update Manager Installation Freezes on Grub Configuration"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by mdffdm on 2010-05-14
IBM ThinkPad X61
Windows Vista Home
Wubi Ubuntu Karmic

I tried to upgrade to Lucid Linx while in Karmic Koala but the installation process froze while doing something with "memtest86+". CTRL-C got it to unfreeze and finish the installation but on a restart when I chose the Ubuntu OS it kept restarting rather than booting. I decided to start fresh.

So I booted into Vista and uninstalled Wubi Karmic Koala and proceeded to do a fresh install of Wubi Lucid Lynx. The installation, including the reboot, went smoothly. However, when the Update Manager was installing software a new screen popped up saying this:


Window Content: 
[Title:] Debconf on Ubuntu
[Message:] Configuring grub-pc
[Checkbox:] Continue without installing Grub? (unchecked)
[Help button: explains consequences of not installing grub]
[Back button] (greyed out) 
[Forward button]

So I leave the checkbox unchecked and click on forward. Nothing happens. All the Update Manager windows remain the same and nothing changes when I hit the Forward button. The "Applying Changes" window is stuck at "Setting up grub-pc (1.98-1ubuntu6) ...".

Can I safely force quit the Update Manager installation? Why am I getting that message about Grub? I didn't choose anything like that. I'm a newbie to Ubuntu.

mdffdm

---

### Post by mdffdm on 2010-05-14
I'm attaching the RESULTS.txt of the Boot Info Script I see everyone recommending for boot related issues.

---

### Post by mdffdm on 2010-05-14
UPDATE:

I checked the checkbox to continue without Grub and clicked forward and the installation unfroze and proceeded. Before rebooting I used the package manager to re-install grub just in case. Now I am about to reboot... time will tell.

---

### Post by phico on 2010-05-19
same issue for me ?!?!

---

### Post by borisd on 2010-05-31
I can confirm the same issue, running 10.04 under VMWare.

---

### Post by ArwensAbendstern on 2010-06-01
I confirm the issue – for a Wubi / 10.04 installation – both operating systems are on separate harddisks.

---

### Post by StiveG on 2010-06-03
Same here the update freeze at the grub (right after memtest86+ part) CTRL-C got it to unfreeze but the installation doesn't finish.

So now, my kernel is not fully update and I can't remove it...

Pretty stuck... Can't imagine what would happen if I restart my computer... :|

**SOLVE**

Restart.
Choose 2.6.32-22 (recovery mode)
Repair broken packages
Update grub bootloader
Resume normal boot

- You will be at the command line at this point.

Reboot

Everything should be ok.

---

### Post by pravincar on 2010-06-13
Exactly same issue confirmed. I'm going to do what you did and revert!

---

### Post by pravincar on 2010-06-13
I clicked the checkbox.. continue without installation and then the updates completed. Then I reinstalled grub-pc with synaptic and restarted the computer. No issues so far:popcorn:

---

