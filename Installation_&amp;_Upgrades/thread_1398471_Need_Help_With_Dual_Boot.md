---
title: "Need Help With Dual Boot"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by aglc2005 on 2010-02-04
When I put together my computer, at the time I decided to run only Ubuntu. Now, I have realized that there are a few things that I would like to have with Windows, mainly gaming. I have tried to run most of my games in a VM, but the VM tends to be too choppy (I have read numerous issues with VirtualBox and currents kernels causing guest OS's to run slow). I have also read through the guide on how to restore Grub after a Windows installation. Where my problem comes in is that I am running my root and swap on a RAID 1 Linux software raid and my /home on a RAID 5 Linux software raid. My intentions are to install Windows on it's own hard drive (an IDE attached drive) separate from all the Linux drives. When I go to reinstall Grub, what kind of complications should I expect? Will I reinstall Grub onto the Linux raid drives? Or will/should it go on the separate Windows disk? I would appreciate any kind of help.

---

### Post by oldfred on 2010-02-04
I do not know about raid but if you set the ide drive as the first/boot drive in bios windows should install there and not do anything to your existing grub. When you set your existing raid first again, and if you have grub2 and sudo update-grub should find your windows install and add it to your boot. 

There have been issues for mixed ide/sata systems mainly caused by the BIOS not having the order correct. Some older BIOS still used the master setting on the ide drive and made it first no matter what. Newer BIOS seem to let you control all drives via BIOS not jumpers on the hard drive or cable select.

---

### Post by aglc2005 on 2010-02-09
Thanks for the response, I apologize for not responding any sooner, I keep forgetting to get the thread subscription.

What you have said makes a lot of sense. I really wish I had just bought a dedicated raid card for my system because that would make your solution perfect. But with it being a software raid, I can't set the "raid" as first since the bios still sees two separate drives. I might have to dig in and see which specific drive has the MBR on it, or does the linux raid split that with a raid 1? I might just go out and buy a raid card and copy everything over to that. I do have a very modern bios, and actually I might have an issue setting an IDE drive as a boot drive to be honest.

---

