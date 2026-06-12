---
title: "Install. error: sis630 compatible bus not detected... - incompatible hardware?"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by ZiGr on 2014-04-08
I am new to Ubuntu, and tried to install it (version 12.04.4 LTS) from WinXP yesterday from the wubi.exe file. (I can not burn DVDs on my PC, neither boot from an USB stick). There was this error message: "sis630 compatible bus not detected, module not inserted", next the screen went black. I don't know what this means. Does it mean that I can't run Linux on my current hardware? Or is this something that can be fixed?

Thanks;

---

### Post by john340 on 2014-12-28
I just had the same experience trying to boot lubuntu 14.04 from a USB.   Started again with a fresh iso on USB and got the sam error. 
As the boot progressed, a screen came up acknowledging Lubuntu 14.04 with 4 dots below that turned on and off in succession. then a blank screen with the the cursor arrowthat moved with the mouse, Finally, a new blank screen began coming up very briefly then disappearing, until I shut the computer down. 
Does this mean that my video card and driver are not compatible with lubuntu linux.  My motherboard is rather old, Asus, P4S800D-x, 2GB mem, pent 4, 2.8 mhz. The computer currently has XP pro installed, 32bit, and i am trying to load lubuntu to try out the OS.  The BIOS does support booting from a USB, which it seems to do without problem.
Need some help!!!
Johnc

---

### Post by MAFoElffen on 2014-12-28
Do you have a SIS 630 video card? If so...

Wubi support ended at the release of 14.04. SIS integrate support last worked okay at about Ubuntu 12.04. That video card was release for Windows 2000 and the technology is about 16 years old.

It is a struggle and have to use many work-arounds to get it working after 12.04... or for any Main Linux Distro after Linux kernel version shortly before 3.x.x. That is in a native installed full-blown mode, outside of WUBI.

The thing is that after KMS implementation, for that card, you have to pass VGA VESA modes through Grub to the Linux kernel... Then tell Xorg XServer to use the sis driver directly. You would opnly be able to use Ubuntu in Gnome fallback (no effects) desktop (only 2D). Xubuntu or Lubuntu have less graphics demands, but are still a struggle with that Video card.

I'll work with you if you are game and understand that it is work on your behalf... and it still may somewhat crippled visually (the screen is going to wash out at times from not having much of a memory buffer). How is your Linux skills? And are you sure you are committed to that?

---

### Post by claracc on 2014-12-29
I suggest you to buy a DVD ( I assume you can play or install from DVD with your old computer, here you have webpage to buy dvd: [https://www.osdisc.com/products/linux/ubuntu/desktop/32bit/v12045lts](https://www.osdisc.com/products/linux/ubuntu/desktop/32bit/v12045lts) ) with ubuntu 12.04 in order to install it.

I have an old laptop (year 2002) with 630/730 Sis graphics card too, and as far as I know, ubuntu 12.04 is the last ubuntu release it can run, The sis graphics card is well recognized although it has serious memory drawbacks in order to play flash videos.

---

### Post by john340 on 2014-12-29
Thanks for the strait talk!
Actually the ASUS board has the SIS card built into the MB along with the SIS chipset.  
Can I get around the problem by using a new ATI or some other video card?  the cost of same is minimal, and if that would make the computer functional then that would be good!
Thanks,
johnc

---

### Post by MAFoElffen on 2014-12-30
Yes you can. Then you would also be able to use full Ubuntu with Unity or Gnome3.

---

### Post by john340 on 2014-12-31
Thanks for the help!
I tried everything to get it working.  Strangely, the computer is working with an ATI Rage XL  video card, which one would think would all ubuntu 12 to boot, but notta!  Finally gave up and used puppy Wake up floppy and booted from cd ISO of puppy precise 5.2.8.  Works fine.  not sure that I the install is correct, but 15 GB HD  and 2Gig memory will only allow so much.
Thanks anyway.
Johnc

---

