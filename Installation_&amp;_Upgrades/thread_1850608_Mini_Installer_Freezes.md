---
title: "Mini Installer Freezes"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by iamdigitalman on 2011-09-26
Hi guys. Been a while, but I have not stopped using ubuntu. Dual boot into it on my computers via WUBI. But now I am calling on it to do a serious project.

I want to either set up a home theatre PC or a home server, and ubuntu would be perfect for the job. I bought a used Ebox 2300 on ebay. It is a small fanless computer, a bit underpowered, but great for a server. 200mhz SOC, 128mb of RAM, onboard VGA, 3 USB ports, 100mbps lan, and a compact flash slot it can boot from. This makes it a silent, fanless, solid state unit.

It came with a 2gb card, which I can get ubuntu running on and then hold files on a hard drive. it does have a 44 pin IDE interface on the motherboard, just need to get a cable and scrounge up a spare drive.

I downloaded the latest 11.04 mini CD, and used unetbootin to put it on a 1gb flash drive. it would not boot. Found out the kernel will not work without recomiling it for the CPU. Despite being x86 and pentium class, it lacks a cmov instruction. So, I backtracked. Tried 10.10. Same thing, back another step, and 10.04 works. Just need to make sure the flash drive is formatted fat16 or syslinux throws an error. However, upon getting the installer going, it keeps freezing after it downloads the release file. I can't seem to find any info on it on the internet. It will go to 100% downloaded after a few seconds, the activity LED on the ethernet port flickers for 30 seconds, then nothing, the only other activity is the ocasional blink of my flash drive, which it does regardless of what it is plugged in to.

I have let it sit for hours on end, and it just sits there at the blue screen with the gray text bar at the bottom. Tried the 8.04 mini CD which is still out there. The only other thing I can do is hit alt+F2, then it says please press enter to activate this console. doing so drops me to busybox./

Also, tried putting the CF card in an external reader, and use my laptop to install ubuntu. that works, but my laptop cannot boot from the reader for some reason, and popping the card back into the ebox just causes an endless reboot cycle.

I have tried tweaking the BIOS, and putting it to defaults, but nothing works. It did have a working install of Kwort 2.4 on the CF card and it ran nicely even with the xserver running, I was surprised. So I know it can handle linux. But I have blown that away, it was a bit out of date, and I had never heard of that distro before.

Any thoughts? Sorry for the long post, mine always are, but I always want to try to include as much detail as possible.

Thanks.

---

