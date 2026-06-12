---
title: "Installing ubuntu without touching windows boot"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by LondoMollari on 2013-02-17
Hi!

I am trying to install ubuntu on my machine. The most imortant thing for me is that my windows 7 boot remains unchanged, because this seems to be a recurring pain in the a** everytime i try to upgrade or uninstall ubuntu (windows wont boot because of grub2)

So what i want to do is install ubuntu so that i have to use the bios bootloader to select OS. To achieve this, I disconnected my Windows drive and attempted to install ubuntu to a seperate physical disk. 

As far as I can tell, the windows-disk is the only disk I have wich has the 'boot' and 'active' flag set, wich is why I am puzzeled as to why the ubuntu installer still tells me that "windows 7 is currently installed on this computer" when the disk is disconnected!?

Why is this? (I am hesitant to continue the installation of ubuntu before I understand this.)

Thanks for all replies :)

---

### Post by darkod on 2013-02-17
Starting from win7 windows can put the boot files on another disk, not where the actual install is. So, not knowing, you might actually have the few boot files it needs on another disk.

Since grub2/ubuntu looks for boot files (not the actual windows C: partition), if it can see boot files it will say it's windows. They might be a left over from a previous installation too.

---

### Post by LondoMollari on 2013-02-17
> **darkod said:**
> They might be a left over from a previous installation too.

That must be it. I recently uninstalled ubuntu, and ran into some problems relating to grub2/windows-boot. I had to do a fresh install of win7. I did this with only one drive connected, so the old bootfiles must be leftovers from the previous setup I guess :)

Thanks

---

### Post by darkod on 2013-02-17
If you are sure this small partition with boot files is not used by the current win7 install, you can delete it so that it doesn't create confusion in the future.

---

### Post by LondoMollari on 2013-02-17
> **darkod said:**
> If you are sure this small partition with boot files is not used by the current win7 install, you can delete it so that it doesn't create confusion in the future.

Will do! Thanks

---

