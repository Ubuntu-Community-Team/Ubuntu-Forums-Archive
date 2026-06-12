---
title: "Ubuntu 14.04 Liveusb with persistent memory on laptop"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by wigout2 on 2014-08-20
Hello all-

I use Ubuntu 12.04 at home and am comfortable with it.

I have a laptop Acer Aspire Timeline 1810T-8638 Core 2 Duo SU7300 - 4 GB RAM with detailed specs at the bottom of the post (not sure what will be relevant, so am including almost the kitchen sink). 
Important note: it came with a harddrive, of course, but it has an FPC (flexible printed cable) connector and I managed to break the tiny plastic push clamp that secures the connection to the motherboard. So the drive can't be read/used/ at all. I have tried to rig it up lots of times with no success.

What I have is a tiny profile 16gb flash drive
What I want is: 
Ubuntu 14.04 Liveusb
that loads to an account login page instead of the no name administrator
As much (>4gb) ext4 persistent memory as can fit, given other needs.
a 2gb fat32 data partition in case I need to share anything with a windows computer.
Swap space adequate to permit suspend and hibernation

What I have done so far:
I created a 14.04 liveusb using the supplied creator in Ubuntu 12.04.
I deleted the casper-rw loopfile, and created a casper-rw ext4 partition, (which it seemed to use).

It went to "install ubuntu" selection screen first, and took (unbearable) minutes to move on to the desktop after clicking try me.
I could get around this by choosing F6 and typing " persistent" at the end of the boot command line, but this had to be done every time manually, at just the right boot up time.

I could create a user account and choose to "logout" then "login" to that account- but I'd like it to go the login screen at boot time.

When I tried to suspend I got a "black screen" from which I could not wake the laptop- and hibernation failed.
I can work around the suspend issue (it happened with previous generations of ubuntu and I google a now forgotten cmd line fix), but I really need hibernation to work.
I gather, from reading posts, that the swap space/partition issue is the problem here. But all the instructions I came across were for very particular circumstances that did not much match mine, so I don't know how to address this/ create and automatically use this here.

Finally, after running the application updater (new Update Manager?), and a restart, the whole installation was broken.

This took all day, and while I learned much, I have no working ubuntu installation for my laptop.


I have read posts and wikis, but I can't quite put together the setup I wish for. 
I am hoping that someone(s) can either:
 point me to a one-stop solution/program
OR
can tell me how to do this properly, or near properly enough that after two more (hopefully not all day) tries, I can have a working install.

Any and all help appreciated,
wigout



> Acer Aspire Timeline 1810T-8638
Core 2 Duo SU7300 - 4 GB RAM

    Intel Core 2 Duo SU7300 / 1.3 GHz
    Cache
    L2 - 3 MB
    Front Side Bus
    800 MHz
    Chipset
    Mobile Intel GS45 Express
    Platform Technology
    Intel Centrino 2
Memory
    RAM
    4 GB ( 2 x 2 GB )
    Technology
    DDR2 SDRAM
    Speed
    667 MHz

Storage
    Interface
    Serial ATA-150
Audio & Video
    Graphics Processor
    Intel GMA 4500MHD
    Memory Allocation Technology
    Dynamic Video Memory Technology 5.0
    Camera
    Yes
    Sound
    Stereo speakers , microphone
    Compliant Standards
    Dolby Sound Room

Input

    Type
    touchpad
    Features
    multi-touch touchpad

Communications

    Wireless
    802.11b/g/n (draft)
    Wireless Controller
    Intel WiFi Link 1000
    Network Interface
    Gigabit Ethernet

Battery
    Capacity
    5600 mAh

Connections & Expansion
    Interfaces
    3 x USB 2.0
    LAN
    VGA
    HDMI
    Microphone input
    Headphone/SPDIF combo jack
    Memory Card Reader
    Yes ( SD Card, Memory Stick, Memory Stick PRO, MultiMediaCard, xD-Picture Card )

---

### Post by ubfan1 on 2014-08-20
You could better just install to the 16G stick, then tweak the install by moving some things like /tmp into ram.   There are several tutorials on that, and comparisons between the full install and a persistent live media (C.S. Cameron wrote some in askubuntu.com and here).  Maybe see the Howto  section.  I run off sticks, but without any swap.

---

### Post by wigout2 on 2014-08-20
I got it working-ish. I'll post the nitty gritty tomorrow. 

The suspend is not working, so I didn't try hibernation.
I have to track down if that's a general laptop bug, my specific laptop bug... and what workarounds exist.

Thanks,
wigout

---

