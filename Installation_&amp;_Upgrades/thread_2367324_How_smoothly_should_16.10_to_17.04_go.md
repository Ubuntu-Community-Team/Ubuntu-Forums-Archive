---
title: "How smoothly should 16.10 to 17.04 go?"
date: 2017-07-28
forum: Installation &amp; Upgrades
---

### Post by efflandt on 2017-07-28
I guess I need to see if I still have the problem with 16.04.2 that I had originally with 16.04. Originally 16.04 did something peculiar (unique?) with my main PC only (Dell XPS 8100 from 2010, no problems on much older Dell PC or laptop) where it did something to Nvidia graphics such that **no text** showed during boot/reboot until some OS did graphics (Linux gui login or Win7 depending upon grub default). So I could not see BIOS splash or grub menu. I have 16.04.2 on an old 80 GB Intel SSD that I will try this weekend (installed using laptop with no proprietary drivers). And maybe I should try a regular install of 17.04 to USB memory stick before committing to that.

I am currently running 64-bit 16.10 which has reached end of support and just wondering how smoothly a 16.10 to 17.04 upgrade goes? I know that I need to purge any ppa, remove any packages from them, and backup anything I definitely want to keep. I originally used the 80 GB SSD for 11.04 beta and had so many problems with that, that I skipped 11.04 to 11.10. I had no problems upgrading 11.10 in place to 12.04 which I kept on my main PC for a long time as a backup boot system while running 14.04 from my hard drive. It was when I tried installing 16.04 fresh on that SSD or another that I ran into blank screen on boot issue only on that one computer.

Also does the nouveau in 16.04 or 17.04 support the GTX 10xx nvidia cards yet or will I need to add graphics-drivers ppa and install nvidia from recovery with networking, then root console. I am currently running GTX 1060, but have GTX 750 Ti or GTX 550 Ti that I could use during install.

---

### Post by #&amp;thj^% on 2017-07-28
You should be fine with any of them.
```
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: wayland (X.Org 1.19.3) drivers: (unloaded: fbdev,vesa) FAILED: modesetting,nouveau
           Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           version: 4.5 Mesa 17.1.2

```
This is upgraded to Artful.

---

### Post by QIII on 2017-07-28
Hello!

Since 16.10 is EOL, you should read [this]("https://help.ubuntu.com/community/EOLUpgrades").

If you have a separate /home partition, you could do a fresh install while preserving your current /home.  Still back up, of course!

---

### Post by vocx on 2017-07-28
> **efflandt said:**
> ...
I am currently running 64-bit 16.10 which has reached end of support and just wondering how smoothly a 16.10 to 17.04 upgrade goes?...
There are a few users in this forum that swear that "upgrading is bad, it never works, you should never attempt it, and I back-up my stuff, and only do fresh installs". They always appear whenever somebody has questions regarding upgrading the distribution.

Personally I've never had a problem upgrading distribution. Several years ago, I went from 6.06 to 7.04, to 7.10, to 8.04, to 8.10, etc. and never had a problem. I don't have your hardware, I'm just commenting from experience that I never had a problem. Most issues, I feel, are due to bad video drivers when using Nvidia or AMD/ATI cards, or missing drivers for Wifi cards, so you should check this out for the distribution you intend to upgrade to. The Linux drivers are mostly incremental, meaning that if it works now, it is hard that the driver will change next version, and it will no longer work. The problem with devices not working is mostly due to new hardware that currently has no good driver. It takes a while for stable drivers to be released and for them to work fine.

If your computer is a few years old, then I'd say the chances of it working fine are high, because its hardware is not new, and thus it will use kernel drivers that withstood the test of time. But double check always for other peoples' experiences with the same device that you have.

Now, as for the rest of your post. What? I'm sorry, theres is a lot of comments that you are making, so I'm getting lost, talking about 80 GB SSD, then Ubuntu 11.10, 12.04, etc. What? Too much stuff.

---

