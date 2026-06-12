---
title: "installing ubuntu alongside windows 7"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by aaj99 on 2011-06-19
i have just bought a laptop (sony s series) with windows 7 and want to install ubuntu on a partitioned hard-drive, largely to avoid getting viruses. i will use ubuntu for all my personal use (internet, photos, music) and windows for work (ms office). i want to keep the two systems separate in order to reduce risk of virus contamination

i have downloaded the installer onto my usb drive and am ready to install. i have two simple (i think) questions:

1. do i select "install ubuntu alongside windows" or "something else"? i definitely want to partition the hard-drive

2. how do i set the partition? i only need about 50gb for my windows docs

i have looked at lots of advice on the internet but most of it seems to be for older versions of ubuntu. i would be very grateful for anyone who can provide me with clear, straightforward advice - i have never partitioned a hard-drive or installed a new os and am a linux virgin

thanks

aaj99

---

### Post by lemonchicken on 2011-06-19
if you haven't already, you will need to use a tool like unetbootin to add the necessary boot files to the usb drive.

boot from flash and select install ubuntu. follow the instructions on screen and you'll find your way to where you need select the hard drive to install to. 

use the slider to determine how much space will be used for the ubuntu partition. otherwise use the 'advanced partition tool' for more options.

should get you well on your way, report back with any problems..

---

### Post by Mark Phelps on 2011-06-19
It's best NOT to allow the Ubuntu installer to shrink the Win7 partition -- despite what the videos and/or guides tell you.  

You should use the Win7 Disk Management utility to shrink the Win7 partition.

---

### Post by YesWeCan on 2011-06-19
> **Mark Phelps said:**
> It's best NOT to allow the Ubuntu installer to shrink the Win7 partition -- despite what the videos and/or guides tell you.  

You should use the Win7 Disk Management utility to shrink the Win7 partition.

Agreed.
Also, back up any critical files before you start messing with partitions and dual installations. It's easy to make a mistake.

---

