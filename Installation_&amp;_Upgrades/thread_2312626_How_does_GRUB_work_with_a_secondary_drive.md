---
title: "How does GRUB work with a secondary drive?"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by eduardoflsantos on 2016-02-05
Hi,

I have a Windows + Ubuntu on dual boot on my HDD. Now I bought a new SDD, and I want to make a fresh Ubuntu install on it, while keeping the old HDD as it was.

How does it work?

Option A: Install Ubuntu on the new HDD, change HDD boot order on bios. I'd have to go to boot options each time I want to load Windows or Ubuntu from the older HDD.

Option B: Install Ubuntu on the new HDD and keep everything as it is. There will be some way where when the GRUB from the older HDD starts, I'll be able to select the fresh Ubuntu on the new HDD.


I tried to go for option A because it looked the simple way to do it, and I don't know if Option B is possible at all. But when I chose the partitions for root, home, swap, of the new HDD, the installation process warned me that it would format the swap from the older HDD. I don't understand why it says that, it makes no sense to me. Can somebody explain me?

Thanks

---

### Post by v3.xx on 2016-02-05
I use option B.  When you do a fresh install it will take control of grub and you need do nothing.  So when you reboot, the new install will be your first boot option no matter which HDD you install to.

---

### Post by yancek on 2016-02-05
> Option A: Install Ubuntu on the new HDD, change HDD boot order on bios.  I'd have to go to boot options each time I want to load Windows or  Ubuntu from the older HDD.

The new install will be on the SSD and not the hard drive so you would need to determine which drive it is.  If you have only one hard drive currently, then the SSD would likely be sdb.  You need to make that determination prior to installing.  During the installation, if you have the HD attached during the install of Ubuntu to the SSD, Grub should detect the other operating systems on the HD and create menuentries for them.  You would then set the SSD to first boot priority and should be able to boot all three systems.

> There will be some way where when the GRUB from the older HDD starts, I'll be able to select the fresh Ubuntu on the new HDD.

Well no, not automatically as Grub on the internal HD will have no way of knowing another OS was installed.  You would have to boot the original Ubuntu and run:  sudo update-grub

---

### Post by grahammechanical on 2016-02-05
The installer has noticed that there is an already existing swap partition. I have no idea if the new install will make use of the 2 swap partitions but the formatting of swap is not something to worry about. I would not worry about it anyway. It is not as if there is data on the swap partition that we can access through normal means.

---

### Post by eduardoflsantos on 2016-02-06
Hi guys.

It worked fine. I was scared because the installation was saying it would format the swap partition from the older HDD. In any case, just like grahammechanical said, it was just a swap, so I proceeded with the installation. Everything is now working as it should. Grub has all the 3 options. 

Thanks for your help.

---

