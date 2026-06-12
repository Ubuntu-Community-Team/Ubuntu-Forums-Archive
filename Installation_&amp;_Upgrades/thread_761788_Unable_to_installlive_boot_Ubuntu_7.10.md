---
title: "Unable to install/live boot Ubuntu 7.10"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by Swambu on 2008-04-21
I tried to live boot ubuntu 7.10 from CD on my computer, but it doens't work.

I do get the Ubuntu boot screen, and loading bar, but after that I get a black screen with a tiny little bar blinking....

I tried to boot it "unsilent" but it keeps saying something about a drive not found or something...

I remember that on my last PC it wouldn't boot either.

My PC :  
ASUS P5W DH deluxe
Core2 duo 2.4ghz
Geforce 8800 GTS 560mb
2 g ram
plenty of hdd

---

### Post by Maintech on 2008-04-21
Try adding: --nomsi  to the boot parameters.

---

### Post by Swambu on 2008-04-21
ty this helped, but not all the way...

I'm getting a progress bar with some text beneath it :

Loading esential drivers                    OK
Running /Scripts/int-premount          OK
Mounting root file system               
Running /script/casper-premount     OK

Here he stops again, there's no CD activity, nor some HDD activity ... it just stopped there

---

### Post by Charlie86 on 2008-04-21
Hi, my problem  is very similar, when the CD boot reach the 100% loading kernel my monitor suddenly turns off, I don't understand how modify the boot process so either the proposal solution. I'm a begginer in linux matters.
Thank you for any help and I'm sorry about my english (I'm from Costa Rica!)

My PC:
Motherboard MSI K9 with nForce 410 Chipset
AMD Athlon 64x2 4400+ (2.3GHz)
Geforce 8400 GS 512MB
1 GB DDR2 800MHz
250 GB Sata 2

---

### Post by popatopalous on 2008-04-21
> **Charlie86 said:**
> Hi, my problem  is very similar, when the CD boot reach the 100% loading kernel my monitor suddenly turns off, I don't understand how modify the boot process so either the proposal solution. I'm a begginer in linux matters.
Thank you for any help and I'm sorry about my english (I'm from Costa Rica!)

My PC:
Motherboard MSI K9 with nForce 410 Chipset
AMD Athlon 64x2 4400+ (2.3GHz)
Geforce 8400 GS 512MB
1 GB DDR2 800MHz
250 GB Sata 2

When 1st boot the CD select either Use Live CD or Install then select F4 and select Safe-Mode and hit enter twice.

---

### Post by Charlie86 on 2008-04-21
Many thank's popatopalous, but I do something like this before, I've used the safe graphics mode but the trouble remains. Is this what you mean?. 
The situation right now is I'm in the university, so I can't test the solution immediatley.
Thank you agin.

---

### Post by Swambu on 2008-04-22
Anyone has some more ideas to help me ?

---

