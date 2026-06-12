---
title: "Trouble Installing Ubuntu 13.10 in VirtualBox 4.3.8 for Windows"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by Drew_Bronson on 2014-03-16
So, I decided to try Ubuntu, and it's not working.

I installed 13.10 32-bit in VirtualBox and setup seemed to go fine.

When I hold shift down I'm getting something that says GRUB at the top, but I'm not seeing any of the options people are saying to use once you get the GRUB menu.

If I tap shift once or twice as I'm booting, but don't hold it down, I get a flashing cursor.

If I do nothing during boot I get a black screen.

I am able to access the text-based terminal from either of the above states, but trying to return to the GUI version gives me a black screen, followed by an error message about five minutes later.

Unfortunately, as this is the first time I have used a) Ubuntu and b) VirtualBox, I have no idea what to troubleshoot beyond a quick web search, which has thus far proved unhelpful.

Can someone please give me a hand? I'm eager to try Linux, but that necessitates first getting it to work.

---

### Post by rollingthunderb on 2014-03-17
Welcome. I love VB and this got me started on many a linux adventures. 

I've seen strange happenings when I thought "i did everything correctly" after what looked like a perfectly good installation.

Open VirtualBox, select your Ubuntu installation and then settings.

select "system" on the left, and then the "processor" tab on the right.

Is "Enable PAE/NX" checked or unchecked? 

It should be checked if it wasn't. Unfortunately I haven't found an easy fix when I forget this. I have to start over and make sure I did check it. i.e. new virtual disk and new install. Just delete the old one completely.

Let us know. If this wasn't it, I just took a quick shot in the dark hoping to help quickly.

---

### Post by Drew_Bronson on 2014-03-18
It shows as checked, and I don't remember having checked it after the fact. I have done some more research and was wondering if my GTX 660 might be the problem. If so, what might I do to get Ubuntu and NVIDIA to play nice?

I realized I should probably post my system specs:
Windows 7 Home Premium, 64-bit (Host System)
VirtualBox 4.3.8
Ubuntu 13.10 Guest System (I have both 32 and 64-bit ISOs, but can't find an option in VB for a 64-bit machine, so am using 32-bit for the time being; help would be appreciated in opening up 64-bit options, as I can't find any virtualization settings in my BIOS)

ASUS Sabertooth Z87
Intel Core i7-4770K (running at manufacturer's spec, and has never (yet) been overclocked)
NVIDIA GTX 660 (Manufactured by EVGA)
8GB RAM
1 TB HDD


EDIT: If it helps diagnose my problem, I should mention that during setup and when presented with the initial login, I see graphics as expected. It's only after logging in that the screen goes black.

EDIT 2: Actually, I may be overclocking...my motherboard runs my processor at 3.8GHz automatically, and the Intel Processor Identification Utility I installed says it's supposed to run at 3.5GHz. Also, the tool tells me that virtualization is enabled, but I still can't seem to select 64-bit Ubuntu as a VM type. Any ideas?

Here is the report that the Intel tool spat out:

Intel(R) Processor Identification Utility
Version: 4.80.20131220
Time Stamp: 2014/03/18 17:23:13
Operating System: 6.1-7601-Service Pack 1
Number of processors in system: 1
Current processor: #1
Active cores per processor: 4
Disabled cores per processor: 0
Processor Name: Intel(R) Core(TM) i7-4770K CPU @ 3.50GHz
Type: 0
Family: 6
Model: 3C
Stepping: 3
Revision: 7
Maximum CPUID Level: D
L1 Instruction Cache: 4 x 32 KB
L1 Data Cache: 4 x 32 KB
L2 Cache: 4 x 256 KB
L3 Cache: 8 MB
Packaging: LGA1150
Enhanced Intel SpeedStep(R) Technology: Yes
MMX(TM): Yes
Intel(R) SSE: Yes
Intel(R) SSE2: Yes
Intel(R) SSE3: Yes
Intel(R) SSE4: Yes
Intel(R) AES-NI: Yes
Intel(R) AVX: Yes
Enhanced Halt State: Yes
Execute Disable Bit: Yes
Intel(R) Hyper-Threading Technology: Yes
Intel(R) 64 Architecture: Yes
Intel(R) Virtualization Technology: Yes
Intel(R) VT-x with Extended Page Tables: Yes
System Graphics: Add-in Graphics
Expected Processor Frequency: 3.50 GHz
Reported Processor Frequency: 3.69 GHz
Expected System Bus Frequency: 100 MHz
Reported System Bus Frequency: 100 MHz
*************************************************************

---

