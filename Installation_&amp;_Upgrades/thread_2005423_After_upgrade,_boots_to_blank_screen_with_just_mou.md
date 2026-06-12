---
title: "After upgrade, boots to blank screen with just mouse cursor"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by WarholsGhost on 2012-06-17
Hello,

I just upgraded to the latest version, but after i restarted now i get a blank screen with just the mouse cursor. The screen flickers a bit but its just black. 

I'm able to boot into the recovery mode and get a root prompt, but i can't load anything. I get the error "cryptswap not ready, continue to wait." but it never loads (yes, i have fds). I'm also getting the error on boot "can't open /dev/mapper/computer-root, file does not exist".

I have a feeling somewhere in the update my full disk encryption got messed up in someway. Any idea how i can fix it? 


Thanks in advance!

---

### Post by Ja55 on 2012-10-17
I have the same problem running **ubuntu 12.10** daily build (October 17). 
first I tried to upgrade from an existing ubuntu 12.04, after upgrading I rebooted the system and I got a black screen, then I tried to reinstall all the system using an ISO from ubuntu daily builds, **the live CD worked just fine** but when I installed the system on my HD it booted on a **blank screen with only the cursor showing**.

I've a Sony VAIO laptop with an ATI Radeon HD 4572 Graphic card.

---

### Post by 2F4U on 2012-10-18
> **WarholsGhost said:**
> Hello,

I just upgraded to the latest version, but after i restarted now i get a blank screen with just the mouse cursor. The screen flickers a bit but its just black. 

I'm able to boot into the recovery mode and get a root prompt, but i can't load anything. I get the error "cryptswap not ready, continue to wait." but it never loads (yes, i have fds). I'm also getting the error on boot "can't open /dev/mapper/computer-root, file does not exist".

I have a feeling somewhere in the update my full disk encryption got messed up in someway. Any idea how i can fix it? 


Thanks in advance!

When you say latest version, do you mean 12.04 or 12.10? You might know that 12.10 hasn't been released yet. Anyways, what is your hardware?

---

### Post by 2F4U on 2012-10-18
> **Ja55 said:**
> I have the same problem running **ubuntu 12.10** daily build (October 17). 
first I tried to upgrade from an existing ubuntu 12.04, after upgrading I rebooted the system and I got a black screen, then I tried to reinstall all the system using an ISO from ubuntu daily builds, **the live CD worked just fine** but when I installed the system on my HD it booted on a **blank screen with only the cursor showing**.

I've a Sony VAIO laptop with an ATI Radeon HD 4572 Graphic card.

Did you try to boot with the nomodeset Grub kernel parameter?

---

### Post by Ja55 on 2012-10-19
I discovered that my problem was due to [LinuxLiveUSB  ]("http://www.linuxliveusb.com/")software : it corrupted my **Quantal live USB, **so I switched to **unetbootin **and everything went perfect.

---

