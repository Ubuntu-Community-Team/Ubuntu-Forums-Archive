---
title: "[Ubuntu] Install Dual boot (Window 10 + Ubuntu) on ASUS VivoBook Pro N580GD-E4085T"
date: 2019-03-15
forum: Installation &amp; Upgrades
---

### Post by dinhtunglam-tspt on 2019-03-15
Dear all,

I would like to create a post to share my experience to install Dual boot (Window 10 + Ubuntu) on my laptop: ASUS VivoBook Pro N580GD-E4085T
It has 2 hard disks: one SSD 128 GB, one HDD 1TB.

My laptop was pre-installed Window 10, and I would like to add Linux OS to do my stuffs.
I have been struggling with the installation, even with referring to lots of information from this forum , i.e: [https://ubuntuforums.org/showthread.php?t=2402972](https://ubuntuforums.org/showthread.php?t=2402972), or another forums.

--- Starting off by disabling Secure Boot and Fast boot ----
With this step I have no issue, finally I realize that disabling Secure Boot is enough.

---- Try with Ubuntu 16.04/ 18.04/ 18.10 directly ----
I created the USB installation media with Rufus for EFI system, and the installation executable file could be run from the USB, but there are 2 cases which preventing me from installing:
1) It only initialize up to the dot counting . . . . of the Ubuntu screen.
2) Even to the next step of pressing the Next button on the Welcome screen of Ubuntu installation, it stuck here forever.
After around 10 times of the issues, I gave up.

--- Try with Debian Stretch ---
I know that Ubuntu is based on Debian, so I tried with Debian Stretch to start off again.
I was very happy because I could install dual boot as usual, but ... Debian is really awful with firmware driver license issues, I could not make the Wi-Fi and touchpad driver work with it, also the Graphic card and audio driver are not available, so I got fed up after 2-3 days of trying and suffering from that fact.

----
[B]Final solution:
[/B]So I tried with Ubuntu 14.04.6 as my last choice ...
I also observed the same issue with drivers on it, so I tried to upgrade to 16.04 to see if I got some lucks, but no, same problem.
I managed to install firmware for Wi-Fi, driver for graphic/touchpad, and even worse because I couldn't logging into the Graphic session, so I had to logging into console by Ctrl + Alt + F2.
And I did another try to upgrade it to 18.04 by command line, and it works like a charm now for all things.

Good luck to you,
Tung Lam, Dinh

---

### Post by yancek on 2019-03-15
Ubuntu has a page online (link below) which explains in detail the requirements for dual booting Ubuntu with windows 10.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by dinhtunglam-tspt on 2019-03-18
Thank @yancek,
Indeed I did read and try the page before, but I couldn't make it an easy way step by step like the guideline. 
With Ubuntu 16.04 and upward I couldn't make the USB storage boots up properly onto the laptop, while the same configuration works with Debian/ Ubuntu 14.04.

---

