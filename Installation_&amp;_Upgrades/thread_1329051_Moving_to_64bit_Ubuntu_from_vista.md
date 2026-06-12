---
title: "Moving to 64bit Ubuntu from vista"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by 987a654 on 2009-11-17
Hi all,

Over the past one year I have been playing with Ubuntu on my desktop and now I want to move my lappy completely to Ubuntu. 
I am going to use 64bit.

I just want to know what would be the best configuration.

I used just 3 partitions before
/
swap
home

but I was suggested the following option.
"
10Gb /
(size of ram) /swap
~2Gb /home
(rest of drive) Data (or whatever you want to call it)

This to some people is more elegant, as you separate the Data files from all the config and .(dot) files for all the applications you use. Because the .(dot) files aren't very big, I think even 1Gb will be enough for /home. Do note to make changes to your virtual system to use the Data partiton instead of your /home."

Any suggestions? I do not play games and use my system mainly for surfing web, docs, email, and watching TV. I am planning to have vista in a VM if I ever need it. 

My Hardware Dell XPS M1210
Mainboard :	Dell 0FP985
Chipset :	Intel i945PM
Processor :	Intel Core 2 Duo Mobile T5600 @ 1833 MHz
Physical Memory :	4096 MB (2 x 2048 DDR2-SDRAM )
Video Card :	NVIDIA GeForce Go 7400
Hard Disk :	WDC (80 GB)
CD-Rom Drive :	HUAWEI Mass Storage USB Device
DVD-Rom Drive :	Optiarc DVD+-RW AD-5540A ATA Device
Monitor Type :	PM822121W1  - 12 inches
Network Card :	Broadcom Corp BCM440x 100Base-TX Fast Ethernet
Network Card :	Intel Corporation PRO/Wireless 3945ABG
Operating System :	Windows Vista (TM) Home Premium Home Edition 6.00.6002 Service Pack 2
DirectX :	Version 10.00
Brother wifi 2170W printer
Bluetooth stereo Headset

I have 4GbRam, what size should the SWAP be?
I tried the live USB version of 9.1, booted with out any problem. Is there anything I should check out before I go for install?

Yudi

---

### Post by WannabeFantasma on 2009-11-17
I read somewhere Swap = Ram X2 so if it's 4GB it'll be 8GB
but not sure if it's really needed...

---

### Post by ed-koala on 2009-11-17
You definitely want swap to be at least as big as your RAM and usually 2x, this makes a big difference in performance if swap is too small to hold all of RAM and whatever else it holds, and doubling RAM size gives all the room you need.

You'll love being free of Windows, trust me.  I haven't given virii or spyware a second thought since going totally Ubuntu a couple of years ago. Ubuntu does all you need. And some games DO run (if ya ever want) using Wine.

---

### Post by 987a654 on 2009-11-18
12Gb /
(size of ram) /swap (8Gb)
5Gb /home
(rest of drive) Data 

How does this partition structure look? 

From what I understand Under LInux one can put any folder in it's own partition. I want to know what are the alternative scenarios.

Because Ubuntu is updated twice a year, I want to know what is the best way to partition the drive so that when I update I will not have to reformat the entire drive. 

Yudi

---

### Post by realzippy on 2009-11-18
If you have 12 GB RAM your system normally will never touch your swapfile 
(set swapiness to 0)...so 8 Gb swap is waste of storage.
With a separate /home partition you are fine when updating.

---

### Post by 987a654 on 2009-11-18
I only have 4gb ram, not 12gb

---

