---
title: "xubuntu - plain blank light blue screen and pointer only"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by brothertonyo on 2007-05-21
I am trying to use an Xubuntu Live CD on an old Compaq Presario 5360 desktop computer. Installation seems to work. I get to a small animated circle then a gerbil running around in the logo. Then I get a plain light blue screen with a mouse pointer and nothing else. When I click nothing happens. I don't have any idea where to go from here. Help anyone?

Some background on me:
I feel like I've wasted half my life either getting things to work on Windows or walking on egg shells in the hope that Windows wouldn't crash. I'm sick of the stress.

For years, I've put off giving Linux a try and I'm finally doing it now because of a conversation I had with a guy I met a week ago. When I told him how much I hate Microsoft's business practices and Windows in particular, he said, "So I guess you use Linux?" Logical assumption. I didn't have a good answer.

For the past week, I've been trying to get Ubuntu running. I tried unsuccessfully on one old machine and after much time searching the Web I finally tested my RAM with Memtest86 and got thousands of errors.

Now I'm trying on the Compaq 5360 and since it's an older system, I'm using Xubuntu. I tested the memory and found no errors. As stated above, I'm looking at a blank light blue screen with a mouse pointer and I'm stuck.

I don't know what other info you might need so let me know.

---

### Post by southernman on 2007-05-21
How much ram is in this box?

---

### Post by brothertonyo on 2007-05-21
I meant to include that in my post. I have two 128 sticks plus one 64 for a total of 320MB of RAM.

---

### Post by brothertonyo on 2007-05-21
More Specs from [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00191380&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00191380&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN) 

450 MHz AMD K6-2 processor with 3DNow! technology
100 MHz system bus
64 MB 100 MHz SyncDRAM, shared memory architecture, three total DIMM slots upgradable to 384 MB - 4 MB dedicated for video memory (SyncDRAM DIMM required)
10.0 GB 1 UltraDMA hard drive
512 KB integrated L2 Pipeline Burst Cache
Integrated 2X AGP Graphics with Direct3D; Integrated 64-bit hardware-accelerated 3D graphics; MPEG full-motion video playback; Maximum non-interlaced resolution of up to 1600 x 1200 (when supported by monitor)
Power Supply: Steady-state 145 watts

---

### Post by brothertonyo on 2007-05-21
And as I stated above, I had added more RAM to the 64MB that came with the computer.

---

### Post by brothertonyo on 2007-05-22
I chose the option: "Check CD for defects" and this was the result: 

Checking ./casper/filesystem.squashfs                       mismat
Checking ./casper/initrd.gz                                                 ut
Checking ./casper/filesystem.manifest                               ut
Checking ./casper/filesystem.manifest-desktop                 ut
Checking ./casper/vmlinuz                                                  ut
Check finished, 1 checksums failed                                     ut
Press any key to reboot your system                                 utch

Whereever I put "ut" in the right column above, the "u" looks funny kinda like it's blended into the "t".

Anyway, I'm now going to try burning another CD but it's going to take awhile because I had deleted the .iso to save hard drive space:oops:

I had created the Live CD several months ago and it has Dapper Drake on it. I see that Feisty Fawn is out now so that's what I'm downloading. I will continue to post my progress...

---

### Post by brothertonyo on 2007-05-22
I tried to use spaces to create columns but it didn't work. The last word of every line that starts with "Check" in my Check CD results should be in one column.

---

### Post by brothertonyo on 2007-05-23
I burned a Xubuntu Feisty Fawn CD and it checked out OK. This time, I got all the way to a desktop with icons. Unfortunately, the mouse is stuck! I'm going to reboot.

---

