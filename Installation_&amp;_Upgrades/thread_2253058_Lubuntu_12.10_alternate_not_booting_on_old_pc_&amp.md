---
title: "Lubuntu 12.10 alternate not booting on old pc &amp; some issues"
date: 2014-11-16
forum: Installation &amp; Upgrades
---

### Post by user313 on 2014-11-16
Hi, 

I have an old system,  I asked people for advice and I ended up trying Lubuntu 12.10 (lubuntu-12.10-alternate-i386) I used unetbootin-windows-608 to install it on a USB 

The system I have is P4 1.7 Ghz 384 RAM 20GB

1. I started the install, I got an error about missing not-free driver rt2561.bin, I found it online from manfacturer and added it on a second USB but the system could not see it, any idea why?

2. I asked it to ignore it and started with installing the system and when I went back I saw an error that something went wrong with software installation, the system gave me the installation steps so I started a step back and chose to update software from ubuntu.com only (1st & rd option) the installation gave me the error again while installing, I felt that this step needed internet connection which was not possible, but I felt this is an update step and I can continue without it, right?

3. I continued until the end and rebooted and I got blank screen, no mouse or text or anything, there is no video signal so monitor turned off I guess (Orange light instead of green, CRT monitor).

I loaded the USB again and asked it to check CD, it gave me an error about missing file possibility or something like that , I went back to windows on my other PC and got this as MD5 of the ISO 5DDE10476CCB7FC2C6FB50D914061902 which seems correct.

Someone can help?

---

### Post by grahammechanical on 2014-11-16
The first thing that you need to know is that Lubuntu 12.10 is no longer supported. Any attempt to update during the installation process will fail even if we have an internet connection due to the fact that the software repositories/archives are closed. Updating will fail after the install as well.

When you ran the installer did you tick to install third party software? Do not do that as it needs an internet connection to download that proprietary software. The third party software will include a wireless driver and a video driver. Now, the graphic adapter manufacturers have a habit of removing support of old graphic adapters. So, the proprietary video driver may not support the graphic card in that machine.

Here is something that you can try. At the Grub boot menu (press shift if Lubuntu is the only OS to bring up the boot menu) select Recovery Mode and then select Resume. That may get you to a desktop using a basic video mode.

My advice would be to try Lubuntu 14.04. With that CRT monitor you may need to use an F6 option such as nomodeset. See the section Changing the CD's boot options and go to section 6 - F6. 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by user313 on 2014-11-16
> **grahammechanical said:**
> The first thing that you need to know is that Lubuntu 12.10 is no longer supported. Any attempt to update during the installation process will fail even if we have an internet connection due to the fact that the software repositories/archives are closed. Updating will fail after the install as well.

When you ran the installer did you tick to install third party software? Do not do that as it needs an internet connection to download that proprietary software. The third party software will include a wireless driver and a video driver. Now, the graphic adapter manufacturers have a habit of removing support of old graphic adapters. So, the proprietary video driver may not support the graphic card in that machine.

Here is something that you can try. At the Grub boot menu (press shift if Lubuntu is the only OS to bring up the boot menu) select Recovery Mode and then select Resume. That may get you to a desktop using a basic video mode.

My advice would be to try Lubuntu 14.04. With that CRT monitor you may need to use an F6 option such as nomodeset. See the section Changing the CD's boot options and go to section 6 - F6. 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

You mean I should not ask about it or there is no driver and such?

First try I think the system chose without asking me because I was away, second time I picked to update with option 1 & 3, I think option 2 is what you are talking about 3rd party software and I still got the error.

I don't see anything at boot but I kept hitting Shift and I got Grub menu, I had two options, normal and advanced, advanced had two options, I tried them all, the first two gave me blank screen and the third sent me to command line.

According to the site Lubuntu 14 needs much more RAM (1 GB and the minimum is 512) and I don't have that as you can see and looking for a lightweight system anyway.

Thanks

---

### Post by mörgæs on 2014-11-16
The need for RAM comes from applications like web browsers, not the operative system itself. You are very low on RAM regardless of the version of Lubuntu.

I agree that 14.04 is a better choice. If the alternate ISO does not work then the minimal is worth trying.

The need for nomodeset comes from the graphics card, not the monitor. You haven't mentioned the card but still the option is worth trying.

More advice in the link in my signature.

---

### Post by user313 on 2014-11-18
> **mörgæs said:**
> The need for RAM comes from applications like web browsers, not the operative system itself. You are very low on RAM regardless of the version of Lubuntu.

I agree that 14.04 is a better choice. If the alternate ISO does not work then the minimal is worth trying.

The need for nomodeset comes from the graphics card, not the monitor. You haven't mentioned the card but still the option is worth trying.

More advice in the link in my signature.


Thanks for the help

---

