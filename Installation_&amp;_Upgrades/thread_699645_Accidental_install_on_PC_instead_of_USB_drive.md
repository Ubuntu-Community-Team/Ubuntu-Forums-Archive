---
title: "Accidental install on PC instead of USB drive"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by atomicant on 2008-02-17
I was using my Windows Vista laptop to make a USB install of Xubunto that I could use to get an old desktop running Xubunto.

I booted the Windows Vista laptop from a Xubunto V7 cd and prodeeded to format the USB and do the install.

Unfortunately, I skipped something somewhere, because the process seems to have put GRUB on the laptop.

Now I get a menu asking what operating system to load and the laptop gives me a GRUB load error 17 if I don't have the USB drive plugged in.

I can choose Vista and eventually it will load and run just fine, which is what I want for the laptop.  How do I sever the connection to the USB and get rid of GRUB on my laptop so I can get back to work on my desktop project with out reformatting my hard drive and loosing all my stuff?

---

### Post by Pumalite on 2008-02-17
Recover your Windows MBR with your Installation CD or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Next time you install, disconnect all your internal drives. Your Grub got half installed in sda and the other half in the USB

---

### Post by carolus on 2008-02-26
> **Pumalite said:**
> Recover your Windows MBR with your Installation CD or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Next time you install, disconnect all your internal drives. Your Grub got half installed in sda and the other half in the USB

What if you have a laptop and can't disconnect the internal drive?

---

### Post by dstew on 2008-02-26
Can your computer boot a USB drive? Check your manual to see, and look in your BIOS settings. If so, install grub onto the MBR of the external drive. You would probably choose (hd1) as the place to install grub. If your BIOS can boot a partition, you can install grub to (hd1,0) Do not install grub to (hd0) which is usually the internal hard drive.

If your computer cannot boot a USB drive, you will have to use a grub boot floppy or CD-ROM to boot the USB-installed Ubuntu.

---

