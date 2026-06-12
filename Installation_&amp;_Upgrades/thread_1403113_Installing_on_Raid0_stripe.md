---
title: "Installing on Raid0 stripe"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by harisund on 2010-02-09
Hey guys 

I have a workstation, 2 250GB SATA hard disks. When I boot up, there's an option to enter a configuration menu (Ctrl+I) wherein I can create a RAID volume, apparently. 

Initially, it was setup so both of them were one big hard disk, RAID0. Fedora recognized them correctly as 1 500GB hard disk, which is what I wanted. 

When I tried Ubuntu, it instead saw them as 2 separate hard disks. I went ahead and installed in the first one, sda, anyway, and after installation grub gave me a "Error 2" and halted. 

I went into the menu, deleted the RAID0 stripe, installed Ubuntu onto sda and it left sdb alone, installed correctly. 

2 questions - 
(a) now when I boot the machine up, I no longer see the option for pressing Ctrl+I... does it mean Grub or Ubuntu did something unfixable? 
(b) What if I want to go back, change it to RAID0 and install Ubuntu on a 500GB hard disk? Not possible at all?

(I thought it was FakeRaid or something like that, but the Ubuntu wiki page on fakeRaid only shows setups for RAID1 and RAID5, not what I want :( )

---

### Post by harisund on 2010-03-17
Never mind. Ubuntu 9.10 sees the RAID, which 9.04 didn't. 9.10 ended up installing Grub-1 anyway, as Grub-2 is apparently not yet "ready for RAID setups". 

Why switch to Grub-2 in the first place is an answer I am unable to find, but hey if the Ubuntu devs think it's the best I am sure it must be the best.

---

