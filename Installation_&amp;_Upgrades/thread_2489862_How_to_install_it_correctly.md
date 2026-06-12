---
title: "How to install it correctly ?"
date: 2023-08-12
forum: Installation &amp; Upgrades
---

### Post by accelerator-krit1 on 2023-08-12
I have an old computer lying around, I want to install it on it, help
Asrock - M3A770DE
phenom ii x6 1045t
16GB

---

### Post by Rubi1200 on 2023-08-12
Hi and welcome to the forums :-)

Not sure what you mean by correctly but here are some questions and things to consider:

1. what graphics card are you using?

2. how much storage do you have?

3. what operating systems are currently installed?

I suggest downloading and burning one of the Ubuntu flavors to USB and then change BIOS to boot and try it out to see what you like.

If you want something lightweight I can recommend Xubuntu or Lubuntu. But there are also lots of Linux distros out there to try, so feel free to explore some of them.

---

### Post by accelerator-krit1 on 2023-08-12
1. GTS 250
2. 160GB
3. There are no systems

---

### Post by yancek on 2023-08-12
Is this computer capable of booting from a USB?  The current Ubuntu iso is to large to fit on a DVD but Xubuntu and Lubuntu are not if you need a DVD.  Download whichever iso file you choose and use software meant for the purpose of creating a bootable USB, insert it in the computer you want to use and use the defaults to install.  Simplest way to do it if the computer has no other OS.  You might check the BIOS firmware to see if the computer shows any mention of UEFI so you can use that if you choose.

---

### Post by mIk3_08 on 2023-08-12
In my opinion, If the system unit is capable of booting from usb then I prefer using bootable usb. Fast and easy way to install Linux Ubuntu Operating System. I have installed lots of system units with Linux Ubuntu Operating System here in Philippines already. It gives me light weight in my works and 101% always successful and less stressful so far. Regards and cheers.

---

### Post by accelerator-krit1 on 2023-08-12
> **yancek said:**
> Is this computer capable of booting from a USB?  The current Ubuntu iso is to large to fit on a DVD but Xubuntu and Lubuntu are not if you need a DVD.  Download whichever iso file you choose and use software meant for the purpose of creating a bootable USB, insert it in the computer you want to use and use the defaults to install.  Simplest way to do it if the computer has no other OS.  You might check the BIOS firmware to see if the computer shows any mention of UEFI so you can use that if you choose.

I have a BIOS, yes, it is possible from a USB flash drive, I just do not know how to properly split the disk

---

### Post by ubfan1 on 2023-08-12
Since there's nothing else on the (tiny 160GB) disk, just use the "whole disk" default on the installer.

---

### Post by accelerator-krit1 on 2023-08-12
> **ubfan1 said:**
> Since there's nothing else on the (tiny 160GB) disk, just use the "whole disk" default on the installer.

Well, can it be divided into / and /home ?

---

### Post by Rubi1200 on 2023-08-12
> **accelerator-krit1 said:**
> Well, can it be divided into / and /home ?
Yes, no problem doing that.

My recommendation would be 30-40GB for / and the rest for /home

40GB may seem a lot but it gives you flexibility to add programs, store user data, and do upgrades.

---

### Post by accelerator-krit1 on 2023-08-12
> **Rubi1200 said:**
> Yes, no problem doing that.

My recommendation would be 30-40GB for / and the rest for /home

40GB may seem a lot but it gives you flexibility to add programs, store user data, and do upgrades.

Thanks

---

### Post by ajgreeny on 2023-08-12
Details of installing with a separate /home partition are shown at [https://ostechnix.com/install-ubuntu-desktop/#manual-partitioning-method](https://ostechnix.com/install-ubuntu-desktop/#manual-partitioning-method)

I have not looked at that site in as much detail as I perhaps should but my quick look seems to point to doing it the same way as I have done for about 12 yeara with no big problems; it certainly makes upgrading the OS version a lot simpler as you can just work on the root partition, leaving the /home partition untouched.

---

### Post by TheFu on 2023-08-12
> **accelerator-krit1 said:**
> I have an old computer lying around, I want to install it on it, help
Asrock - M3A770DE
phenom ii x6 1045t
16GB

What is "it"?

If "it" is ubuntu, your GTX 250 won't be supported with native GPU drivers.  I had a 430 GT loose driver support in 2016.  That means you'll be using the F/LOSS GPU driver which will likely limit the resolutions available.  I think 1280x768 is about the best to be expected.

The CPU model and RAM will matter next.
phenom ii x6 1045t provides a passmark of about 3000, which should be fine for low-end server or basic desktops. It won't be a speed daemon.  My systems have about 20,000 passmarks for a comparison. That's with an AM4 socket $120 APU and 65W peak power use.  I replaced a 125W Core i7 and the electricity cost savings in the next 2 yrs paid for the new system (MB, CPU, RAM). I reused everything else.

16G of RAM is more than I have on my desktop. Should be fine.  Just setup a swap area of 4.1G.
If you want a faster boot, spend $40-$55 and get an SSD. Quality SSDs are cheap - you'll probably need a SATA 2.5in SSD for a phenom.  Check out the Samsung 8x0 line. Those are SATA SSDs in a 2.5in form-factor for laptops and desktops.  Think 500G-1TB are in that price range.  [https://www.amazon.com/Samsung-SM883-2-5-240-Serial/dp/B07R2YNH5S](https://www.amazon.com/Samsung-SM883-2-5-240-Serial/dp/B07R2YNH5S), I'd get an 500G 870 EVO or 1TB.  Going really small seems to lose SSD endurance (i.e. lifespan).

I've probably install a lighter Ubuntu 22.04 (Xubuntu/Lubuntu/Ubuntu-Mate) or Linux Mint 22.x.  Just depends on your needs.  I'm running Linux Mint 21.1 here. Nice, snap-free, OS.

---

