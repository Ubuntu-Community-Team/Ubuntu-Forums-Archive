---
title: "&quot;Loading kernel&quot; fails and stuck at a colorful screen full with smiley faces"
date: 2016-09-29
forum: Installation &amp; Upgrades
---

### Post by sebastian.schuth on 2016-09-29
I'm a medium-knowledge linux and pc user. I wanted to install Bio-Linux 8 on a 2006 computer I inherited from my brother. It previously had Debian, XP and Vista (as native) in multiboot, and although the hard disk warns me of imminent failure, all OSs were capable of working on it. I could erase, create, move, resize partitions and whatnot. I could install and modify programs, even play some PC games on it, like Terraria. However, I then erased the complete hardrive, and proceed to installing Bio-Linux 8, which is based on Ubuntu 14.04.

[IMG]http://storage8.static.itmages.com/i/16/0929/h_1475178105_4807905_fb796a8509.png[/IMG]
Live USB worked fine when trying to install, but if I selected TRY WITHOUT INSTALLING option, Bio-Linux froze and then crashed to tiny pieces of block repetitions of the desktop image, and had to hard reboot. Using the INSTALLING option (after using GParted from an old Ubuntu 7.04 CD) I could successfully install it.
The problem is now this: BIOS screen is fine, but as soon as the kernel should load (I can only see that message display for half a second: Loading kernel) the system crashes and shows half a grey and half a really colorful and wicked screen, full with letters that spell nonsense, numbers and other characters like music notes and happy smiley faces throughout the bottom half of the screen. Some of the characters flash. I cannot type, nor move, and must long-press the hardware ON button.
I thought the problem was related to the first issue from Bio-Linux, so I made a new USB with Ubuntu 16.04 64 bits (to see if the problem was Unity and my system could not handle it.) It was curiously working as a live USB, did not crash, but flashed and twitched as if it were going to crash, whenever I pressed HOME button on keyboard to search for an application, like GParted. It managed to load GParted smoothly, though. I did not installed it, becuase I wanted to make a new experiment.
I then made a new USB with Lubuntu 14.04 i386 (32 bits) trying to see if it worked better, and it did, as a Live USB, managing to load and run really fast. I proceed to install it and the same crash as Bio-Linux 8 (Ubuntu 14.04) happened: the colorful half screen with flashing letters and faces.

I then installed Ubutnu 8.04 TLS and the error did not appear, but this time a black screen with a promt is shown, and only the word GRUB appears. No other indicative. I cannot write but I could ctrl-alt-del to restart. When I used the CD to grub then select: boot from Hard Drive option, then a black screen with similar weird random characters, happy faces appears.

Right now, I'm downloading Lubuntu yakkety i386.iso to install it with UNetbootin, to see if the issue is from 14.04. If that doesn't work, I will try older versions of Lubuntu or Bio-Linux. I thoroughly believe the issue is not actually graphical, because I can run Live USB pretty OK.

My computer specifications are the following:

Phoenix - AwardBIOS v6.00PG
Main Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ @2.000 MHz
Chipset: GeForce 6150 LE
Memory: DDR2 533 Dual Channel, 128-bit   2 sticks of 1 GB
Hard Drive: SAMSUNG SP2504C VT100-49   250 GB SATA
Motherboard:
                                         
[LIST]
[*]                       Manufacturer: Asus 
[*]                       Motherboard Name: A8N-BR 
[*]HP/Compaq motherboard name: Pyrite-GL8e 
[/LIST]

My partitions are as follows:
dev/sda
  dev/sda1  ext4 /root 40 GB 
  dev/sda2  ext4 /home around 150 GB to store genomic sequences
  dev/sda3  linux-swap 32 GB (because of my heavy interest in genome analysis)

I don't wanna believe the problem is the Harddisk, because it still functions alright.

While UNetbootin is downloading the iso image, I will try and install Ubuntu 8.04 with a separate partitions for /boot. Perhaps that will help.
Even with the separate partition for /boot, black screen with the title GRUB but nothing happens; and got an error: "failed to load kernel image" when booted live USB containing UNetbootin downloaded latest version of Lubuntu.

---

