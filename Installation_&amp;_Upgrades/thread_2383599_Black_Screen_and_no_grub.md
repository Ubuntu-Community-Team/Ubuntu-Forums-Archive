---
title: "Black Screen and no grub"
date: 2018-01-27
forum: Installation &amp; Upgrades
---

### Post by ladyrebelle on 2018-01-27
I've been having this problem for a couple of weeks, ever since I've started trying to install Linux. I'm having this problem with every distro except for Debian (it automatically uses nomodeset I think, but I can't update my driver's or do much of anything on it, it keeps saying I'm not the root user when I am...), but I really want to use Ubuntu or Ubuntu Mate.

Anyway, I can't install them the normal way. When I get into the Live DVD or Live USB, I have to hit Esc as soon as the screen with the little keyboard on the bottom shows up and press nomodeset and then click Try Ubuntu. It works, but everything is stretched out. I can install it at least.

Well, after installing it, and when I try to boot into Ubuntu, it just gives me a blank screen. After researching, I learned that you can set nomodeset in grub before getting into Ubuntu so that'll allow me to install my video drivers, but here's my second problem: I press shift to get into grub, and it says 'grub loading', but then goes to a black screen again!

I've been researching these problems, and I've found that other people have these problems too, but never together at the same time. I'm at my wit's end! Anyone know if there's something I can do in the Live installation media? I'm completely new to Linux, so I need any instructions to be a little detailed...

Also wanted to add that I don't have any other OS installed.

Edit: also wanted to add that I have a laptop with Windows on it if I there's anything I can do on there (like if I have to download something or make new Live USBs or Live DVDs.)

OS's I've tried: Ubuntu, Ubuntu Mate, Linux Mint, Pearl OS, Elementary OS, OpenSuse, and Debian (only one I can boot into, but it won't let me do much in the terminal - I think it has a bug in it or something.)

Motherboard: MSI gf615m-p33
CPU: AMD Athlon II X3 450
GPU: Radeon HD 4850
Ram: 8gb DDR3

---

### Post by mörgæs on 2018-01-28
Hi, welcome to the fora.

Have you tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by ladyrebelle on 2018-01-28
My motherboard doesn't have uefi. But I can try installing the alternate ISO, and if that doesn't work, then the upgrade.

---

### Post by managerceo1 on 2018-01-28
More details on the ubuntu website:[URL="https://wiki.ubuntu.com/RecoveryMode"]
https://wiki.ubuntu.com/RecoveryMode[/URL]

---

### Post by ladyrebelle on 2018-01-28
I've tried installing Ubuntu 17.10. it won't take me directly to the live usb, and after I press Esc and set nomodeset and click Try Ubuntu, it's now saying it's having a kernel panic.
I'll check out that Wiki now. I'm about to give up on this and borrow a copy of Windows. :( Really wanted to learn how to use Linux, but it's just too much of a headache to get it running on my computer (although I was able to successfully install it on my in-laws computers and they have on-board AMD graphics...)

---

### Post by ladyrebelle on 2018-01-28
I've looked at the wiki, and it says I have to get into grub, which I've previously stated that I can't get into grub. I can't boot into Ubuntu, and I can't get into grub. Pressing shift makes it say 'grub loading', but then it disappears, displays a black screen, and then my TV says there's no connection.

---

### Post by mörgæs on 2018-01-29
And how about the alternate ISO?

---

### Post by ladyrebelle on 2018-01-29
I haven't tried the alternate ISO yet. I have tried the minimalist CD and Lubuntu (forgot to mention those) and when I downloaded the alternate ISO, the file name had Lubuntu in it, and it was the same version number as the one I downloaded from Lubuntu's website, so I put using the alternate ISO off.

And I did download a copy of Ubuntu 17.10 from the Ubuntu website, so it should be the latest one.

I'll give the alternate ISO a shot, but I don't think it'll work.

---

### Post by ladyrebelle on 2018-02-07
An update on my situation: I've tried the alternate ISO and had the same issues. I finally got a hold of a regular monitor and I was able to get to the loading screen (which I couldn't get to before, when I was using my TV), but then it went black for a while before it began saying no connection.

Since this monitor has DVI hook-up, I was able to use an ordinary DVI cable instead of the DVI to HDMI cable that I was using on our TV. I was hoping it would work, and I got just a little bit farther with it, but I'm still unable to boot into Ubuntu.

I've no idea what's going on with this, as I've been able to successfully install it on both my in-laws and my parents computers. Guess I'm going back to Windows...

My hardware:
Motherboard: MSI gf615m-p33
CPU: AMD Athlon II X3 450
GPU: Radeon HD 4850
Ram: 8gb DDR3
HDD: Seagate 500gb (Sata)
Optical Drive: ATAPI iHAS124 C SCSI CdRom Device (weird name, but that's how Speccy is seeing it. It can read and write DVDs too, not just CDs. Don't know why it's called that.)
PSU: I think it's a generic brand, can't remember. I don't remember the wattage either, but I do know it's over 400 watts since I've never wanted to use anything lower. Probably either a 400watt or a 500watt.

I did add a wireless card to it (don't remember the brand and model, as I've had it for ages and forgot to look at it before I installed it.) I had to install the wireless card since I had to move my PC because of the monitor, and I don't have a long enough Ethernet cable

And my TV (I was using this before I got my monitor) is an LG 4k smart TV, model 65UH6030, in case other people that know more about this stuff are able to experiment more with it.

I think there's an incompatibility issue somewhere, but I've no idea what hardware it's incompatible with. I've even looked at the supported graphic card list, and mine is listed on there (although I can't use the official driver for it.)

---

### Post by mörgæs on 2018-02-08
Running out if ideas. The only suggestion I have is experimenting with boot options. 

It seems like Debian has the best default selection for your hardware.

---

### Post by ladyrebelle on 2018-02-23
Ok, so an update. I found an older hard-drive (I went from a 500gb desktop hdd, to a 250gb laptop hdd) and I've changed the cmos battery, and now everything is working great! I don't even have to use nomodeset! Weird!

Don't know if it'll work on my TV or not, haven't tried yet. But at least it's working on a regular monitor now.

---

### Post by mörgæs on 2018-02-25
Good, thanks for posting the solution. 
Please mark the thread solved for others to benefit.

---

