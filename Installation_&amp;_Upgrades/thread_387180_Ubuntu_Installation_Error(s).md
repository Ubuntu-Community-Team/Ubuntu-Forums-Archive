---
title: "Ubuntu Installation Error(s)"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by guitarist809 on 2007-03-18
Hello,

When I'm installing Ubuntu 6.10 (from the Live CD), I get the following errors, after waiting 5 minutes watching the splash screen with the bouncing bar thing do it's thing:

[17179717.540000] hdc: ide_intr: huh? expected NULL handler on exit
[17179717.588000] Buffer I/O error on device hdc, logical block 357564

This repeats many times, but the 1717xxxx.xxxxxx is always a different number.

When I saw hdc, I recognised it as my CD drive, so I figured it was a bad cd. I reburned the image 3 times (all using different settings, and the last 2 was on 8x speed). When I gave up with that, I decided to replace my CD player with another spare. Amazingly, It got past this error, but came up with a corrupted-looking screen telling me (forgot the name, but there was an X somewhere in it. I think it was X Windows). Anyway it asked me if I wanted to see a report, but I said 'No'. I was then directed to a useless command prompt, which only accepted a few commands and told me to type exit when I was done. I typed "exit". it just repeated the message (I repeated this like 7 times). I rebooted.

Heres some information (if it's needed):
- My hard drive is SATA, so its sda, which isn't the error here
- Just to make sure it wasn't the error, i re-particioned my hard drive making much of it ext3.
- My image file is _not_ corrupted, and the hash file is the same as one I found on google.
- In order for me to see these errors, I have to set my resolution (pressing F4) to 1280x1024 32), if I leave it at the default, the splash screen shows for about 10 minutes, then completly crashes.
- My other particion is NFTS (win xp)
- My CPU is 64 bit, but I'm using the 32 bit for stability.


Any help will be greatly appreciated.

Thanks,
Matt

---

### Post by Kateikyoushi on 2007-03-18
Which motherboard and video adapter do you use ?

---

### Post by alamba on 2007-03-18
> **guitarist809 said:**
> Amazingly, It got past this error, but came up with a corrupted-looking screen telling me (forgot the name, but there was an X somewhere in it. I think it was X Windows). 

This sounds like an XServer error. I'd suggest getting into your xorg.conf file and setting it up for vesa with a low resolution, just to get your GUI up and running. Then we can look into setting it up with the drivers for your video card and the correct resolution.

A

---

### Post by ilmorris on 2007-03-24
> **guitarist809 said:**
> [17179717.540000] hdc: ide_intr: huh? expected NULL handler on exit
[17179717.588000] Buffer I/O error on device hdc, logical block 357564


I have seen these errors a lot with more recent distro releases, and not just ubuntu.  What has worked for me, assuming you're using an IDE CD-ROM, is to swap the IDE cable going from the motherboard to the CD-ROM and use an older 40-pin IDE cable instead of the newer 80-pin cables.  I have no idea why this would correct the error, maybe someone more hardware saavy could explain, but it has resolved it EVERY time I have tried it.

---

