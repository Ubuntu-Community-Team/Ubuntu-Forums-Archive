---
title: "Can’t even begin to install Kubuntu 19.10"
date: 2019-12-12
forum: Installation &amp; Upgrades
---

### Post by rainbowraven on 2019-12-12
I’m kind of new to Linux. I have used Red Hat in college (many years ago) and Ubuntu a few years back, but I’m definitely rusty. I want to try Kubuntu by dual booting my Windows 10 laptop. (I should note I’m not new to dual booting - I dual-booted Ubuntu and Jolicloud in the past.) I downloaded 19.10 64-bit from the official site and checked the SHA-256 which matched. I’ve tried using both Rufus and unetbootin on 2 different flash drives; a 32GB SanDisk and a 64GB PNY. (With unetbootin I tried the Live option.) So I reboot my Dell laptop and hit F12 and choose to boot from the USB drive. In every instance, I get the screen in the first image. If I try any of the first 3 options, or if I wait more than 5 seconds, the screen goes black, there is a small amount of activity on the flash drive (indicates by its lights), and then everything goes dead. I have no idea what’s going wrong or what to try. I ran Speccy so you could see my hardware, to see if there’s an incompatibility I don’t know about, which is image 2. Should I try the LTS release next or is there something else I’m missing?

---

### Post by rainbowraven on 2019-12-12
I am reading [this thread from below]("http://ubuntuforums.org/showthread.php?t=2432911") and it said on grub menu, to hit e and replace quiet splash with nomodeset. That worked so I guess this post is solved!

---

